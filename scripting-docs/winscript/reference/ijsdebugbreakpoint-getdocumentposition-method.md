---
title: 'Método ijsdebugbreakpoint:: Getdocumentposition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.GetDocumentPosition
apilocation:
- jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d92a58dabe76e391d55996e511409fb63c9d671
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097663"
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>Método IJsDebugBreakPoint::GetDocumentPosition
Retorna a posição da instrução onde o ponto de interrupção foi associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDocumentPosition(  
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
 [Interface IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)