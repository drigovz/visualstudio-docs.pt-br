---
title: IDebugProgramNode2:Attach_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdee5b224ae38c3474009aeaf26e783ebc5dd139
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722132"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Preterido. NÃO USE.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

## <a name="parameters"></a>parâmetros

`pMDMProgram`\
[em] A interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa o programa a ser anexado.

`pCallback`\
[em] A interface [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) a ser usada para enviar eventos de depuração para o SDM.

`dwReason`\
[em] Um valor da [enumeração ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) que especifica o motivo da anexação.

## <a name="return-value"></a>Valor retornado

Uma implementação `E_NOTIMPL`deve sempre retornar .

## <a name="remarks"></a>Comentários

> [!WARNING]
> A partir do Visual Studio 2005, este método `E_NOTIMPL`não é mais utilizado e deve sempre retornar . Consulte a interface [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) para obter uma abordagem alternativa se o nó do programa precisar indicar `GUID`que ele não pode ser anexado ou se o nó do programa está simplesmente definindo o programa . Caso contrário, implemente o método [Anexar.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="prior-to-visual-studio-2005"></a>Antes do Visual Studio 2005

Este método só precisa ser implementado se o DE for executado no espaço de endereço do programa que está sendo depurado. Caso contrário, este `S_FALSE`método deve retornar .

Quando esse método é chamado, o DE deve enviar o objeto de evento [IDebugEngineCreateEvent2,](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) se ele ainda não tiver sido enviado para esta instância da interface [IDebugEngine2,](../../../extensibility/debugger/reference/idebugengine2.md) bem como os objetos de evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) e [IDebugLoadCompleteEvent2.](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) O objeto de evento [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) é enviado se o `dwReason` parâmetro for `ATTACH_REASON_LAUNCH`.

O DE deve chamar o método [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) no objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) fornecido pelo objeto de evento [IDebugProgramCreateEvent2,](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) e deve armazenar os dados guid do programa nos dados de instância para o `IDebugProgram2` objeto implementado pelo DE.

## <a name="see-also"></a>Confira também

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
