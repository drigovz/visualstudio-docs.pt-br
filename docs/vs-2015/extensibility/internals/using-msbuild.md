---
title: Usando o MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a1ad59e6d8f4cb88004629b0dfd2cdf0631a7824
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297668"
---
# <a name="using-msbuild"></a>Usando o MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O MSBuild fornece um formato XML extensível e bem definido para a criação de arquivos de projeto que descrevem totalmente os itens de projeto a serem criados, as tarefas de compilação e as configurações de compilação.  
  
 Para obter um exemplo de ponta a ponta de um sistema de projeto de linguagem baseado no MSBuild, consulte a amostra aprofundada do IronPython nos[exemplos de VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="general-msbuild-considerations"></a>Considerações gerais do MSBuild  
 Os arquivos de projeto do MSBuild, por exemplo, [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. csproj e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] arquivos. vbproj, contêm dados que são usados no momento da compilação, mas também podem conter dados que são usados em tempo de design. Os dados de tempo de compilação são armazenados usando primitivos do MSBuild, incluindo o [elemento de item (MSBuild)](../../msbuild/item-element-msbuild.md) e o [elemento de propriedade (MSBuild)](../../msbuild/property-element-msbuild.md). Os dados de tempo de design, que são dados específicos para o tipo de projeto e todos os subtipos de projeto relacionados, são armazenados em XML de forma livre reservado para ele.  
  
 O MSBuild não tem suporte nativo para objetos de configuração, mas fornece atributos condicionais para especificar dados específicos da configuração. Por exemplo:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Para obter mais informações sobre atributos condicionais, consulte [constructos condicionais](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Estendendo o MSBuild para o tipo de projeto  
 As interfaces e APIs do MSBuild estão sujeitas a alterações em versões futuras do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Portanto, é prudente usar as classes do MPF (estrutura de pacote gerenciada) porque elas fornecem a blindagem de alterações.  
  
 A estrutura de pacote gerenciada para projetos (MPFProj) fornece classes auxiliares para criar e gerenciar o novo sistema de projeto. Você pode encontrar o código-fonte e as instruções de compilação em [MPF for projects-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
 As classes do MPF específicas do projeto são as seguintes:  
  
|Classe|Implementação|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` classe é um wrapper para itens do MSBuild.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Geradores de arquivo único versus tarefas do MSBuild  
 Os geradores de arquivo único são acessíveis em tempo de design apenas, mas as tarefas do MSBuild podem ser usadas em tempo de design e em tempo de compilação. Para obter máxima flexibilidade, portanto, use tarefas do MSBuild para transformar e gerar código. Para obter mais informações, consulte [ferramentas personalizadas](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>Consulte também  
 [Referência do MSBuild](../../msbuild/msbuild-reference.md)   
 [MSBuild](https://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [Ferramentas personalizadas](../../extensibility/internals/custom-tools.md)
