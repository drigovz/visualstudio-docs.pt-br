---
title: 'Como: Usar o contexto de interface do ui baseado em regras para extensões visuais do estúdio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: de1a1e0a2022482433f81b0b2810b0d201ab7b8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710591"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Como: Usar o contexto de interface do ui baseado em regras para extensões do Visual Studio

O Visual Studio permite o carregamento de <xref:Microsoft.VisualStudio.Shell.UIContext>VSPackages quando certos s conhecidos são ativados. No entanto, esses contextos de interface do iu não são finos, o que não deixa escolha para os autores de extensão, a não ser escolher um contexto de interface do ui disponível que seja ativado antes do ponto que eles realmente queriam que o VSPackage carregasse. Para obter uma lista de contextos <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>de interface do ui bem conhecidos, consulte .

Carregar pacotes pode ter um impacto de desempenho e carregá-los mais cedo do que o necessário não é a melhor prática. O Visual Studio 2015 introduziu o conceito de UI Contexts baseado em regras, um mecanismo que permite aos autores de extensão definir as condições precisas em que um contexto de interface do ui é ativado e VSPackages associados são carregados.

## <a name="rule-based-ui-context"></a>Contexto de interface do ui baseado em regras

Uma "Regra" consiste em um novo contexto de interface do usuário (um GUID) e uma expressão booleana que faz referência a um ou mais "Termos" combinados com operações lógicas "e", "ou", "não". "Termos" são avaliados dinamicamente em tempo de execução e a expressão é reavaliada sempre que qualquer um de seus termos muda. Quando a expressão é avaliada como verdadeira, o contexto de interface do ui associado é ativado. Caso contrário, o contexto da interface do ui é desativado.

O contexto de interface do iu baseado em regras pode ser usado de várias maneiras:

1. Especifique as restrições de visibilidade para comandos e janelas de ferramentas. Você pode ocultar as janelas de comandos/ferramentas até que a regra de contexto de interface do usuário seja atendida.

2. Como restrições de carga automática: pacotes de carga automática somente quando a regra é cumprida.

3. Como tarefa atrasada: atrase o carregamento até que um intervalo especificado tenha passado e a regra ainda seja cumprida.

   O mecanismo pode ser usado por qualquer extensão do Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Crie um contexto de interface do ui baseado em regras
 Suponha que você tenha uma extensão chamada TestPackage, que oferece um comando de menu que se aplica apenas a arquivos com extensão *.config.* Antes do VS2015, a melhor opção <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> era carregar testpackage quando o UI Context foi ativado. O carregamento do TestPackage desta forma não é eficiente, uma vez que a solução carregada pode nem conter um arquivo *.config.* Essas etapas mostram como o contexto de interface do ui baseado em regras pode ser usado para ativar um contexto de interface do mundo somente quando um arquivo com extensão *.config* for selecionado e carregar TestPackage quando esse contexto de interface do ui estiver ativado.

1. Defina um novo GUID de uicontext <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>e adicione à classe VSPackage e .

    Por exemplo, vamos supor que um novo UIContext "UIContextGuid" deve ser adicionado. O GUID criado (você pode criar um GUID clicando em **Tools** > **Create GUID**) é "8B40D5E2-5626-42AE-99EF-3D1EFF46E7B". Em seguida, adicione a seguinte declaração dentro da sua classe de pacote:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Para os atributos, adicione os seguintes valores: (Detalhes desses atributos serão explicados posteriormente)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Esses metadados definem o novo UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) e uma expressão referente a um único termo, "DotConfig". O termo "DotConfig" avalia-se como verdadeiro sempre que a seleção atual\\na hierarquia ativa tiver um nome que corresponda ao padrão de expressão regular " .config$" (termina com *.config*). O valor (Padrão) define um nome opcional para a regra útil para depuração.

    Os valores do atributo são adicionados ao pkgdef gerado durante o tempo de construção posteriormente.

