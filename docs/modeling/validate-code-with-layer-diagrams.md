---
title: Validar o código com diagramas de dependência
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 975fe8eac5657e245027a4811e50bbc93528cfe5
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759707"
---
# <a name="validate-code-with-dependency-diagrams"></a>Validar o código com diagramas de dependência

## <a name="why-use-dependency-diagrams"></a>Por que usar diagramas de dependência?

Para garantir que esse código não entre em conflito com seu design, valide seu código com diagramas de dependência no Visual Studio. Isso pode ajudar a:

- Encontre conflitos entre dependências em seu código e dependências no diagrama de dependência.

- Encontre dependências que talvez sejam afetadas por alterações propostas.

   Por exemplo, você pode editar o diagrama de dependência para mostrar possíveis alterações de arquitetura e, em seguida, validar o código para ver as dependências afetadas.

- Refatore ou migre o código para um design diferente.

   Encontre o código ou as dependências que exijam trabalho quando você move o código para uma arquitetura diferente.

**Requisitos**

- Visual Studio

  Para criar um diagrama de dependência para um projeto .NET Core, você deve ter visual studio versão 16.2 ou posterior.

- Uma solução que tem um projeto de modelagem com um diagrama de dependência. Este diagrama de dependência deve estar ligado a artefatos em projetos C# ou Visual Basic que você deseja validar. Consulte [Criar diagramas de dependência a partir do seu código](../modeling/create-layer-diagrams-from-your-code.md).

