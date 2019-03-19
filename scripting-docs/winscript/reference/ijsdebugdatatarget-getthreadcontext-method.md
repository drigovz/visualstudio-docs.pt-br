---
title: 'Método ijsdebugdatatarget:: Getthreadcontext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7904ef81eb900c6466069267101f30d89e362a1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154680"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>Método IJsDebugDataTarget::GetThreadContext
Recupera o contexto para o thread fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `threadId`  
 [in] Thread em execução no processo de destino.  
  
 `contextFlags`  
 [in] Especifica os sinalizadores de contexto. Isso é o mesmo que o campo ContextFlags de CONTEXT (para obter mais informações, consulte Winnt. h, pesquise por CONTEXT_ALL).  
  
 `contextSize`  
 [in] O tamanho do buffer especificado pelo pContext.  
  
 `pContext`  
 [out] Recebe a estrutura de contexto específicas da plataforma do buffer especificado pelo pContext.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)