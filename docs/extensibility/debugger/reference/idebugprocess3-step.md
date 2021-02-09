---
title: 'IDebugProcess3:: Step | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69f7c1736f786b2c59678826b71f7f9349629057
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926246"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Faz com que o processo passe uma instrução ou instrução.

> [!NOTE]
> Esse método deve ser usado em vez de [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md).

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

## <a name="parameters"></a>Parâmetros
`pThread`\
no Um objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o thread que está sendo percorrido.

`sk`\
no Um dos valores de [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) .

`step`\
no Um dos valores de [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) .

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna o código de erro.

## <a name="remarks"></a>Comentários
 Caso haja qualquer sincronização de threads ou comunicação entre threads, outros threads no processo devem ser executados quando um determinado thread está sendo reapresentado.

 **Aviso** Não enviar um evento de interrupção ou um evento imediato (síncrono) para [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao lidar com essa chamada; caso contrário, o depurador pode parar de responder.

## <a name="see-also"></a>Confira também
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
