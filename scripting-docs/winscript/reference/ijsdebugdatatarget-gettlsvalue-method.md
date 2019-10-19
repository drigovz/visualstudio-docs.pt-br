---
title: 'Método IJsDebugDataTarget:: GetTlsValue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eecf9acf370656d5310a03d68ed74e10671a0bc2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577601"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>Método IJsDebugDataTarget::GetTlsValue
Para o thread que está sendo depurado, o recupera o valor no slot de armazenamento local do thread (TLS) para o índice TLS especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `threadId`  
 no Thread em execução no processo de destino para ler.  
  
 `tlsIndex`  
 no O índice TLS que foi alocado quando o processo de destino chamou a função TlsAlloc.  
  
 `pValue`  
 fora O valor do tamanho do ponteiro que foi armazenado no slot TLS do thread. Se o thread-alvo for de 32 bits, os 32 superiores desse valor serão zero.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="remarks"></a>Comentários  
 Cada thread de um processo tem seu próprio slot para cada índice TLS.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)