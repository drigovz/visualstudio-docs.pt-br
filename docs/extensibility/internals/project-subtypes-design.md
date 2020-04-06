---
title: Projeto Subtipos Design | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b939d197bfd7e58b555ca7698f08643e3d38ef2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706442"
---
# <a name="project-subtypes-design"></a>Design de subtipos de projeto

Os subtipos do projeto permitem que os VSPackages ampliem projetos baseados no Microsoft Build Engine (MSBuild). O uso da agregação permite que você reutilize a maior [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] parte do sistema de projeto gerenciado do núcleo implementado ainda em personalizar o comportamento para um cenário específico.

 Os seguintes tópicos detalham o projeto básico e a implementação dos subtipos do projeto:

- Projeto Subtipo Design.

- Agregação multinível.

- Interfaces de suporte.

## <a name="project-subtype-design"></a>Projeto de subtipo

A inicialização de um subtipo de projeto é <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> alcançada agregando os principais e objetos. Essa agregação permite que um subtipo de projeto anule ou melhore a maioria das capacidades do projeto base. Os subtipos do projeto têm <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>a primeira <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> chance <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>de lidar com <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>propriedades usando, comandos usando e , e gerenciamento de itens de projeto usando . Os subtipos do projeto também podem se estender:

- Objetos de configuração do projeto.

- Objetos dependentes da configuração.

- Objetos de navegação independentes de configuração.

- Objetos de automação de projetos.

- Coleções de propriedades de automação de projetos.