2. No arquivo VSCT para os comandos do TestPackage, adicione o sinalizador "DynamicVisibility" aos comandos apropriados:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. Na seção Visibilidades do VSCT, vincule os comandos apropriados ao novo UIContext GUID definido em #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Na seção Símbolos, adicione a definição do UIContext:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Agora, os comandos * \** do menu de contexto para arquivos .config serão visíveis somente quando o item selecionado no explorador de soluções for um arquivo *.config* e o pacote não será carregado até que um desses comandos seja selecionado.

   Em seguida, use um depurador para confirmar se o pacote é carregado apenas quando você espera. Para depurar testpackage:

5. Defina um ponto <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> de ruptura no método.

6. Construa o TestPackage e comece a depurar.

7. Crie um projeto ou abra um.

8. Selecione qualquer arquivo com uma extensão diferente *de .config*. O ponto de ruptura não deve ser atingido.

9. Selecione o arquivo *App.Config.*

   O TestPackage carrega e pára no ponto de ruptura.

## <a name="add-more-rules-for-ui-context"></a>Adicione mais regras para o contexto de interface do iu
 Como as regras do Contexto de Interface do Usuário são expressões booleanas, você pode adicionar regras mais restritas para um contexto de interface do usuário. Por exemplo, no contexto de interface do ui acima, você pode especificar que a regra só se aplica quando uma solução com um projeto é carregada. Desta forma, os comandos não aparecerão se você abrir um arquivo *.config* como um arquivo autônomo, não como parte de um projeto.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Agora, a expressão faz referência a três termos. Os dois primeiros termos, "SingleProject" e "MultipleProjects", referem-se a outros contextos de interface do usuário bem conhecidos (por seus GUIDs). O terceiro termo, "DotConfig" é o contexto de interface do usuário baseado em regras definido anteriormente neste artigo.

## <a name="delayed-activation"></a>Ativação atrasada
 As regras podem ter um "Atraso" opcional. O atraso é especificado em milissegundos. Se estiver presente, o atraso faz com que a ativação ou a desativação do contexto de interface do usuário de uma regra seja adiada por esse intervalo de tempo. Se a regra mudar antes do intervalo de atraso, então nada acontecerá. Esse mecanismo pode ser usado para "escalonar" etapas de inicialização - especialmente inicialização única sem depender de temporizadores ou registro de notificações ociosas.

 Por exemplo, você pode especificar sua regra de carga de teste para ter um atraso de 100 milissegundos:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Tipos de termos

Aqui estão os vários tipos de termo que são suportados:

