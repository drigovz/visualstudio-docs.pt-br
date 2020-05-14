---
title: IDebugProcess3::Passo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5c4927f3f997b7fdbdca2b32977f2aa31a51219
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723558"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Faz com que o processo dê um passo à tona instrução ou declaração.

> [!NOTE]
> Este método deve ser usado em vez de [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md).

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

## <a name="parameters"></a>parâmetros
`pThread`\
[em] Um objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) representando o segmento que está sendo pisado.

`sk`\
[em] Um dos valores [STEPKIND.](../../../extensibility/debugger/reference/stepkind.md)

`step`\
[em] Um dos valores [STEPUNIT.](../../../extensibility/debugger/reference/stepunit.md)

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna código de erro.

## <a name="remarks"></a>Comentários
 No caso de haver qualquer sincronização de rosca ou comunicação entre os segmentos, outros segmentos no processo devem ser executados quando um segmento específico estiver pisando.

 **Aviso** Não envie um evento de parada ou um evento imediato (síncrono) para [o Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante o tratamento desta chamada; caso contrário, o depurador pode travar.

## <a name="see-also"></a>Confira também
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
