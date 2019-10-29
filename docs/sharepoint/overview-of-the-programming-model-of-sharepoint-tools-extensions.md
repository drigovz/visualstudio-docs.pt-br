---
title: Visão geral do modelo de programação das extensões de ferramentas do SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 160751e7f580ede458232f98dc753a1145094f57
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985139"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Visão geral do modelo de programação das extensões de ferramentas do SharePoint
  Ao criar uma extensão para as ferramentas do SharePoint no Visual Studio, você começa implementando uma ou mais interfaces de extensibilidade que são expostas pelas ferramentas do SharePoint. Na maioria dos casos, você também usará outros tipos fornecidos pelas ferramentas do SharePoint para implementar recursos em sua extensão. Em alguns cenários, você também pode usar tipos em outros modelos de objeto fornecidos pelo Visual Studio e pelo SharePoint. Você deve entender a finalidade de cada um desses modelos de objeto e saber como usá-los entre si para criar extensões para as ferramentas do SharePoint.

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Estenda as ferramentas do SharePoint implementando interfaces de extensibilidade
 O Visual Studio usa o Managed Extensibility Framework (MEF) no .NET Framework 4 para fornecer o modelo de extensibilidade para as ferramentas do SharePoint. O MEF é uma API (implementada no assembly System. ComponentModel. composição) que permite que os aplicativos exponham pontos de extensibilidade e descubram e carreguem extensões em tempo de execução. Para obter mais informações sobre o MEF [, &#40;consulte&#41;Managed Extensibility Framework MEF](/dotnet/framework/mef/index).

 Para estender as ferramentas do SharePoint, implemente uma ou mais interfaces de extensibilidade que são expostas pelo Visual Studio. Você também deve aplicar o <xref:System.ComponentModel.Composition.ExportAttribute>e atributos específicos de ferramentas adicionais do SharePoint, conforme necessário, à implementação da interface. A tabela a seguir lista as interfaces que você pode implementar para estender as ferramentas do SharePoint.

|Interface|Descrição|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implemente essa interface para definir um novo tipo de item de projeto do SharePoint. Para obter um exemplo, consulte [como: definir um tipo de item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implemente essa interface para estender um tipo de item de projeto do SharePoint que já está instalado no Visual Studio. Para obter um exemplo, consulte [como: criar uma extensão de item de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implemente essa interface para estender projetos do SharePoint. Para obter um exemplo, consulte [como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implemente essa interface para definir uma nova etapa de implantação que pode ser executada quando um item de projeto do SharePoint é implantado ou cancelado. Para obter um exemplo, consulte [Walkthrough: criar uma etapa de implantação personalizada para projetos do SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implemente essa interface para estender um nó existente no nó **conexões do SharePoint** na janela **Gerenciador de servidores** . Para obter um exemplo, consulte [como: estender um nó do SharePoint no Gerenciador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implemente essa interface para definir um novo tipo de nó no nó **conexões do SharePoint** na janela **Gerenciador de servidores** . Para obter um exemplo, consulte [como: estender um nó do SharePoint no Gerenciador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implemente essa interface para definir uma regra de validação de recurso personalizada. Para obter um exemplo, consulte [como criar regras personalizadas de validação de pacote e de recurso para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implemente essa interface para definir uma regra de validação de pacote personalizada. Para obter um exemplo, consulte [como criar regras personalizadas de validação de pacote e de recurso para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

 Depois de implementar uma extensão das ferramentas do SharePoint, você deve implantar o assembly de extensão em um pacote de VSIX (extensão do Visual Studio) para permitir que o Visual Studio descubra e carregue a extensão. Para obter mais informações, consulte [implantar extensões para as ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Entender os modelos de objeto que você usa nas extensões de ferramentas do SharePoint
 Há vários modelos de objeto que você pode usar ao criar extensões para as ferramentas do SharePoint:

- *Modelo de objeto das ferramentas do SharePoint*. Esse modelo de objeto fornece as interfaces de extensibilidade que você implementa para criar extensões de ferramentas do SharePoint e outros tipos relacionados.

- *Modelos de objeto de integração e automação do Visual Studio*. Use esses modelos de objeto para acessar recursos do Visual Studio que estão além do escopo do modelo de objeto das ferramentas do SharePoint.

    > [!NOTE]
    > Você pode converter alguns objetos no modelo de objeto de ferramentas do SharePoint em objetos nos modelos de objeto de automação e integração do Visual Studio e vice-versa, usando o serviço de projeto do SharePoint. Para obter mais informações, consulte [converter entre tipos de sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

- *Modelos de objeto de cliente e servidor do SharePoint*. Use esses modelos de objeto para modificar um site do SharePoint ou para recuperar dados de um site do SharePoint do contexto de uma extensão de ferramentas do SharePoint.

### <a name="sharepoint-tools-object-model"></a>Modelo de objeto das ferramentas do SharePoint
 Cada extensão das ferramentas do SharePoint usa tipos no modelo de objeto das ferramentas do SharePoint para definir o comportamento principal e a funcionalidade da extensão. As tabelas a seguir descrevem os namespaces que são incluídos nesse modelo de objeto, pelo assembly que os contém.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll

|espaço de nome|Descrição|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint>|Contém tipos que você usa para estender e automatizar o sistema de projeto do SharePoint. Por exemplo, você pode estender os projetos internos do SharePoint e os itens do projeto, ou pode criar seus próprios itens de projeto. Para obter mais informações, consulte [estender o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Contém tipos que você usa para estender o processo de implantação para projetos do SharePoint, como criar suas próprias etapas de implantação e configurações de implantação. Para obter mais informações, consulte [estender o empacotamento e a implantação do SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Contém tipos que você usa para estender nós sob o nó **conexões do SharePoint** na janela **Gerenciador de servidores** ou para definir novos tipos de nós. Para obter mais informações, consulte [estender o nó conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Features>|Contém tipos que você usa para acessar as definições de recurso em um projeto do SharePoint.|
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Contém tipos que você usa para acessar a definição de pacote em uma solução do SharePoint.|
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|Contém tipos que você usa para personalizar o recurso e o comportamento de validação do pacote para projetos do SharePoint. Para obter mais informações, consulte [como criar regras personalizadas de validação de pacotes e recursos para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft. VisualStudio. SharePoint. Commands. dll

|espaço de nome|Descrição|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Contém tipos que você pode usar para criar *comandos personalizados do SharePoint*. Um comando do SharePoint é um método que chama o modelo de objeto do SharePoint Server a partir de uma extensão de ferramentas do SharePoint. Para obter mais informações, consulte [chamar os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft. VisualStudio. SharePoint. Explorer. Extensions. dll

|espaço de nome|Descrição|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Contém tipos que você pode usar para obter informações sobre nós de **Gerenciador de servidores** internos que representam componentes individuais em um site do SharePoint, como um nó que representa uma lista, um campo ou um tipo de conteúdo. Para obter mais informações, consulte [estender o nó conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|

### <a name="visual-studio-automation-object-model"></a>Modelo de objeto de automação do Visual Studio
 O modelo de objeto de automação do Visual Studio fornece APIs que você pode usar para automatizar projetos do Visual Studio e o IDE. Use o modelo de objeto do Visual Studio para executar tarefas relacionadas ao projeto que não são específicas para projetos do SharePoint ou para executar outras tarefas gerais de automação no Visual Studio. Tradicionalmente, esse modelo de objeto é geralmente usado em suplementos e macros do Visual Studio, mas você também pode usá-lo em extensões de ferramentas do SharePoint.

 A parte principal do modelo de objeto de automação do Visual Studio é definida no assembly *EnvDTE. dll* . O *EnvDTE\\\<versão >. dll* assemblies fornecem funcionalidades adicionais que foram introduzidas em versões específicas do Visual Studio. Esses assemblies estão incluídos no Visual Studio.

 Para obter mais informações sobre o modelo de objeto de automação, consulte [referência do SDK do Visual Studio](../extensibility/visual-studio-sdk-reference.md).

### <a name="visual-studio-integration-object-model"></a>Modelo de objeto de integração do Visual Studio
 O modelo de objeto de integração fornece APIs que você pode usar para adicionar recursos ao Visual Studio criando um *VSPackage*. Um VSPackage é um módulo que estende o IDE do Visual Studio fornecendo recursos personalizados, como janelas de ferramentas, editores, designers, serviços e projetos.

 Você pode usar o modelo de objeto de integração se quiser adicionar um novo recurso do Visual Studio que será usado com as ferramentas internas do SharePoint. Por exemplo, se você criar um item de projeto personalizado do SharePoint que representa uma ação personalizada para um site do SharePoint, também poderá criar um VSPackage que implemente um designer para a ação personalizada. Você pode associar o designer à ação personalizada adicionando um item de menu de atalho ao item de projeto que representa a ação personalizada no **Gerenciador de soluções**. Você pode abrir seu designer abrindo o menu de atalho (clicando com o botão direito do mouse no item de projeto de ação personalizada ou escolhendo-o e escolhendo a **tecla Shift**+teclas **F10** ) e, em seguida, escolhendo **abrir**.

 Esse modelo de objeto é definido em um conjunto de assemblies que são incluídos no SDK do Visual Studio. Alguns dos principais assemblies neste modelo de objeto incluem *Microsoft. VisualStudio. Shell. 11.0. dll*, *Microsoft. VisualStudio. Shell. Interop. dll*e *Microsoft. VisualStudio. OLE. Interop. dll*.

 Para obter mais informações sobre o modelo de objeto de integração, consulte [visão geral do modelo de automação](../extensibility/internals/automation-model-overview.md) e [referência do SDK do Visual Studio](../extensibility/visual-studio-sdk-reference.md).

### <a name="sharepoint-object-models"></a>Modelos de objeto do SharePoint
 As extensões de ferramentas do SharePoint podem usar as APIs do SharePoint para modificar um site do SharePoint ou para recuperar dados de um site do SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] fornecem dois modelos de objeto diferentes: um modelo de objeto de servidor e um modelo de objeto de cliente.

 Você pode usar APIs em qualquer modelo de objeto em uma extensão de ferramentas do SharePoint, mas cada modelo de objeto tem alguns benefícios e desvantagens no contexto das extensões de ferramentas do SharePoint. Para obter mais informações, consulte [chamar os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

|Modelo de objeto|Descrição|
|------------------|-----------------|
|Modelo de objeto de servidor|O modelo de objeto de servidor fornece acesso a todos os recursos que [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] são expostos programaticamente. Esse modelo de objeto foi projetado para ser usado por soluções do SharePoint que são executadas no servidor do SharePoint. A maior parte desse modelo de objeto é definida no assembly *Microsoft. SharePoint. dll* . Para obter mais informações sobre o modelo de objeto de servidor, consulte [usando o modelo de objeto do SharePoint Foundation Server](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).|
|Modelo de objeto de cliente|O modelo de objeto de cliente é um subconjunto do modelo de objeto de servidor que pode ser usado para interoperar com dados do SharePoint de um cliente ou servidor remoto. Ele foi projetado para minimizar o número de viagens de ida e volta que devem ser executadas para executar tarefas comuns. A maior parte do modelo de objeto de cliente é definida nos assemblies *Microsoft. SharePoint. Client. dll* e *Microsoft. SharePoint. Client. Runtime. dll* . Para obter mais informações sobre o modelo de objeto de cliente, consulte [modelo de objeto de cliente gerenciado](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).|

## <a name="see-also"></a>Consulte também
- [Estenda as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Chamar para os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Usar o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
