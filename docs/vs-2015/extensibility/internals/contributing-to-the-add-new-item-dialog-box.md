---
title: Contribuindo para a caixa de diálogo Adicionar novo item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d288f2d007fd0f923021847179326069959d3698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197018"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Contribuindo com a caixa de diálogo Adicionar Novo Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um subtipo de projeto pode fornecer um novo diretório completo de itens para a caixa de diálogo **Adicionar novo item** , registrando adicionar modelos de **Item** na `Projects` subchave do registro.  
  
## <a name="registering-add-new-item-templates"></a>Registrando adicionar novos modelos de item  
 Esta seção está localizada em **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0\Projects** no registro. As entradas de registro abaixo pressupõem um [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projeto agregado por um subtipo de projeto hipotético. As entradas para o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projeto estão listadas abaixo.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 A `AddItemTemplates\TemplateDirs` subchave contém entradas de registro com o caminho para o diretório em que os itens disponibilizados na caixa de diálogo **Adicionar novo item** são colocados.  
  
 O ambiente carrega automaticamente todos os `AddItemTemplates` dados na `Projects` subchave do registro. Isso pode incluir os dados para implementações de projeto base, bem como os dados para tipos de subtipo de projeto específicos. Cada subtipo de projeto é identificado por um tipo de projeto `GUID` . O subtipo de projeto pode especificar que um conjunto alternativo de `Add Item` modelos deve ser usado para uma instância de projeto determinada, dando suporte à `VSHPROPID_ AddItemTemplatesGuid` enumeração de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> em <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementação para retornar o valor de GUID do subtipo do projeto. Se `VSHPROPID_AddItemTemplatesGuid` a propriedade não for especificada, o GUID do projeto base será usado.  
  
 Você pode filtrar itens na caixa de diálogo **Adicionar novo item** implementando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interface no objeto agregador de subtipo do projeto. Por exemplo, um subtipo de projeto que implementa um projeto de banco de dados agregando um [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projeto, pode filtrar os [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] itens específicos da caixa de diálogo **Adicionar novo item** implementando a filtragem e, por sua vez, pode adicionar itens específicos do projeto de banco de dados ao dar suporte ao `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Para obter mais informações sobre como filtrar e adicionar itens à caixa de diálogo **Adicionar novo item** , consulte [adicionando itens às caixas de diálogo Adicionar novo item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATIDs para objetos que normalmente são usados para estender projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
