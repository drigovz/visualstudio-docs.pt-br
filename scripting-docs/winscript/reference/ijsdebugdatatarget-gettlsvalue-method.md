---
title: 'Método ijsdebugdatatarget:: Gettlsvalue | Microsoft Docs'
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
ms.openlocfilehash: 458aaab05f274983fdaf69c6e702502974665403
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157097"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>Método IJsDebugDataTarget::GetTlsValue
Para o thread que está sendo depurado, recupera o valor no slot de armazenamento local (TLS) de thread para o índice TLS especificado.  
  
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
 [in] Em execução no processo de destino para ler a partir do thread.  
  
 `tlsIndex`  
 [in] O índice TLS que foi atribuído quando o processo de destino chamou a função TlsAlloc.  
  
 `pValue`  
 [out] O valor do ponteiro dimensionado que foi armazenado no encaixe de TLS do thread. Se o thread de destino for de 32 bits, 32-bits superiores desse valor será zero.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Cada thread de um processo tem seu próprio slot para cada índice TLS.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)