Para ver quais edições do Visual Studio suportam esse recurso, consulte [o suporte do Edition para ferramentas de arquitetura e modelagem.](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

Você pode validar o código manualmente a partir de um diagrama de dependência aberta no Visual Studio ou a partir de um prompt de comando. Você também pode validar código automaticamente ao executar compilações locais ou compilações do Azure Pipelines. Veja [o vídeo do Canal 9: Projete e valide sua arquitetura usando diagramas de dependência](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Se você quiser executar a validação de camadas usando o TEAM Foundation Server (TFS), você também deve instalar a mesma versão do Visual Studio em seu servidor de compilação.

## <a name="live-dependency-validation"></a>Validação de dependência ao vivo

A validação da dependência ocorre em tempo real, e os erros são mostrados imediatamente na **Lista de Erros**.

* A validação ao vivo é suportada para C# e Visual Basic.

* Para habilitar a análise completa da solução ao usar a validação de dependência ao vivo, abra as configurações de opções da barra de ouro que aparece na **Lista de erros**.

  - Você pode descartar permanentemente a barra de ouro se você não estiver interessado em ver todas as questões arquitetônicas em sua solução.
  - Se você não permitir a análise completa da solução, a análise é feita apenas para os arquivos que estão sendo editados.

* Ao atualizar projetos para habilitar a validação ao vivo, um diálogo mostra o progresso da conversão.

* Ao atualizar um projeto para validação de dependência ao vivo, a versão do pacote NuGet é atualizada para ser a mesma para todos os projetos e é a versão mais alta em uso.

* A adição de um novo projeto de validação de dependência ativa uma atualização do projeto.

## <a name="see-if-an-item-supports-validation"></a>Verificar se um item dá suporte à validação

Você pode vincular camadas a sites, documentos do Office, arquivos de texto simples e arquivos em projetos que são compartilhados em vários aplicativos, mas o processo de validação não os incluirá. Os erros de validação não serão exibidos para referências a projetos ou assemblies vinculados a camadas separadas quando nenhuma dependência for exibida entre essas camadas. Essas referências não serão consideradas dependências, a menos que o código use essas referências.

1. No diagrama de dependência, selecione uma ou mais camadas, clique com o botão direito do mouse na seleção e clique **em Exibir Links**.

2. No **Explorador de**camadas, olhe para a coluna Validação de **suportes.** Se o valor for falso, o item não dará suporte à validação.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Incluir outros assemblies e projetos do .NET para validação

Quando você arrasta itens para o diagrama de dependência, as referências aos conjuntos ou projetos .NET correspondentes são adicionadas automaticamente à pasta **Referências** de camada no projeto de modelagem. Essa pasta contém referências aos assemblies e aos projetos analisados durante a validação. Você pode incluir outros conjuntos e projetos .NET para validação sem arrastá-los manualmente para o diagrama de dependência.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto de modelagem ou na pasta **Referências de camada** e clique em Adicionar **referência**.

2. Na caixa de diálogo **Adicionar referência,** selecione as montagens ou projetos e clique em **OK**.

## <a name="validate-code-manually"></a>Validar código manualmente

Se você tiver um diagrama de dependência aberto vinculado a itens de solução, você pode executar o comando **Valid** atalho a partir do diagrama. Você também pode usar o prompt de comando para executar o comando **msbuild** com a propriedade personalizada **/p:ValidateArchitecture** definida como **True**. Por exemplo, à medida que fizer alterações no código, execute a validação da camada regularmente de forma que você possa capturar conflitos de dependência com antecedência.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Validar código de um diagrama de dependência aberta

1. Clique com o botão direito do mouse na superfície do diagrama e clique em **Validar arquitetura**.

    > [!NOTE]
    > Por padrão, a propriedade **Build Action** no arquivo diagrama de dependência (.layerdiagram) está definida como **Validar** para que o diagrama seja incluído no processo de validação.

     A janela **Lista de erros** informa quaisquer erros que ocorram. Para obter mais informações sobre erros de validação, consulte [Problemas de validação de camadas](#troubleshoot-layer-validation-issues).

2. Para visualizar a origem de cada erro, clique duas vezes no erro na janela **Lista de erros.**

    > [!NOTE]
    > O Visual Studio pode mostrar um mapa de código em vez da fonte do erro. Isso ocorre quando o código tem uma dependência de um conjunto que não é especificado pelo diagrama de dependência, ou o código está perdendo uma dependência especificada pelo diagrama de dependência. Revise o mapa de código ou o código para determinar se a dependência deve existir. Para obter mais informações sobre mapas de código, consulte [As dependências do Mapa em suas soluções](../modeling/map-dependencies-across-your-solutions.md).

3. Para gerenciar erros, consulte [Resolver erros de validação de camadas](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Validar o código no prompt de comando

1. Abra o prompt de comando do Visual Studio.

2. Escolha uma destas opções:

   - Para validar o código em relação a um projeto de modelagem específico na solução, execute o MSBuild com a seguinte propriedade personalizada.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - ou –

       Navegue até a pasta que contém o arquivo projeto de modelagem (.modelproj) e o diagrama de dependência e execute o MSBuild com a seguinte propriedade personalizada:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Para validar o código de todos os projetos de modelagem da solução, execute o MSBuild com a seguinte propriedade personalizada:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - ou –

       Navegue até a pasta de solução, que deve conter um projeto de modelagem que contenha um diagrama de dependência e, em seguida, execute o MSBuild com a seguinte propriedade personalizada:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Todos os erros ocorridos serão listados. Para obter mais informações sobre o MSBuild, consulte [MSBuild](../msbuild/msbuild.md) e [MSBuild Task](../msbuild/msbuild-task.md).

   Para obter mais informações sobre erros de validação, consulte [Problemas de validação de camadas](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Gerenciar erros na validação

Durante o processo de desenvolvimento, você talvez queira suprimir alguns dos conflitos reportados durante a validação. Por exemplo, você talvez queira suprimir erros que já esteja resolvendo ou que não sejam relevantes para seu cenário específico. Quando você suprime um erro, é uma boa prática registrar um item de trabalho na Team Foundation.

> [!WARNING]
> Você já deve estar conectado ao TFS Source Code Control (SCC) para criar ou vincular a um item de trabalho. Se você tentar abrir uma conexão com um TFS SCC diferente, o Visual Studio fechará a solução atual automaticamente. Certifique-se de que você já está conectado ao CCS apropriado antes de tentar criar ou vincular a um item de trabalho. Em versões posteriores do Visual Studio, os comandos do menu não estão disponíveis se você não estiver conectado a um SCC.

#### <a name="create-a-work-item-for-a-validation-error"></a>Crie um item de trabalho para um erro de validação

- Na janela **Lista de erros,** clique com o botão direito do mouse no erro, aponte para **Criar item de trabalho**e clique no tipo de item de trabalho que deseja criar.

Use essas tarefas para gerenciar erros de validação na janela **Lista de erros:**

|**Para**|**Siga estes passos**|
|-|-|
|Suprimir erros selecionados durante a validação|Clique com o botão direito do mouse sobre um ou vários erros selecionados, aponte para **Gerenciar erros de validação**e clique em **Supressão de erros**.<br /><br /> Os erros suprimidos são exibidos com formatação de tachado. Quando você executar a validação da próxima vez, esses erros não serão exibidos.<br /><br /> Os erros suprimidos são rastreados em um arquivo .supressão para o arquivo de diagrama de dependência correspondente.|
|Parar a supressão de erros selecionados|Clique com o botão direito do mouse no erro ou erros suprimidos selecionados, aponte para **Gerenciar erros de validação**e clique em Parar **supressão de erros**.<br /><br /> Os erros suprimidos selecionados serão exibidos quando você executar a validação na próxima vez.|
|Restaurar todos os erros suprimidos na janela **Lista de erros**|Clique com o botão direito do mouse em qualquer lugar na janela **Lista de erros,** aponte para **Gerenciar erros de validação**e clique em Mostrar todos os erros **suprimidos**.|
|Ocultar todos os erros suprimidos da janela **Lista de erros**|Clique com o botão direito do mouse em qualquer lugar na janela **Lista de erros,** aponte para **Gerenciar erros de validação**e clique em **Ocultar todos os erros suprimidos**.|

## <a name="validate-code-automatically"></a>Validar código automaticamente

É possível executar a validação da camada sempre que você executa uma compilação local. Se sua equipe usar O Azure DevOps, você poderá executar a validação de camadas com check-ins fechados, que você pode especificar criando uma tarefa MSBuild personalizada e usar relatórios de compilação para coletar erros de validação. Para criar compilações de check-in fechadas, consulte [o check-in fechado TFVC](/azure/devops/pipelines/build/triggers).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Para validar automaticamente o código durante uma compilação local

Use um editor de texto para abrir o arquivo do projeto de modelagem (.modelproj) e, em seguida, inclua a seguinte propriedade:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- ou –

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto de modelagem que contém o diagrama ou diagramas de dependência e clique em **Propriedades**.

2. Na janela **Propriedades,** defina a propriedade **Valid Architecture** do projeto de modelagem como **True**.

    Isso inclui o projeto de modelagem no processo de validação.

3. No **Solution Explorer,** clique no arquivo diagrama de dependência (.layerdiagram) que deseja usar para validação.

4. Na janela **Propriedades,** certifique-se de que a propriedade **'''Ação** de construção' do diagrama esteja definida como **Validar**.

    Isso inclui o diagrama de dependência no processo de validação.

Para gerenciar erros na janela Lista de erros, consulte [Resolver erros de validação de camadas](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Solucionar problemas de validação da camada

A tabela a seguir descreve problemas na validação da camada e sua resolução. Esses problemas são diferentes dos erros resultantes de conflitos entre o código e o design. Para obter mais informações sobre esses erros, consulte [Problemas de validação de camadas](#troubleshoot-layer-validation-issues).

|**Problema**|**Causa Possível**|**Resolução**|
|-|-|-|
|Os erros de validação não ocorrem como esperado.|A validação não funciona em diagramas de dependência que são copiados de outros diagramas de dependência no Solution Explorer e que estão no mesmo projeto de modelagem. diagramas de dependência que são copiados desta forma contêm as mesmas referências do diagrama de dependência original.|Adicione um novo diagrama de dependência ao projeto de modelagem.<br /><br /> Copie os elementos do diagrama de dependência de origem para o novo diagrama.|

## <a name="resolve-layer-validation-errors"></a>Resolver erros de validação de camadas

Quando você valida o código em um diagrama de dependência, erros de validação ocorrem quando o código entra em conflito com o design. Por exemplo, as seguintes condições podem fazer os erros de validação ocorrerem:

- Um artefato é atribuído à camada errada. Nesse caso, mova o artefato.

- Um artefato como, por exemplo, uma classe usa outra classe de maneira a entrar em conflito com a arquitetura. Nesse caso, refatore o código para remover a dependência.

Para resolver esses erros, atualize o código até que mais nenhum erro seja exibido durante a validação. É possível realizar essa tarefa de maneira iterativa.

A seção a seguir descreve a sintaxe usada nesses erros, explica o significado desses erros e sugere o que é possível fazer para o resolver ou gerenciá-los.

|**Sintaxe**|**Descrição**|
|-|-|
|*Artefaton**(ArtifactTypeN)*|*ArtifactN* é um artefato que está associado a uma camada no diagrama de dependência.<br /><br /> *ArtifactTypeN* é o tipo de *ArtifactN,* como uma **Classe** ou **Método,** por exemplo:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NomeNamespaceN*|O nome de um namespace.|
|*NomeCamadaN*|O nome de uma camada no diagrama de dependência.|
|*DependencyType*|O tipo de relação de dependência entre *Artefato1* e *Artefato2*. Por exemplo, *Artifact1* tem uma relação **Chamadas** com *Artifact2*.|

| **Erro de Sintaxe** | **Descrição do erro** |
|-|-|
| DV0001: **Dependência inválida** | Esse problema é relatado quando um elemento de código (namespace, type, member) mapeado para uma camada faz referência a um elemento de código mapeado para outra camada, mas não há nenhuma seta de dependência entre essas camadas no diagrama de validação de dependência que contém essas camadas. Isso é uma violação de restrição de dependência. |
| DV1001: Nome **de namespace inválido** | Este problema é relatado em um elemento de código associado a uma camada que a propriedade "Nomes de Namespace Permitidos" não contém o namespace no qual este elemento de código é definido. Isso é uma violação de restrição de nomeação. Observe que a sintaxe de "Nomes de Namespace Permitidos" deve ser uma lista de espaços de nomes em que os elementos de código associados são permitidos para serem definidos. |
| DV1002: **Dependência do espaço de nome não referencial** | Este problema é relatado em um elemento de código associado a uma camada e fazendo referência a outro elemento de código definido em um namespace que é definido na propriedade "Unreferenceable Namespace" da camada. Isso é uma violação de restrição de nomeação. Observe que a propriedade "Namespaces não referencial" é definida como uma lista separada de espaços de nome semi-colon que não devem ser referenciadas em elementos de código associados a esta camada. |
| DV1003: **Nome de namespace proibido** | Este problema é relatado em um elemento de código associado a uma camada que a propriedade "Nomes de Namespace Proibidos" contém o namespace no qual este elemento de código é definido. Isso é uma violação de restrição de nomeação. Observe que a propriedade "Nome de namespace proibido" é definida como uma lista de espaços de nome separados por semi-colon no qual os elementos de código associados a esta camada não devem ser definidos. |
| DV2001: **Presença do diagrama da camada** | Este problema é relatado em um projeto que não inclui um arquivo de diagrama de dependência, mas refere-se aos analisadores de validação de dependência. Se a Validação de Dependência não tiver sido usada, você pode remover "Microsoft.DependencyValidation.Analyzers" diretamente do Solution Explorer ou suprimir este aviso. Para adicionar um diagrama de dependência, consulte [Criar diagramas de dependência a partir do seu código](../modeling/create-layer-diagrams-from-your-code.md). |
| DV2002: **Base de tipos não mapeados** | Este problema é relatado quando um elemento de código não é mapeado para qualquer camada. |
| DV3001: **Link ausente** | Layer '*LayerName*' links para '*Artefato*' que não podem ser encontrados. Você não tem uma referência de assembly? |
| DV9001: **Análise arquitetônica encontrou erros internos** | Os resultados talvez não estejam completos. Para obter mais informações, consulte o log de eventos da compilação detalhado ou a janela de saída. |

## <a name="see-also"></a>Confira também

- [Validação de dependência ao vivo no Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)
- [Vídeo: Valide suas dependências de arquitetura em tempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
