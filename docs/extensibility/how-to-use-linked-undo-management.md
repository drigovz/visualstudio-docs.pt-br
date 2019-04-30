---
title: 'Como: Use o gerenciamento de desfazer vinculado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f11ea8e93d7d952f28315481f65149122a7b68a3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63415581"
---
# <a name="how-to-use-linked-undo-management"></a>Como: Use o gerenciamento de desfazer vinculado
Desfazer vinculado permite que o usuário simultaneamente, desfazer as mesmas edições em vários arquivos. Por exemplo, as alterações de texto simultâneas em vários arquivos de programa, como um arquivo de cabeçalho e um arquivo do Visual C++, é uma transação de desfazer vinculado. Capacidade de desfazer vinculado está incorporada a implementação do ambiente do Gerenciador de desfazer, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> permite manipular esse recurso. Desfazer vinculado é implementado por uma unidade de desfazer pai que pode vincular as pilhas de desfazer separado juntos para ser tratado como uma unidade de desfazer. O procedimento para usar um Desfazer vinculado é detalhado na seção a seguir.

## <a name="to-use-linked-undo"></a>Para usar um Desfazer vinculado

1. Chame `QueryService` na `SVsLinkedUndoManager` para obter um ponteiro para `IVsLinkedUndoTransactionManager`.

2. Criar a unidade de desfazer vinculado pai inicial chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Isso define o ponto de partida para um conjunto de pilhas de desfazer a ser agrupada em pilhas de desfazer vinculado. No `OpenLinkedUndo` método, você também precisará especificar se deseja que o desfazer vinculado ser estrito ou não restrito. Comportamento de desfazer vinculado não estrito significa que alguns dos documentos com irmãos de desfazer vinculado podem fechar e ainda, deixe o outro vinculado desfazer irmãos em suas pilhas. Comportamento estrito desfazer vinculado Especifica que todas as pilhas de irmão desfazer vinculado precisam ser desfeita juntos ou nenhum. Adicionar subsequentes vinculado pilhas de desfazer, chamando [IOleUndoManager::Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) método.

3. Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> reverter todas as unidades de desfazer vinculado como um.

    > [!NOTE]
    > Para implementar o gerenciamento de desfazer vinculado em um editor, adicione o gerenciamento de desfazer. Para obter mais informações sobre como implementar o gerenciamento de desfazer vinculado, consulte [como: Implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md).

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>
- [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)
- [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)
- [Como: Implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md)