---
title: IDebugProgram2::Step | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2eec3fd22e41ce7fd49584bb65e2646428646a3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926857"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Executa uma etapa.  
  
> [!NOTE]
>  Este método foi preterido. Use o [etapa](../../../extensibility/debugger/reference/idebugprocess3-step.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pThread`  
 [in] Uma [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread que está sendo passado.  
  
 `sk`  
 [in] Um valor a partir de [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) enumeração que especifica o tipo de etapa.  
  
 `step`  
 [in] Um valor a partir de [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) enumeração que especifica a unidade de etapa (por exemplo, pela instrução ou instrução).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Caso haja qualquer sincronização de thread ou a comunicação entre threads, outros threads no programa devem ser executado quando um determinado thread passo a passo.  
  
> [!WARNING]
>  Não enviar um evento de interrupção ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao manipular essa chamada; caso contrário, o depurador poderá parar de responder.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
