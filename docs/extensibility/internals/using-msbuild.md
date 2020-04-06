---
title: Usando o MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f961249ff584f7767dc2505bb20b1fb0961b7dd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704283"
---
# <a name="using-msbuild"></a>Usando o MSBuild
O MSBuild fornece um formato XML bem definido e extensível para criar arquivos de projeto que descrevem completamente itens de projeto a serem construídos, tarefas de construção e configurações de construção.

## <a name="general-msbuild-considerations"></a>Considerações gerais do MSBuild
 Os arquivos do projeto MSBuild, por [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] exemplo, arquivos .csproj e .vbproj, contêm dados que são usados na hora da compilação, mas também podem conter dados que são usados na hora do projeto. Os dados de tempo de construção são armazenados usando primitivos msbuild, incluindo [Item Element (MSBuild)](../../msbuild/item-element-msbuild.md) e [Property Element (MSBuild)](../../msbuild/property-element-msbuild.md). Os dados de tempo de projeto, que são dados específicos do tipo de projeto e de quaisquer subtipos de projeto relacionados, são armazenados em XML de forma livre reservado para ele.

 O MSBuild não tem suporte nativo para objetos de configuração, mas fornece atributos condicionais para especificar dados específicos da configuração. Por exemplo:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Para obter mais informações sobre atributos condicionais, consulte [Construções Condicionais](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Estendendo o MSBuild para o seu tipo de projeto
 As interfaces e APIs do MSBuild [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]estão sujeitas a alterações nas versões futuras de . Portanto, é prudente usar as classes de quadro de pacotegerenciado (MPF) porque fornecem proteção contra mudanças.

 O MpfProj (Managed Package Framework for Projects) oferece aulas de ajuda para a criação e gerenciamento de novos sistemas de projetos. Você pode encontrar o código fonte e instruções de compilação no [MPF para Projetos - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 As classes do MPF específicas do projeto são as seguintes:

|Classe|Implementação|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`classe é um invólucro para itens MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Geradores de arquivos únicos vs. Tarefas mSBuild
 Geradores de arquivos únicos são acessíveis apenas na hora do projeto, mas as tarefas do MSBuild podem ser usadas em tempo de projeto e tempo de construção. Para máxima flexibilidade, portanto, use tarefas mSBuild para transformar e gerar código. Para obter mais informações, consulte [Ferramentas personalizadas](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Confira também
- [Referência MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Ferramentas personalizadas](../../extensibility/internals/custom-tools.md)
