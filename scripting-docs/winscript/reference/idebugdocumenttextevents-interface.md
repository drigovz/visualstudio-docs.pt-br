---
title: Interface IDebugDocumentTextEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c83a6e3a41ed7087338989d5cb077fa070e724b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434258"
---
# <a name="idebugdocumenttextevents-interface"></a>Interface IDebugDocumentTextEvents
Fornece eventos que indicam alterações no documento de texto associado.  
  
> [!NOTE]
> O texto do documento muda quando os eventos nessa interface incêndio. Manipuladores de eventos podem recuperar o novo texto usando o `IDebugDocumentText` interface.  
  
 Além dos métodos herdados de `IUnknown`, o `IDebugDocumentTextEvents` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Indica que o documento subjacente foi destruído e não é mais válido|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Indica que o novo texto foi adicionado ao documento|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Indica que o texto foi removido do documento.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Indica que o texto foi substituído.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Indica que os atributos de texto associados ao intervalo de posição de caractere subjacente foram alterados.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Indica que os atributos do documento é alterado.|