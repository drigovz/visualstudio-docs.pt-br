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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fc852b4d5003cf809248c72ca3ac42ad3a6bf23
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981128"
---
# <a name="validate-code-with-dependency-diagrams"></a>Validar o código com diagramas de dependência

## <a name="why-use-dependency-diagrams"></a>Por que usar diagramas de dependência?

Para garantir que o código não entre em conflito com seu design, valide seu código com diagramas de dependência no Visual Studio. Isso pode ajudar a:

- Localize conflitos entre dependências em seu código e dependências no diagrama de dependência.

- Encontre dependências que talvez sejam afetadas por alterações propostas.

   Por exemplo, você pode editar o diagrama de dependência para mostrar possíveis alterações de arquitetura e, em seguida, validar o código para ver as dependências afetadas.

- Refatore ou migre o código para um design diferente.

   Encontre o código ou as dependências que exijam trabalho quando você move o código para uma arquitetura diferente.

**Requirements**

- Visual Studio

  Para criar um diagrama de dependência para um projeto do .NET Core, você deve ter o Visual Studio 2019 versão 16,2 ou posterior.

- Uma solução que tem um projeto de modelagem com um diagrama de dependência. Esse diagrama de dependência deve ser vinculado a artefatos no C# ou Visual Basic projetos que você deseja validar. Confira [criar diagramas de dependência do seu código](../modeling/create-layer-diagrams-from-your-code.md).

