---
title: Adicionando diretórios à caixa de diálogo Adicionar novo item | Microsoft Docs
description: Saiba como adicionar diretórios à caixa de diálogo Adicionar novo item no Visual Studio usando um script de registro para registrar os diretórios.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 68a16d544147ca95512f8b6064d2b9712b26ed64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969016"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Adicionar diretórios à caixa de diálogo Adicionar novo item
O exemplo de código a seguir demonstra como registrar um novo conjunto de diretórios para a caixa de diálogo **Adicionar novo item** . Os diretórios para a caixa de diálogo **Adicionar novo item** são diferentes para cada projeto. Portanto, os diretórios são registrados na subchave **projetos** , encontrados em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

## <a name="registry-script"></a>Script de registro

```
NoRemove Projects
{
  NoRemove %GUID_Project%
  {
    NoRemove AddItemTemplates
    {
      NoRemove TemplateDirs
      {
        ForceRemove %CLSID_Package%
        {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
          {
            val TemplatesDir = s '%Template_Path%'
            val SortPriority = d 2000
          }
        }
      }
    }
  }
}
```

 O `%Template_Path%` valor especifica o caminho completo do diretório que contém os modelos de projeto. Esses modelos podem ser arquivos *. vsz* ou arquivos de modelo de protótipos para serem clonados.

 O `SortPriority` valor especifica uma prioridade de classificação.

## <a name="add-items-to-an-existing-project"></a>Adicionar itens a um projeto existente
 Você também pode adicionar itens a um projeto existente. Por exemplo, para um [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projeto, você pode adicionar itens à pasta *\<root> \Program Files\Microsoft Visual Studio\VC # \CSharpProjectItems\LocalProjectItems* . Nesse caso, `%GUID_Project%` é o GUID de um projeto C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Você também pode estender um projeto existente programando um subtipo de projeto. Com um subtipo de projeto, você pode estender um projeto sem gravar um novo tipo de projeto. Para obter mais informações sobre subtipos de projeto, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Consulte também
- [Registrar modelos de projeto e item](../../extensibility/internals/registering-project-and-item-templates.md)
- [Adicionar itens à caixa de diálogo Adicionar novo item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Adicionar diretórios à caixa de diálogo novo projeto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
