---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da3eb33d76f55310e6428a34dd09cabbc271aa68
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719448"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

O mecanismo de depuração (DE) pode enviar este evento opcional para o Gerenciador de depuração de sessão (SDM) quando um programa foi interrompido.

## <a name="syntax"></a>Sintaxe

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores

Esta interface foi introduzida com o Visual Studio 2005. As versões anteriores não suportavam paradas assíncronas.

- [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) é chamado pelo SDM em cenários multiprocessos ou multiprogramas. Quando um programa envia um evento de parada para o SDM, o SDM solicita que outros programas também parem.

Stop é usado para informar assíncronamente o SDM que um programa parou. Informar o SDM é útil para um mecanismo de depuração de intérprete, onde às vezes nenhum código está sendo executado dentro do programa depurado, então [stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) não pode ser concluído sincronizadamente. Se um mecanismo de depuração quiser empregar esta `S_ASYNC_STOP` notificação assíncrona, ele deve retornar de [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Requisitos

Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
