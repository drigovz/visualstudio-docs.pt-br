---
title: Contribuindo para a caixa de diálogo de adicionar novos itens | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83444d9be6ba23392b792a0187bf46dc9920c465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709285"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Contribua para a caixa de diálogo Adicionar novo item
Um subtipo de projeto pode fornecer um novo diretório completo de itens para a caixa de diálogo **Adicionar novo item,** registrando modelos de **adicionar itens** sob a sub-chave de registro **de projetos.**

## <a name="register-add-new-item-templates"></a>Registre adicionar modelos de novos itens
 Esta seção está localizada sob **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projetos** no registro. As entradas de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registro abaixo assumem um projeto agregado por um subtipo hipotético do projeto. As inscrições para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o projeto estão listadas abaixo.

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

 A **subchave AddItemTemplates\TemplateDirs** contém entradas de registro com o caminho para o diretório onde os itens disponibilizados na caixa de diálogo **Adicionar novo item** são colocados.

 O ambiente carrega automaticamente todos os dados **AddItemTemplates** sob a sub-chave de registro **de projetos.** Esses dados podem incluir os dados para implementações de projetos básicos, bem como os dados para tipos específicos de subtipos de projeto. Cada subtipo de projeto é identificado por um tipo de projeto **GUID**. O subtipo do projeto pode **Add Item** especificar que um conjunto alternativo de modelos de `VSHPROPID_ AddItemTemplatesGuid` itens adicionais <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> deve ser usado para uma instância de projeto com sabor específico, apoiando a enumeração da implementação para retornar o valor GUID do subtipo do projeto. Se `VSHPROPID_AddItemTemplatesGuid` a propriedade não for especificada, o GUID do projeto base será usado.

 Você pode filtrar itens na caixa de diálogo Adicionar <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> novo **item** implementando a interface no objeto agregador do subtipo do projeto. Por exemplo, um subtipo de projeto que implementa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um projeto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] banco de dados agregando um projeto, pode filtrar os itens específicos da caixa de `VSHPROPID_ AddItemTemplatesGuid` diálogo <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>Adicionar **novo item** implementando a filtragem e, por sua vez, pode adicionar itens específicos do projeto de banco de dados, suportando em . Para obter mais informações sobre filtrar e adicionar itens à caixa de diálogo **Adicionar novo item,** consulte [Adicionar itens à caixa de diálogo Adicionar novo item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATIDs para objetos que normalmente são usados para estender projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
