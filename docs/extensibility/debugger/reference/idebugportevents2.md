---
title: IDebugPortEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c611eb531bdabb633b11ac2e8ca2d0d11f52005
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725181"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Esta interface notifica um ouvinte (tipicamente o gerenciador de depuração de sessão [SDM] ou um mecanismo de depuração) de criação e destruição de processos e programas em uma determinada porta. Essas informações podem ser usadas para apresentar uma visão em tempo real dos processos e programas em execução na porta.

## <a name="syntax"></a>Sintaxe

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O Visual Studio normalmente implementa essa interface para receber notificações sobre criação e destruição de programas. Um mecanismo de depuração também pode implementar esta interface para ouvir tais eventos de porta.

## <a name="notes-for-callers"></a>Observações para chamadores
 Todas as interfaces [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) podem <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> ser consultadas para uma interface. Em <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> seguida, `IDebugPortEvents2` o método <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> para é <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> chamado na interface para obter uma interface. Finalmente, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> o método <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> na interface é chamado para enviar os eventos através do método [Event.](../../../extensibility/debugger/reference/idebugportevents2-event.md)

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugPortEvents2`mostra o método de .

|Método|Descrição|
|------------|-----------------|
|[Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envia eventos que descrevem a criação e destruição de processos e programas no porto.|

## <a name="remarks"></a>Comentários
 `IDebugPortEvents2`também é usado pelo SDM para depurar programas que são executados em um processo que já está sendo depurado.

 Os eventos de porta são passados para o SDM por esta interface.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
