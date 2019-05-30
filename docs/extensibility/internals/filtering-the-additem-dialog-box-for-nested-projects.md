---
title: A caixa de diálogo Adicionar item de filtragem para projetos aninhados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc3ff1f85e8c8c71bf8ef16e6fe0c89bf3613f4d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328957"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrar a caixa de diálogo AddItem para projetos aninhados
Quando você exibe um **AddItem** caixa de diálogo para um projeto aninhado, o projeto pai pode controlar quais itens são exibidos na caixa de diálogo.

 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interface lhe permite filtrar os nós que estarão em um **AddItem** caixa de diálogo. Quando o projeto filho exibe a **AddItem** caixa de diálogo, o pai pode implementar o `IVsFilterAddProjectItemDlg` interface e filtrar itens que seriam exibidos no projeto de seu filho.

 Quando os projetos são agrupados por função em projetos pai específico, você pode implementar `IVsFilterAddProjectItemDlg` quando o usuário seleciona **Adicionar Item de projeto** no menu de atalho em um projeto aninhado. Implementando `IvsFilterAddProjectItemDlg displays` somente projeto itens ou específico a esse grupo de arquivos. Itens de projeto para outros grupos são filtradas fora da caixa de diálogo, mesmo se eles são armazenados no mesmo diretório.

 Quando um usuário abre o **AddItem** filho, a implementação do projeto pai da caixa de diálogo de `IVsFilterAddProjectItemDlg` interface é chamado.

 O `IVsFilterAddProjectItemDlg` interface também pode implementar a filtragem por categoria. Para obter mais informações, consulte [adicionar itens à caixa de diálogo Adicionar Novo Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) e [registrar modelos de projeto e item](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Adicionar itens à caixa de diálogo Adicionar Novo Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrar os modelos de projeto e de item](../../extensibility/internals/registering-project-and-item-templates.md)
- [Projetos de aninhamento](../../extensibility/internals/nesting-projects.md)