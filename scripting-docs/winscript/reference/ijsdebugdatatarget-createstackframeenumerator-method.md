---
title: 'Método IJsDebugDataTarget:: CreateStackFrameEnumerator | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.CreateStackFrameEnumerator
apilocation:
- jscript9diag.dll
ms.assetid: cda172e5-18d0-43c5-81d8-432ab30ee70d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 59d58f0256a326d3922e280818176a43ef4aa5ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577624"
---
# <a name="ijsdebugdatatargetcreatestackframeenumerator-method"></a>Método IJsDebugDataTarget::CreateStackFrameEnumerator
Cria um enumerador para os quadros de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateStackFrameEnumerator(  
   DWORD threadId,  
   IEnumJsStackFrames **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `threadId`  
 no Thread em execução no processo de destino.  
  
 `ppEnumerator`  
 fora O enumerador para os quadros de ativação.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)