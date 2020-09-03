---
title: Filtrando a caixa de diálogo AddItem para projetos aninhados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bc97b6041f4844ff71fe1d38a7103e1219888be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708381"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrar a caixa de diálogo AddItem para projetos aninhados
Quando você exibe uma caixa de diálogo **AddItem** para um projeto aninhado, o projeto pai pode controlar quais itens são exibidos na caixa de diálogo.

 A <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interface permite filtrar os nós que estarão em uma caixa de diálogo **AddItem** . Quando o projeto filho exibe a caixa de diálogo **AddItem** , o pai pode implementar a `IVsFilterAddProjectItemDlg` interface e filtrar itens que, de outra forma, seriam exibidos no projeto do filho.

 Quando os projetos são agrupados por função em projetos pai específicos, você pode implementar `IVsFilterAddProjectItemDlg` quando o usuário seleciona **Adicionar item de projeto** no menu de atalho em um projeto aninhado. Implementar `IvsFilterAddProjectItemDlg displays` somente itens de projeto ou arquivos específicos para esse grupo. Os itens de projeto para outros grupos são filtrados fora da caixa de diálogo, mesmo se estiverem armazenados no mesmo diretório.

 Quando um usuário abre a caixa de diálogo **AddItem** para o filho, a implementação do projeto pai da `IVsFilterAddProjectItemDlg` interface é chamada.

 A `IVsFilterAddProjectItemDlg` interface também pode implementar a filtragem por categoria. Para obter mais informações, consulte [Adicionar itens à caixa de diálogo Adicionar novo item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) e [registrar modelos de projeto e item](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Adicionar itens à caixa de diálogo Adicionar novo item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrar modelos de projeto e item](../../extensibility/internals/registering-project-and-item-templates.md)
- [Aninhar projetos](../../extensibility/internals/nesting-projects.md)
