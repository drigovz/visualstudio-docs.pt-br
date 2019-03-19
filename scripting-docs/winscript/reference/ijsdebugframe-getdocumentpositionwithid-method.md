---
title: 'Método ijsdebugframe:: Getdocumentpositionwithid | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithId
apilocation:
- jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 741fe323e787c57f5f05a25461eae87c98dba70f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144388"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>Método IJsDebugFrame::GetDocumentPositionWithId
Retorna a posição atual deste quadro de pilha dentro do documento de nível de usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDocumentId`  
 [out] ID exclusiva para um documento de origem (ponteiro para o IDebugDocumentText).  
  
 `pCharacterOffset`  
 [out] O deslocamento de caracteres baseado em zero do início do script.  
  
 `pStatementCharCount`  
 [out] O comprimento da instrução atual, que começa em * pCharacterOffset, em caracteres.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)