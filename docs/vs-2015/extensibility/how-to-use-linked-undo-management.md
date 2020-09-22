---
title: 'Como: usar o gerenciamento de desfazer vinculado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67d0d173909b8cdfe2eaf0d56aa5c99c437d5ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838388"
---
# <a name="how-to-use-linked-undo-management"></a>Como usar o gerenciamento de desfazer vinculado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O recurso desfazer vinculado permite ao usuário desfazer simultaneamente as mesmas edições em vários arquivos. Por exemplo, alterações de texto simultâneas em vários arquivos de programas, como um arquivo de cabeçalho e um arquivo de Visual C++, são uma transação de desfazer vinculada. A funcionalidade de desfazer vinculada é incorporada à implementação do ambiente do Gerenciador de desfazer e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> permite que você manipule esse recurso. O desfazer vinculado é implementado por uma unidade de desfazer pai que pode vincular pilhas de desfazer separadas para ser tratada como uma única unidade de desfazer. O procedimento para usar desfazer vinculados é detalhado na seção a seguir.  
  
### <a name="to-use-linked-undo"></a>Para usar desfazer vinculado  
  
1. Ligue `QueryService` `SVsLinkedUndoManager` para para obter um ponteiro para `IVsLinkedUndoTransactionManager` .  
  
2. Crie a unidade de desfazer vinculada pai inicial chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> . Isso define o ponto de partida para um conjunto de pilhas de desfazer a ser agrupado em pilhas de desfazer vinculadas. No `OpenLinkedUndo` método, você também precisará especificar se deseja que o desfazer vinculado seja estrito ou não estrito. O comportamento de desfazer vinculado não estrito significa que alguns dos documentos com irmãos de desfazer vinculados podem fechar e ainda deixar os outros irmãos de desfazer vinculados em suas pilhas. Comportamento de desfazer vinculado estrito Especifica que todas as pilhas irmãs de desfazer vinculadas precisam ser desfeitas juntas ou não. Adicione as pilhas de desfazer vinculadas subsequentes chamando o método [IOleUndoManager:: Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) .  
  
3. Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> para reverter todas as unidades de desfazer vinculadas como uma.  
  
    > [!NOTE]
    > Para implementar o gerenciamento de desfazer vinculado em um editor, adicione o gerenciamento de desfazer. Para obter mais informações sobre como implementar o gerenciamento de desfazer vinculado, consulte [como implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Como implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md)
