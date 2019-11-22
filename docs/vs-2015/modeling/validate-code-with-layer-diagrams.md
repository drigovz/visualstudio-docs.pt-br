---
title: Validar código com diagramas de camada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 596711c5c59738d5356437bb761e80caeddfbd6b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301355"
---
# <a name="validate-code-with-layer-diagrams"></a>Validar o código com diagramas de camada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para garantir que o código não entre em conflito com seu design, valide seu código com diagramas de camada no Visual Studio. Isso pode ajudar a:

- Encontrar conflitos entre dependências no código e nas dependências do diagrama de camada.

- Encontre dependências que talvez sejam afetadas por alterações propostas.

   Por exemplo, é possível editar o diagrama de camada para mostrar alterações na arquitetura em potencial e, em seguida, validar o código para ver as dependências afetadas.

- Refatore ou migre o código para um design diferente.

   Encontre o código ou as dependências que exijam trabalho quando você move o código para uma arquitetura diferente.

  **Requisitos**

- Visual Studio

- Visual Studio em seu servidor de compilação do Team Foundation para validar o código automaticamente com o Team Foundation Build

- Uma solução com um projeto de modelagem com um diagrama de camada. Esse diagrama de camada deve ser vinculado aos artefatos e projetos do Visual C# .NET ou do Visual Basic .NET que você deseja validar. Consulte [criar diagramas de camada do seu código](../modeling/create-layer-diagrams-from-your-code.md).

  Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

  É possível validar manualmente o código com base em um diagrama de camada aberto no Visual Studio ou em um prompt de comando. Também é possível validar o código automaticamente durante a execução de compilações locais ou do Team Foundation Build. Veja [vídeo do Channel 9: projete e valide sua arquitetura usando diagramas de camada](https://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Se você quiser executar a validação de camada com o Team Foundation Build, também deverá instalar a mesma versão do Visual Studio em seu servidor de compilação.

- [Ver se um item dá suporte à validação](#SupportsValidation)

- [Incluir outros assemblies e projetos .NET para validação](#IncludeReferences)

- [Validar o código manualmente](#ValidateManually)

- [Validar o código automaticamente](#ValidateAuto)

- [Solucionar problemas de validação de camada](#TroubleshootingValidation)

- [Entender e resolver erros de validação de camada](#UnderstandingValidationErrors)

## <a name="SupportsValidation"></a>Ver se um item dá suporte à validação
 É possível vincular camadas a sites, documentos do Office, arquivos de texto sem formatação e arquivos em projetos compartilhados entre vários aplicativos, mas o processo de validação não os incluirá. Os erros de validação não serão exibidos para referências a projetos ou assemblies vinculados a camadas separadas quando nenhuma dependência for exibida entre essas camadas. Essas referências não serão consideradas dependências, a menos que o código use essas referências.

1. No diagrama de camada, selecione uma ou mais camadas, clique com o botão direito do mouse na seleção e, em seguida, clique em **Exibir Links**.

2. Em **Gerenciador de Camadas**, examine a coluna **Dá Suporte à Validação**. Se o valor for falso, o item não dará suporte à validação.

## <a name="IncludeReferences"></a>Incluir outros assemblies e projetos .NET para validação
 Quando você arrasta itens para o diagrama de camada, as referências para os assemblies ou projetos do .NET correspondentes são adicionadas automaticamente à pasta **Referências de Camada** no projeto de modelagem. Essa pasta contém referências aos assemblies e aos projetos analisados durante a validação. É possível incluir outros assemblies e projetos do .NET para avaliação sem arrastá-los manualmente para o diagrama de camada.

1. No **Gerenciador de Soluções**, clique com botão direito do mouse no projeto de modelagem ou na pasta **Referências de Camada** e, em seguida, clique em **Adicionar Referência**.

2. Na caixa de diálogo **Adicionar Referência**, selecione os assemblies ou os projetos e, em seguida, clique em **OK**.

## <a name="ValidateManually"></a>Validar o código manualmente
 Se tiver um diagrama de camada aberto vinculado a itens de solução, você poderá executar o comando de atalho **Validar** no diagrama. Você também pode usar o prompt de comando para executar o comando do **MSBuild** com a propriedade personalizada **/p: ValidateArchitecture** definida como **true**. Por exemplo, à medida que fizer alterações no código, execute a validação da camada regularmente de forma que você possa capturar conflitos de dependência com antecedência.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Para validar o código com base em um diagrama de camada aberto

1. Clique com o botão direito do mouse na superfície do diagrama e, em seguida, clique em **Validar Arquitetura**.

    > [!NOTE]
    > Por padrão, a propriedade **Compilar Ação** no arquivo do diagrama de camada (.layerdiagram) é definida como **Validar**, de forma que o diagrama seja incluído no processo de validação.

     A janela **Lista de Erros** relata todos os erros ocorridos. Para obter mais informações sobre erros de validação, consulte [Compreender e resolver erros na validação de camada](#UnderstandingValidationErrors).

2. Para exibir a origem de cada erro, clique duas vezes no erro na janela **Lista de Erros**.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pode mostrar um mapa de código em vez da origem do erro. Isso ocorre quando o código tem uma dependência em um assembly não especificado pelo diagrama de camada ou o código não tem uma dependência especificada pelo diagrama de camada. Examine o mapa de código ou o código para determinar se a dependência deve existir. Para obter mais informações sobre mapas de código, consulte [mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md).

3. Para gerenciar erros, consulte [Gerenciar erros de validação](#ManageErrors).

#### <a name="to-validate-code-at-the-command-prompt"></a>Para validar o código no prompt de comando

1. Abra o prompt de comando do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Escolha uma das seguintes opções:

   - Para validar o código em um projeto de modelagem específico na solução, execute [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] com a propriedade personalizada a seguir.

     ```
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
     ```

     - ou –

       Navegue até a pasta que contém o arquivo de modelagem do projeto (.modelproj) e o diagrama de camada e, em seguida, execute [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] com a seguinte propriedade personalizada:

     ```
     msbuild /p:ValidateArchitecture=true
     ```

   - Para validar o código em todos os projeto de modelagem na solução, execute [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] com a propriedade personalizada a seguir:

     ```
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
     ```

     - ou –

       Navegue até a pasta da solução, que deve conter um projeto de modelagem com um diagrama de camada e, em seguida, execute [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] com a seguinte propriedade personalizada:

     ```
     msbuild /p:ValidateArchitecture=true
     ```

     Todos os erros ocorridos serão listados. Para obter mais informações sobre [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], consulte [MSBuild](../msbuild/msbuild.md) e [MSBuild Task](../msbuild/msbuild-task.md).

   Para obter mais informações sobre erros de validação, consulte [Compreender e resolver erros na validação de camada](#UnderstandingValidationErrors).

### <a name="ManageErrors"></a>Gerenciar erros de validação
 Durante o processo de desenvolvimento, você talvez queira suprimir alguns dos conflitos reportados durante a validação. Por exemplo, você talvez queira suprimir erros que já esteja resolvendo ou que não sejam relevantes para seu cenário específico. Quando você suprime um erro, é uma prática recomendada registrar em log um item de trabalho em [!INCLUDE[esprfound](../includes/esprfound-md.md)].

> [!WARNING]
> Você já deve estar conectado ao SCC (controle de código-fonte) do TFS para criar ou vincular a um item de trabalho. Se você tentar abrir uma conexão com um outro TFS SCC, o Visual Studio fechará a solução atual automaticamente. Verifique se você já está conectado ao SCC apropriado antes de tentar criar ou vincular a um item de trabalho. Em versões posteriores do Visual Studio, os comandos de menu não estarão disponíveis se você não estiver conectado a um SCC.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>Para criar um item de trabalho para um erro de validação

- Na janela **Lista de Erros**, clique com o botão direito do mouse no erro, aponte para **Criar Item de Trabalho** e, em seguida, clique no tipo de item de trabalho que você deseja criar.

  Use essas tarefas para gerenciar erros de validação na janela **Lista de Erros**:

|**To**|**Siga estas etapas**|
|------------|----------------------------|
|Suprimir erros selecionados durante a validação|Clique com o botão direito do mouse em um ou em vários erros selecionados, aponte para **Gerenciar Erros de Validação** e, em seguida, clique em **Suprimir Erros**.<br /><br /> Os erros suprimidos são exibidos com formatação de tachado. Quando você executar a validação da próxima vez, esses erros não serão exibidos.<br /><br /> Os erros suprimidos são acompanhados em um arquivo .suppressions para o arquivo do diagrama de camada correspondente.|
|Parar a supressão de erros selecionados|Clique com o botão direito do mouse no erro ou nos erros suprimidos selecionados, aponte para **Gerenciar Erros de Validação** e, em seguida, clique em **Parar de Suprimir Erros**.<br /><br /> Os erros suprimidos selecionados serão exibidos quando você executar a validação na próxima vez.|
|Restaurar todos os erros suprimidos na janela **Lista de Erros**|Clique com o botão direito do mouse em qualquer lugar na janela **Lista de Erros**, aponte para **Gerenciar Erros de Validação** e, em seguida, clique em **Mostrar Todos os Erros Suprimidos**.|
|Ocultar todos os erros suprimidos na janela **Lista de Erros**|Clique com o botão direito do mouse em qualquer lugar na janela **Lista de Erros**, aponte para **Gerenciar Erros de Validação** e, em seguida, clique em **Ocultar Todos os Erros Suprimidos**.|

## <a name="ValidateAuto"></a>Validar o código automaticamente
 É possível executar a validação da camada sempre que você executa uma compilação local. Se a equipe usar o Team Foundation Build, será possível executar a validação da camada com check-ins restritos, que você pode especificar criando uma tarefa MSBuild personalizada, e usar relatórios de compilação para coletar erros de validação. Para criar compilações de check-in restringidas, consulte [usar um processo de compilação de check-in restrito para validar as alterações](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>Para validar automaticamente o código durante uma compilação local

- Use um editor de texto para abrir o arquivo do projeto de modelagem (.modelproj) e, em seguida, inclua a seguinte propriedade:

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- ou -

1. No **Gerenciador de Soluções**, clique com botão direito do mouse no projeto de modelagem que contém o diagrama ou os diagramas de camada e, em seguida, clique em **Propriedades**.

2. Na janela **Propriedades**, defina a propriedade **Validar Arquitetura** do projeto de modelagem como **Verdadeiro**.

    Isso inclui o projeto de modelagem no processo de validação.

3. No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo do diagrama de camada (.layerdiagram) que você talvez queira usar na validação.

4. Na janela **Propriedades**, verifique se a propriedade **Compilar Ação** do diagrama está definida como **Validar**.

    Isso inclui o diagrama de camada no processo de validação.

   Para gerenciar erros na janela Lista de Erros, consulte [Gerenciar Erros de Validação](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Para validar automaticamente o código durante um Team Foundation Build

1. No **Team Explorer**, clique duas vezes na definição da compilação e, em seguida, clique em **Processo**.

2. Em **Parâmetros do processo de compilação**, expanda **Compilação** e digite o seguinte no parâmetro **Argumentos de MSBuild**:

    `/p:ValidateArchitecture=true`

   Para obter mais informações sobre erros de validação, consulte [Compreender e resolver erros na validação de camada](#UnderstandingValidationErrors). Para obter mais informações sobre [!INCLUDE[esprbuild](../includes/esprbuild-md.md)], consulte:

- [Compilar o aplicativo](/azure/devops/pipelines/index)

- [Usar o modelo padrão para seu processo de compilação](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [Modificar uma compilação herdada baseada em UpgradeTemplate. XAML](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [Personalizar o modelo de processo de compilação](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [Monitorar o progresso de uma compilação em execução](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="TroubleshootingValidation"></a>Solucionar problemas de validação de camada
 A tabela a seguir descreve problemas na validação da camada e sua resolução. Esses problemas são diferentes dos erros resultantes de conflitos entre o código e o design. Para obter mais informações sobre esses erros, consulte [Compreender e resolver erros na validação de camada](#UnderstandingValidationErrors).

|**Lo**|**Causa possível**|**Resolução**|
|---------------|------------------------|--------------------|
|Os erros de validação não ocorrem como esperado.|A validação não funciona em diagramas de camada copiados de outros diagramas de camada no Gerenciador de Soluções e que estejam no mesmo projeto de modelagem. Os diagramas de camada copiados dessa maneira contêm as mesmas referências do diagrama de camada original.|Adicione um novo diagrama de camada ao projeto de modelagem.<br /><br /> Copie os elementos do diagrama de camada de origem para o novo diagrama.|

## <a name="UnderstandingValidationErrors"></a>Compreendendo e Resolvendo erros de validação de camada
 Quando você valida o código em um diagrama de camada, os erros de validação ocorrem quando o código entra em conflito com o design. Por exemplo, as seguintes condições podem fazer os erros de validação ocorrerem:

- Um artefato é atribuído à camada errada. Nesse caso, mova o artefato.

- Um artefato como, por exemplo, uma classe usa outra classe de maneira a entrar em conflito com a arquitetura. Nesse caso, refatore o código para remover a dependência.

  Para resolver esses erros, atualize o código até que mais nenhum erro seja exibido durante a validação. É possível realizar essa tarefa de maneira iterativa.

  A seção a seguir descreve a sintaxe usada nesses erros, explica o significado desses erros e sugere o que é possível fazer para o resolver ou gerenciá-los.

|**Sintaxe**|**Descrição**|
|----------------|---------------------|
|*ArtifactN*(*ArtifactTypeN*)|O *artefaton* é um artefato associado a uma camada no diagrama de camadas.<br /><br /> *ArtifactTypeN* é o tipo de *artefaton*, como uma **classe** ou um **método**, por exemplo:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|O nome de um namespace.|
|*LayerNameN*|O nome de uma camada no diagrama de camada.|
|*DependencyType*|O tipo de relação de dependência entre *Artefato1* e *Artefato2*. Por exemplo, *Artefato1* tem uma relação **Chamadas** com *Artefato2*.|

|**Sintaxe de erro**|**Descrição do erro**|
|----------------------|---------------------------|
|AV0001: Dependência inválida: *Artefato1*(*TipoArtefato1*) --> *Artefato2*(*TipoArtefato2*)<br /><br /> Camadas: *LayerName1*, dependências de *LayerName2* &#124; : *DependencyType*|*Artifact1* em *LayerName1* não deve ter uma dependência em *Artifact2* no *LayerName2* porque *LayerName1* não tem uma dependência direta em *LayerName2*.|
|AV1001: Namespace Inválido: *Artefato*<br /><br /> Camada: *LayerName* &#124; obrigatório namespace: *NamespaceName1* &#124; Current namespace: *NamespaceName2*|{1&gt;NomeCamada&lt;1} exige que seus artefatos associados devam pertencer a {2&gt;NomeNamespace1&lt;2}. O *artefato* está em *NamespaceName2*, não *NamespaceName1*.|
|AV1002: depende do namespace proibido: *Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> Camada: nome da *camada* &#124; proibido namespace: dependências de *NamespaceName* &#124; : *DependencyType*|{1&gt;NomeCamada&lt;1} exige que seus artefatos associados não devam depender de {2&gt;NomeNamespace&lt;2}. {1&gt;Artefato1&lt;1} não pode depender do {2&gt;Artefato2&lt;2} porque o {3&gt;Artefato2&lt;3} está no {4&gt;NomeNamespace&lt;4}.|
|AV1003: No Namespace Proibido: *Artefato*(*TipoArtefato*)<br /><br /> Camada: namespace de *LayerName* &#124; proibido: *NamespaceName*|O *LayerName* requer que seus artefatos associados não possam pertencer a *NamespaceName*. O *artefato* pertence a *NamespaceName*.|
|AV3001: Link Ausente: não foi possível encontrar os links da camada '*NomeCamada*' com o '*Artefato*'. Você não tem uma referência de assembly?|Os links de *LayerName* para um artefato que não podem ser encontrados. Por exemplo, um link para uma classe talvez não seja encontrado porque o projeto de modelagem não tem uma referência para o assembly que contém a classe.|
|AV9001: A análise arquitetônica encontrou erros internos. Os resultados talvez não estejam completos. Para obter mais informações, consulte o log de eventos da compilação detalhado ou a janela de saída.|Consulte o log de eventos da compilação ou a janela de saída para obter mais detalhes.|

## <a name="security"></a>Segurança

## <a name="see-also"></a>Consulte também
 [Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)