|Termo|Descrição|
|-|-|
|{nnnnnnnn-nnnn-nnnnnnnnnnnnnnnn}|O GUID refere-se a um contexto de interface do mundo. O termo será verdadeiro sempre que o Contexto de Interface do Usuário estiver ativo e falso de outra forma.|
|HierSingleSelectionNome:\<> de padrão|O termo será verdadeiro sempre que a seleção na hierarquia ativa for um único item e o nome do item selecionado corresponder à expressão regular .Net dada por "padrão".|
|Configurações do usuárioStoreQuery:\<consulta>|"consulta" representa um caminho completo para o armazenamento de configurações do usuário, que deve avaliar para um valor não zero. A consulta é dividida em uma "coleção" e "nome de propriedade" na última barra.|
|Configurações configuraçõesStoreQuery:\<consulta>|"consulta" representa um caminho completo para o armazenamento de configurações de configuração, que deve ser avaliado para um valor não zero. A consulta é dividida em uma "coleção" e "nome de propriedade" na última barra.|
|ActiveProjectFlavor:\<projectTypeGuid>|O termo será verdadeiro sempre que o projeto selecionado for aromatizado (agregado) e tiver um sabor que corresponda ao tipo de projeto GUID.|
|ActiveEditorConteúdoTipo:\<conteúdoTipo>|O termo será verdadeiro quando o documento selecionado for um editor de texto com o tipo de conteúdo dado. Nota: quando o documento selecionado é renomeado, este termo não é atualizado até que o arquivo seja fechado e reaberto.|
|ActiveProjectCapability:\<> de expressão|O termo é verdadeiro quando os recursos ativos do projeto correspondem à expressão fornecida. Uma expressão pode ser algo como VB &#124; CSharp.|
|SolutionHasProjectCapability:\<Expressão>|Semelhante ao acima, mas o termo é verdadeiro quando a solução tem qualquer projeto carregado que corresponda à expressão.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|O termo será verdadeiro sempre que uma solução tiver projeto que tenha sabor (agregado) e tenha um sabor que corresponda ao determinado tipo de projeto GUID.|
|ProjectAddedItem:\<> de padrão| O termo é verdadeiro quando um arquivo que corresponde ao "padrão" é adicionado a um projeto na soluion que é aberto.|
|ActiveProjectOutputType:\<saídaTipo>|O termo é verdadeiro quando o tipo de saída para projeto ativo corresponde exatamente.  O outputType pode ser um <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> inteiro ou um tipo.|
|ActiveProjectBuildProperty:\<buildProperty\<>= regex>|O termo é verdadeiro quando o projeto ativo tem as correspondências de propriedade de construção e valor de propriedade especificadas para o filtro regex fornecido. Consulte [Dados persistentes no MSBuild Project Files](internals/persisting-data-in-the-msbuild-project-file.md) para obter mais detalhes sobre propriedades de compilação.|
|SolutionHasProjectBuildProperty:\<buildProperty\<>= regex>|O termo é verdadeiro quando a solução tem um projeto carregado com a propriedade de construção especificada e combina o valor da propriedade para o filtro regex fornecido.|

## <a name="compatibility-with-cross-version-extension"></a>Compatibilidade com extensão de versão cruzada

Rule-based UI Contexts é um novo recurso no Visual Studio 2015 e não seria portado para versões anteriores. Não portar para versões anteriores cria um problema com extensões/pacotes que visam várias versões do Visual Studio. Essas versões teriam que ser carregadas automaticamente no Visual Studio 2013 e anteriormente, mas podem se beneficiar de contextos de interface do ui baseados em regras para evitar serem carregados automaticamente no Visual Studio 2015.

Para suportar tais pacotes, as entradas Do AutoLoadPackages no registro agora podem fornecer uma bandeira em seu campo de valor para indicar que a entrada deve ser ignorada no Visual Studio 2015 e acima. Isso pode ser feito adicionando <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>uma opção de bandeiras para . VsPackages agora pode adicionar **skipWhenUIContextRulesActive** ao seu <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo para indicar que a entrada deve ser ignorada no Visual Studio 2015 e acima.
## <a name="extensible-ui-context-rules"></a>Regras de contexto de interface do ui extensíveis

Às vezes, os pacotes não podem usar regras estáticas de contexto de interface do ui. Por exemplo, suponha que você tenha um pacote de extensibilidade de suporte, de tal forma que o estado de comando seja baseado em tipos de editores que são suportados por provedores MEF importados. O comando é ativado se houver uma extensão que suporte ao tipo de edição atual. Nesses casos, o pacote em si não pode usar uma regra de contexto de interface do usuário estático, uma vez que os termos mudariam dependendo de quais extensões MEF estão disponíveis.

Para suportar esses pacotes, os contextos de interface do usuário baseados em regras suportam uma expressão codificada "*" que indica que todos os termos abaixo serão unidos com or. Isso permite que o pacote mestre defina um contexto de interface do ui baseado em regras conhecido e vincule seu estado de comando a este contexto. Posteriormente, qualquer extensão MEF direcionada para o pacote mestre pode adicionar seus termos para editores que suporta sem afetar outros termos ou a expressão mestre.

A documentação do construtor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> mostra a sintaxe para regras extensíveis de contexto de interface do usuário.