Para obter mais informações sobre extensibilidade por subtipos de projeto, consulte [Propriedades e Métodos Estendidos por Subtipos de Projeto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>Arquivos de Política

O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente fornece um exemplo de extensão do sistema de projeto base com um subtipo de projeto em sua implementação de arquivos de políticas. Um arquivo de diretiva permite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a modelagem do ambiente gerenciando recursos que incluem o Solution Explorer, **Add Project** caixa de diálogo, adicionar caixa de diálogo **De novo item** e a caixa de diálogo **Propriedades.** O subtipo de política substitui e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` aprimora esses recursos através de implementações e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementações.

### <a name="aggregation-mechanism"></a>Mecanismo de agregação

O mecanismo de agregação do subtipo de projeto do ambiente suporta vários níveis de agregação, permitindo assim que um subtipo avançado seja implementado aromatizar ainda mais um projeto com sabor. Além disso, os objetos de suporte <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>de um subtipo de projeto, tais como , são projetados para permitir vários níveis de camadas. De acordo com as restrições das regras de agregação COM e COM, subtipos de projetos e projetos básicos de projeto precisam ser programados cooperativamente para permitir que o subtipo interno ou o projeto base participem adequadamente na delegar chamadas de métodos e gerenciar contagens de referência. Ou seja, o projeto prestes a ser agregado tem que ser programado para apoiar a agregação.

A ilustração a seguir mostra uma representação esquemática de uma agregação de subtipo de projeto de vários níveis.

![Gráfico de projectflavor de vários níveis do Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Uma agregação de subtipo de projeto multinível consiste em três níveis, um projeto base, que é agregado por um subtipo de projeto, então ainda mais agregado por um subtipo de projeto avançado. A figura se concentra em algumas das interfaces de suporte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que são fornecidas como parte da arquitetura do subtipo do projeto.

### <a name="deployment-mechanisms"></a>Mecanismos de implantação

Entre muitas das funcionalidades do sistema de projeto base aprimoradas por um subtipo de projeto estão mecanismos de implantação. Um subtipo de projeto influencia os mecanismos <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>implantação implementando interfaces de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>configuração (como e ) que são recuperadas chamando QueryInterface em . Em um cenário onde tanto o subtipo do projeto quanto o subtipo `QueryInterface` avançado do projeto adicionam diferentes implementações de configuração, o projeto base solicita o subtipo de `IUnknown`projeto avançado . Se o subtipo interno do projeto contiver a implementação de configuração que o projeto base está pedindo, o subtipo avançado do projeto será substituído pela implementação fornecida pelo subtipo interno do projeto. Como um mecanismo para persistir de um nível de agregação para <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> outro, todos os níveis de subtipos de projeto implementam para persistir dados XML relacionados à não-construção nos arquivos do projeto. Para obter mais informações, consulte [Dados persistentes no arquivo do projeto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>é implementado como um mecanismo para recuperar extensores de automação dos subtipos do projeto.

A ilustração a seguir se concentra na implementação do extensor de automação, o objeto de navegação de configuração do projeto em particular, usado por subtipos de projeto para estender o sistema de projeto base.

![VS Project Flavor Auto Extender gráfico](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Os subtipos do projeto podem estender ainda mais o sistema de projeto base, ampliando o modelo de objeto de automação. Estes são definidos como parte do objeto de automação DTE `ProjectItem` e `Configuration` são usados para estender o objeto Project, o objeto e o objeto. Para obter mais informações, [consulte, estendendo o modelo de objeto do projeto base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Agregação multinível

Uma implementação de subtipo de projeto que envolva um subtipo de projeto de nível inferior precisa ser programada cooperativamente para permitir que o subtipo interno do projeto funcione corretamente. Uma lista de responsabilidades de programação inclui:

- A <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementação do subtipo do projeto que está <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> envolvendo o subtipo interno <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> deve delegar a implementação do subtipo interno do projeto para ambos e métodos.

- A <xref:EnvDTE80.IInternalExtenderProvider> implementação do subtipo do projeto de invólucro deve delegar ao de seu subtipo de projeto interno. Em particular, a <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> implementação de necessidades para obter a seqüência de nomes do subtipo interno do projeto e, em seguida, concatenar as strings que deseja adicionar como extensores.

- A <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> implementação de um subtipo de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> projeto de invólucro deve instanciar o objeto de seu subtipo interno do projeto e mantê-lo como um delegado privado, uma vez que apenas o objeto de configuração do projeto base sabe diretamente que o objeto de configuração do subtipo do projeto de invólucro existe. O subtipo externo do projeto pode inicialmente escolher interfaces de configuração que deseja lidar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>diretamente e, em seguida, delegar o resto para a implementação do subtipo de projeto interno de .

## <a name="supporting-interfaces"></a>Interfaces de suporte

O projeto base delega chamadas para o suporte de interfaces adicionadas por um subtipo de projeto, para estender vários aspectos de sua implementação. Isso inclui estender objetos de configuração de projeto e vários objetos de navegador de propriedade. Essas interfaces são recuperadas chamando `QueryInterface` `punkOuter` (um ponteiro para o `IUnknown`) do agregador de subtipo de projeto externo.

|Interface|Subtipo do projeto|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Permite que o subtipo do projeto:<br /><br /> - Fornecer uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>implementação de .<br />- Controlar o lançamento do depurador permitindo que o subtipo do projeto forneça sua própria implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />- Desativar a avaliação de expressão de `DBGLAUNCH_DesignTimeExprEval` tempo de projeto, manipulando adequadamente o caso na sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|
|<xref:EnvDTE80.IInternalExtenderProvider>|Permite que o subtipo do projeto:<br /><br /> - Estender <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> o do projeto para adicionar ou remover propriedades independentes de configuração do projeto.<br />- Estender o objeto<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>de automação do projeto ( ) do projeto.<br /><br /> Os valores de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> propriedade acima são retirados da enumeração.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permite que o subtipo do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> projeto mapeie de volta para o objeto dada a configuração do projeto procurar objeto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permite que o subtipo do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projeto `VSITEMID` mapeie de volta para o objeto ou para o objeto, dada a configuração do projeto procurar objeto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permite que o subtipo do projeto persista dados estruturados de XML arbitrários para o arquivo do projeto (.vbproj ou .csproj). Esses dados não são visíveis para o MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Permite que o subtipo do projeto:<br /><br /> - Adicionar novas propriedades MSBuild a serem persistidas.<br />- Remova propriedades desnecessárias do MSBuild.<br />- Consulta a um valor atual de uma propriedade MSBuild.<br />- Alterar o valor atual de uma propriedade MSBuild.|

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