Para ver quais edições do Visual Studio oferecem suporte a esse recurso, consulte [suporte de edição para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Você pode validar o código manualmente de um diagrama de dependência aberto no Visual Studio ou em um prompt de comando. Você também pode validar o código automaticamente ao executar compilações locais ou Azure Pipelines Builds. Veja [vídeo do Channel 9: projete e valide sua arquitetura usando diagramas de dependência](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Se você quiser executar a validação de camada usando o Team Foundation Server (TFS), também deverá instalar a mesma versão do Visual Studio em seu servidor de compilação.

## <a name="live-dependency-validation"></a>Validação de dependência ao vivo

A validação de dependência ocorre em tempo real e os erros são mostrados imediatamente no **lista de erros**.

* A validação ao vivo tem C# suporte para o e o Visual Basic.

* Para habilitar a análise de solução completa ao usar a validação de dependência ao vivo, abra as configurações de opções da barra de ouro que aparece na **lista de erros**.

  - Você pode ignorar permanentemente a barra de ouro se não estiver interessado em ver todos os problemas arquitetônicos em sua solução.
  - Se você não habilitar a análise completa da solução, a análise será feita apenas para os arquivos que estão sendo editados.

* Ao atualizar projetos para habilitar a validação dinâmica, uma caixa de diálogo mostra o progresso da conversão.

* Ao atualizar um projeto para validação de dependência ao vivo, a versão do pacote NuGet é atualizada para ser a mesma para todos os projetos e é a versão mais alta em uso.

* A adição de um novo projeto de validação de dependência dispara uma atualização de projeto.

## <a name="see-if-an-item-supports-validation"></a>Verificar se um item dá suporte à validação

Você pode vincular camadas a sites, documentos do Office, arquivos de texto sem formatação e arquivos em projetos que são compartilhados entre vários aplicativos, mas o processo de validação não os inclui. Os erros de validação não serão exibidos para referências a projetos ou assemblies vinculados a camadas separadas quando nenhuma dependência for exibida entre essas camadas. Essas referências não serão consideradas dependências, a menos que o código use essas referências.

1. No diagrama de dependência, selecione uma ou mais camadas, clique com o botão direito do mouse em sua seleção e clique em **exibir links**.

2. No **Gerenciador de camadas**, examine a coluna de **validação de suporte** . Se o valor for falso, o item não dará suporte à validação.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Incluir outros assemblies e projetos do .NET para validação

Quando você arrasta itens para o diagrama de dependência, as referências aos assemblies ou projetos do .NET correspondentes são adicionadas automaticamente à pasta de **referências de camada** no projeto de modelagem. Essa pasta contém referências aos assemblies e aos projetos analisados durante a validação. Você pode incluir outros assemblies e projetos .NET para validação sem arrastá-los manualmente para o diagrama de dependência.

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto de modelagem ou na pasta **referências de camada** e clique em **Adicionar referência**.

2. Na caixa de diálogo **Adicionar referência** , selecione os assemblies ou projetos e clique em **OK**.

## <a name="validate-code-manually"></a>Validar código manualmente

Se você tiver um diagrama de dependência aberto vinculado a itens de solução, poderá executar o comando **validar** atalho do diagrama. Você também pode usar o prompt de comando para executar o comando do **MSBuild** com a propriedade personalizada **/p: ValidateArchitecture** definida como **true**. Por exemplo, à medida que fizer alterações no código, execute a validação da camada regularmente de forma que você possa capturar conflitos de dependência com antecedência.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Validar o código de um diagrama de dependência aberto

1. Clique com o botão direito do mouse na superfície do diagrama e clique em **validar arquitetura**.

    > [!NOTE]
    > Por padrão, a propriedade de **ação de compilação** no arquivo de diagrama de dependência (. layerdiagram) é definida como **validar** para que o diagrama seja incluído no processo de validação.

     A janela **lista de erros** relata os erros que ocorrem. Para obter mais informações sobre erros de validação, consulte [solucionar problemas de validação de camada](#troubleshoot-layer-validation-issues).

2. Para exibir a origem de cada erro, clique duas vezes no erro na janela **lista de erros** .

    > [!NOTE]
    > O Visual Studio pode mostrar um mapa de código em vez da origem do erro. Isso ocorre quando o código tem uma dependência em um assembly que não é especificado pelo diagrama de dependência ou o código não tem uma dependência especificada pelo diagrama de dependência. Examine o mapa de código ou o código para determinar se a dependência deve existir. Para obter mais informações sobre mapas de código, consulte [mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md).

3. Para gerenciar erros, consulte [resolver erros de validação de camada](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Validar o código no prompt de comando

1. Abra o prompt de comando do Visual Studio.

2. Escolha uma das seguintes opções:

   - Para validar o código em um projeto de modelagem específico na solução, execute o MSBuild com a seguinte propriedade personalizada.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - ou –

       Navegue até a pasta que contém o arquivo de projeto de modelagem (. modelproj) e o diagrama de dependência e, em seguida, execute o MSBuild com a seguinte propriedade personalizada:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Para validar o código em todos os projetos de modelagem na solução, execute o MSBuild com a seguinte propriedade personalizada:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - ou –

       Navegue até a pasta da solução, que deve conter um projeto de modelagem que contém um diagrama de dependência e, em seguida, execute o MSBuild com a seguinte propriedade personalizada:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Todos os erros ocorridos serão listados. Para obter mais informações sobre o MSBuild, consulte [MSBuild](../msbuild/msbuild.md) e [MSBuild Task](../msbuild/msbuild-task.md).

   Para obter mais informações sobre erros de validação, consulte [solucionar problemas de validação de camada](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Gerenciar erros na validação

Durante o processo de desenvolvimento, você talvez queira suprimir alguns dos conflitos reportados durante a validação. Por exemplo, você talvez queira suprimir erros que já esteja resolvendo ou que não sejam relevantes para seu cenário específico. Ao suprimir um erro, é uma prática recomendada registrar um item de trabalho no Team Foundation.

> [!WARNING]
> Você já deve estar conectado ao SCC (controle de código-fonte) do TFS para criar ou vincular a um item de trabalho. Se você tentar abrir uma conexão com um outro TFS SCC, o Visual Studio fechará a solução atual automaticamente. Verifique se você já está conectado ao SCC apropriado antes de tentar criar ou vincular a um item de trabalho. Em versões posteriores do Visual Studio, os comandos de menu não estarão disponíveis se você não estiver conectado a um SCC.

#### <a name="create-a-work-item-for-a-validation-error"></a>Criar um item de trabalho para um erro de validação

- Na janela **lista de erros** , clique com o botão direito do mouse no erro, aponte para **Criar item de trabalho**e clique no tipo de item de trabalho que você deseja criar.

Use estas tarefas para gerenciar erros de validação na janela de **lista de erros** :

|**To**|**Siga estas etapas**|
|-|-|
|Suprimir erros selecionados durante a validação|Clique com o botão direito do mouse em um ou vários erros selecionados, aponte para **Gerenciar erros de validação**e clique em **suprimir erros**.<br /><br /> Os erros suprimidos são exibidos com formatação de tachado. Quando você executar a validação da próxima vez, esses erros não serão exibidos.<br /><br /> Erros suprimidos são rastreados em um arquivo. supressões para o arquivo de diagrama de dependência correspondente.|
|Parar a supressão de erros selecionados|Clique com o botão direito do mouse no erro ou erros suprimidos selecionados, aponte para **Gerenciar erros de validação**e clique em **parar de suprimir erros**.<br /><br /> Os erros suprimidos selecionados serão exibidos quando você executar a validação na próxima vez.|
|Restaurar todos os erros suprimidos na janela de **lista de erros**|Clique com o botão direito do mouse em qualquer lugar na janela **lista de erros** , aponte para **Gerenciar erros de validação**e clique em **Mostrar todos os erros suprimidos**.|
|Ocultar todos os erros suprimidos da janela de **lista de erros**|Clique com o botão direito do mouse em qualquer lugar na janela **lista de erros** , aponte para **Gerenciar erros de validação**e clique em **ocultar todos os erros suprimidos**.|

## <a name="validate-code-automatically"></a>Validar código automaticamente

É possível executar a validação da camada sempre que você executa uma compilação local. Se sua equipe usa o Azure DevOps, você pode executar a validação de camada com check-ins restritos, que você pode especificar criando uma tarefa personalizada do MSBuild e usar os relatórios de compilação para coletar erros de validação. Para criar compilações de check-in restringidas, consulte [check-in restrito do TFVC](/azure/devops/pipelines/build/triggers#gated).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Para validar automaticamente o código durante uma compilação local

Use um editor de texto para abrir o arquivo do projeto de modelagem (.modelproj) e, em seguida, inclua a seguinte propriedade:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- ou -

1. No **Gerenciador de soluções**, clique com o botão direito do mouse no projeto de modelagem que contém o diagrama de dependência ou diagramas e clique em **Propriedades**.

2. Na janela **Propriedades** , defina a propriedade de arquitetura de **validação** do projeto de modelagem como **true**.

    Isso inclui o projeto de modelagem no processo de validação.

3. Em **Gerenciador de soluções**, clique no arquivo de diagrama de dependência (. layerdiagram) que você deseja usar para validação.

4. Na janela **Propriedades** , verifique se a propriedade **ação de Build** do diagrama está definida como **validar**.

    Isso inclui o diagrama de dependência no processo de validação.

Para gerenciar erros na janela de Lista de Erros, consulte [resolver erros de validação de camada](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Solucionar problemas de validação da camada

A tabela a seguir descreve problemas na validação da camada e sua resolução. Esses problemas são diferentes dos erros resultantes de conflitos entre o código e o design. Para obter mais informações sobre esses erros, consulte [solucionar problemas de validação de camada](#troubleshoot-layer-validation-issues).

|**Lo**|**Causa possível**|**Resolução**|
|-|-|-|
|Os erros de validação não ocorrem como esperado.|A validação não funciona em diagramas de dependência que são copiados de outros diagramas de dependência no Gerenciador de Soluções e que estão no mesmo projeto de modelagem. os diagramas de dependência que são copiados dessa forma contêm as mesmas referências que o diagrama de dependência original.|Adicione um novo diagrama de dependência ao projeto de modelagem.<br /><br /> Copie os elementos do diagrama de dependência de origem para o novo diagrama.|

## <a name="resolve-layer-validation-errors"></a>Resolver erros de validação de camada

Quando você valida o código em um diagrama de dependência, os erros de validação ocorrem quando o código está em conflito com o design. Por exemplo, as seguintes condições podem fazer os erros de validação ocorrerem:

- Um artefato é atribuído à camada errada. Nesse caso, mova o artefato.

- Um artefato como, por exemplo, uma classe usa outra classe de maneira a entrar em conflito com a arquitetura. Nesse caso, refatore o código para remover a dependência.

Para resolver esses erros, atualize o código até que mais nenhum erro seja exibido durante a validação. É possível realizar essa tarefa de maneira iterativa.

A seção a seguir descreve a sintaxe usada nesses erros, explica o significado desses erros e sugere o que é possível fazer para o resolver ou gerenciá-los.

|**Sintaxe**|**Descrição**|
|-|-|
|*Artefaton*(*ArtifactTypeN*)|O *artefaton* é um artefato associado a uma camada no diagrama de dependência.<br /><br /> *ArtifactTypeN* é o tipo de *artefaton*, como uma **classe** ou um **método**, por exemplo:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|O nome de um namespace.|
|*LayerNameN*|O nome de uma camada no diagrama de dependência.|
|*DependencyType*|O tipo de relação de dependência entre *Artifact1* e *Artifact2*. Por exemplo, *Artifact1* tem uma relação de **chamadas** com *Artifact2*.|

| **Sintaxe de erro** | **Descrição do erro** |
|-|-|
| DV0001: **dependência inválida** | Esse problema é relatado quando um elemento de código (namespace, tipo, membro) mapeado para uma camada faz referência a um elemento de código mapeado para outra camada, mas não há nenhuma seta de dependência entre essas camadas no diagrama de validação de dependência que contém essas camadas. Essa é uma violação de restrição de dependência. |
| DV1001: **nome de namespace inválido** | Esse problema é relatado em um elemento de código associado a uma camada que a propriedade "nomes de namespace permitidos" não contém o namespace no qual esse elemento de código está definido. Esta é uma violação de restrição de nomenclatura. Observe que a sintaxe de "nomes de namespace permitidos" é uma lista ponto-e-vírgula dos namespaces nos quais os elementos de código associados à camada têm permissão para serem definidos. |
| DV1002: **dependência de namespace não referenciable** | Esse problema é relatado em um elemento de código associado a uma camada e referenciando outro elemento de código definido em um namespace que é definido na propriedade "namespace não referenciable" da camada. Esta é uma violação de restrição de nomenclatura. Observe que a propriedade "namespaces não referenciable" é definida como uma lista separada por ponto-e-vírgula de namespaces que não devem ser referenciados em elementos de código associados a essa camada. |
| DV1003: **nome de namespace não permitido** | Esse problema é relatado em um elemento de código associado a uma camada que a propriedade "nomes de namespaces não permitidos" contém o namespace no qual esse elemento de código está definido. Esta é uma violação de restrição de nomenclatura. Observe que a propriedade "nome do namespace não permitido" é definida como uma lista separada por ponto e vírgula de namespaces nos quais elementos de código associados a essa camada não devem ser definidos. |
| DV3001: **link ausente** | A camada '*LayerName*' vincula-se ao '*artefato*', que não foi encontrado. Você não tem uma referência de assembly? |
| DV9001: **análise de arquitetura encontrou erros internos** | Os resultados talvez não estejam completos. Para obter mais informações, consulte o log de eventos da compilação detalhado ou a janela de saída. |

## <a name="see-also"></a>Consulte também

- [Validação de dependência ao vivo no Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)
- [Vídeo: valide suas dependências de arquitetura em tempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
