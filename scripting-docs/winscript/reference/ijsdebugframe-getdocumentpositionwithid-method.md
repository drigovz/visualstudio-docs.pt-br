---
title: 'Método ijsdebugframe:: Getdocumentpositionwithid | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4c37f31ca6b75ca826dbdab93847a1e70ff054c1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090006"
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