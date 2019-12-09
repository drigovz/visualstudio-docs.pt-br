---
title: 'Método IJsDebugDataTarget:: GetThreadContext | Microsoft Docs'
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
ms.openlocfilehash: da5722553b448605129adcf32cfaa52e2dc76352
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577654"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>Método IJsDebugDataTarget::GetThreadContext
Recupera o contexto para determinado thread.  
  
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
 no Thread em execução no processo de destino.  
  
 `contextFlags`  
 no Especifica os sinalizadores de contexto. Isso é o mesmo que o campo ContextFlags do contexto (para obter mais informações, consulte Winnt. h, pesquise por CONTEXT_ALL).  
  
 `contextSize`  
 no O tamanho do buffer especificado por pContext.  
  
 `pContext`  
 fora Recebe a estrutura de contexto específica da plataforma no buffer especificado por pContext.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)