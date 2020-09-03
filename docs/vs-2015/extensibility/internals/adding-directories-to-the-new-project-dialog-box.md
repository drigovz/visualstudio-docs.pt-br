---
title: Adicionando diretórios à caixa de diálogo novo projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8a9eeca4dc455c4f16e3551541454483138a993
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203870"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Adicionar diretórios à caixa de diálogo Novo Projeto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ao criar novos tipos de projeto, você também pode registrar um novo diretório na caixa de diálogo **novo projeto** para exibi-los para uso como modelos. O exemplo de código a seguir explica como registrar um novo diretório, também conhecido como um nó. No exemplo, os modelos expostos por VSPackage CLSID_Package são registrados. Como resultado, o lado esquerdo da caixa de diálogo **novo projeto** oferece o nó adicionado, com um nome determinado pelo recurso de Folder_Label_ResID. Esse recurso é carregado da DLL satélite do VSPackage.  
  
 O valor da **pasta** representa um GUID de uma pasta sob a qual o nó de Folder_Label_ResID é exibido. No exemplo, o GUID representa a pasta **outros projetos** no painel **tipos de projeto** da caixa de diálogo **novo projeto** . Se o valor de **outros projetos** estiver ausente, o rótulo será posicionado no nível superior.  
  
 O valor TemplatesDir especifica o caminho completo do diretório que contém os modelos de projeto. Esses arquivos podem ser arquivos. vsz ou arquivos de modelo típicos a serem clonados.  
  
 Se você especificar TemplatesLocalizedSubDir, ela deverá ser a ID de recurso de uma cadeia de caracteres que nomeia o subdiretório de TemplatesDir que contém modelos localizados. Como [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o carrega o recurso de cadeia de caracteres de uma DLL satélite, se você tiver um, cada DLL satélite poderá conter um nome de subdiretório diferente. O valor SortPriority especifica uma prioridade de classificação.  
  
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
  
## <a name="see-also"></a>Consulte Também  
 [Registrando modelos de projeto e item](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Adicionando itens às caixas de diálogo Adicionar novo item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Adicionando diretórios à caixa de diálogo Adicionar Novo Item](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
