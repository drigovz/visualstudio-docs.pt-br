---
title: Adicionando diretórios à caixa de diálogo Adicionar novo item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f370d208cb8f7aad88f806983983ccee9f584625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203923"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Adicionando diretórios à caixa de diálogo Adicionar Novo Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O exemplo de código a seguir demonstra como registrar um novo conjunto de diretórios para a caixa de diálogo **Adicionar novo item** . Os diretórios para a caixa de diálogo **Adicionar novo item** são diferentes para cada projeto. Portanto, os diretórios são registrados na subchave projetos, encontrados em \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects> :  
  
## <a name="the-registry-script"></a>O script de registro  
  
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
  
 O valor de Template_Path especifica o caminho completo do diretório que contém os modelos de projeto. Esses modelos podem ser arquivos. vsz ou arquivos de modelo de protótipos para serem clonados.  
  
 O valor SortPriority especifica uma prioridade de classificação.  
  
## <a name="adding-items-to-an-existing-project"></a>Adicionando itens a um projeto existente  
 Você também pode adicionar itens a um projeto existente. Por exemplo, para um [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projeto, você pode adicionar itens à \<root> pasta \Program Files\Microsoft Visual Studio \VC # \CSharpProjectItems\LocalProjectItems. Nesse caso, o `%GUID_Project%` é o GUID de um projeto C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Você também pode estender um projeto existente programando um subtipo de projeto. Com um subtipo de projeto, você pode estender um projeto sem gravar um novo tipo de projeto. Para obter mais informações sobre subtipos de projeto, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Registrando modelos de projeto e item](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Adicionando itens às caixas de diálogo Adicionar novo item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Adicionar diretórios à caixa de diálogo Novo Projeto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
