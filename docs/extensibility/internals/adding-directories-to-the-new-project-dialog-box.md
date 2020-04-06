---
title: Adicionando diretórios à caixa de diálogo do novo projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 827e383bba13c9742deb654bf3d680adeb3c109b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710241"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Adicionar diretórios à caixa de diálogo Do Novo Projeto
Ao criar novos tipos de projeto, você também pode registrar um novo diretório na caixa de diálogo **Projeto Novo** para exibi-los para uso como modelos. O exemplo de código a seguir explica como registrar um novo diretório, também conhecido como nó. No exemplo, modelos expostos pelo VSPackage, *CLSID_Package*, são registrados. Como resultado, o lado esquerdo da caixa de diálogo **Novo Projeto** oferece o nó adicionado, com um nome determinado pelo recurso *Folder_Label_ResID.* Este recurso é carregado a partir do satélite VSPackage DLL.

 O valor **da pasta** representa um GUID de uma pasta sob a qual o *nó Folder_Label_ResID* é exibido. No exemplo, o GUID representa a pasta **Outros Projetos** no painel **Tipos** de projeto da caixa de diálogo **Novo Projeto.** Se o valor **de Outros Projetos** estiver ausente, o rótulo será posicionado no nível superior.

 O `TemplatesDir` valor especifica o caminho completo do diretório que contém os modelos do projeto. Esses arquivos podem ser arquivos *.vsz* ou arquivos de modelo típicos a serem clonados.

 Se você `TemplatesLocalizedSubDir`especificar, deve ser o ID de recurso `TemplatesDir` de uma string que nomeia o subdiretório do que contém modelos localizados. Como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carrega o recurso de string de um DLL de satélite se você tiver um, cada DLL de satélite pode conter um nome de subdiretório diferente. O `SortPriority` valor especifica uma prioridade de classificação.

```
NoRemove NewProjectTemplates
{
    NoRemove TemplateDirs
  {
    ForceRemove %CLSID_Package%
    {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
      {
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'
        val TemplatesDir = s '%Template_Path%'
        val TemplatesLocalizedSubDir = s '#100'
        val SortPriority = d 1000
      }
    }
  }
}
```

## <a name="see-also"></a>Confira também
- [Registre modelos de projetos e itens](../../extensibility/internals/registering-project-and-item-templates.md)
- [Adicionar itens à caixa de diálogo Adicionar novo item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Adicionar diretórios à caixa de diálogo Adicionar novo item](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
