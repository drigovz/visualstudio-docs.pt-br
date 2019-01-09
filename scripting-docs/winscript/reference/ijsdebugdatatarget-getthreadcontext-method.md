---
title: 'Método ijsdebugdatatarget:: Getthreadcontext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 50e2bdb7b8720549aac5e5b3c4cebffc4b7ae892
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090051"
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