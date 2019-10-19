---
title: 'Método IJsDebugFrame:: GetDocumentPositionWithId | Microsoft Docs'
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
ms.openlocfilehash: f35f6fb84db95950fe83d571c9f5e5e7db9de1e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573855"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>Método IJsDebugFrame::GetDocumentPositionWithId
Retorna a posição atual deste quadro de pilhas no documento de nível de usuário.  
  
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
 fora ID exclusiva de um documento de origem (ponteiro para o IDebugDocumentText).  
  
 `pCharacterOffset`  
 fora O deslocamento de caractere baseado em zero a partir do início do script.  
  
 `pStatementCharCount`  
 fora O comprimento da instrução atual, que começa em * pCharacterOffset, em caracteres.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)