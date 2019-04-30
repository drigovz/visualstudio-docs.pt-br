---
title: IDebugProcess3::Step | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 296c76a386b72c3435a90e207dd76f9eeca56422
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412949"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Faz com que o processo para a etapa de uma instrução ou instrução.

> [!NOTE]
> Esse método deve ser usado em vez de [etapa](../../../extensibility/debugger/reference/idebugprogram2-step.md).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

#### <a name="parameters"></a>Parâmetros
 `pThread`

 [in] Uma [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread que está sendo passado.

 `sk`

 [in] Um dos [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) valores.

 `step`

 [in] Um dos [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) valores.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna o código de erro.

## <a name="remarks"></a>Comentários
 Caso haja qualquer sincronização de thread ou a comunicação entre threads, outros threads no processo devem ser executado quando um determinado thread passo a passo.

 **Aviso** envia um evento de interrupção ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao manipular essa chamada; caso contrário, o depurador poderá parar de responder.

## <a name="see-also"></a>Consulte também
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)