---
title: IDebugThread2::GetLogicalThread | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f430ea7ba69ca55bc76543d853396e22b193cf02
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58921839"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Mecanismos de depuração não implementam este método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStackFrame`  
 [in] Uma [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) objeto que representa o quadro de pilhas.  
  
 `ppLogicalThread`  
 [out] Retorna um `IDebugLogicalThread2` interface que representa o thread lógico associado. Uma implementação do mecanismo de depuração deve definir isso como um valor nulo.  
  
## <a name="return-value"></a>Valor de retorno  
 Depurar as implementações de mecanismo sempre retornam `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
