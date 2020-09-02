---
title: Filtrando a caixa de diálogo AddItem para projetos aninhados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7bb98eac2bc481aa5e3652144dfbcadf70430d04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538090"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Filtrando a caixa de diálogo AddItem para projetos aninhados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando você exibe uma caixa de diálogo **AddItem** para um projeto aninhado, o projeto pai pode controlar quais itens são exibidos na caixa de diálogo.  
  
 A <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interface permite filtrar os nós que estarão em uma caixa de diálogo **AddItem** . Quando o projeto filho exibe a caixa de diálogo **AddItem** , o pai pode implementar a `IVsFilterAddProjectItemDlg` interface e filtrar itens que, de outra forma, seriam exibidos no projeto do filho.  
  
 Quando os projetos são agrupados por função em projetos pai específicos, você pode implementar `IVsFilterAddProjectItemDlg` quando o usuário seleciona **Adicionar item de projeto** no menu de atalho em um projeto aninhado. Implementar `IvsFilterAddProjectItemDlg displays` somente itens de projeto ou arquivos específicos para esse grupo. Os itens de projeto para outros grupos são filtrados fora da caixa de diálogo, mesmo se estiverem armazenados no mesmo diretório.  
  
 Quando um usuário abre a caixa de diálogo **AddItem** para o filho, a implementação do projeto pai da `IVsFilterAddProjectItemDlg` interface é chamada.  
  
 A `IVsFilterAddProjectItemDlg` interface também pode implementar a filtragem por categoria. Para obter mais informações, consulte [adicionando itens às caixas de diálogo Adicionar novo item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) e [registrando modelos de projeto e item](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Adicionando itens às caixas de diálogo Adicionar novo item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrando modelos de projeto e item](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Aninhando projetos](../../extensibility/internals/nesting-projects.md)
