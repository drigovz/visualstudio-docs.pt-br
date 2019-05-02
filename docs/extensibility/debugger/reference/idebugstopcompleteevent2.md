---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3ec59d6e9a6008f195cab40fe5c1998aff24a50
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915953"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

O mecanismo de depuração (DES) pode enviar esse evento opcional para o Gerenciador de sessão de depuração (SDM) quando um programa foi interrompido.

## <a name="syntax"></a>Sintaxe

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores

Essa interface foi introduzida com o Visual Studio 2005. Versões anteriores não dava suporte assíncrono parando.

- [Parar](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) é chamado pelo SDM em vários processos ou um programas com vários cenários. Quando um programa envia um evento de interrupção para o SDM, o SDM solicita parar, muito de outros programas.

Parada é usada para informar assincronamente o SDM que um programa foi interrompido. Informando o SDM é útil para um mecanismo de depuração do interpretador, em que, às vezes, nenhum código é executado dentro do depurado do programa, isso [parar](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) não pode ser concluída de forma síncrona. Se um mecanismo de depuração deseja empregar essa notificação assíncrona, ela deve retornar `S_ASYNC_STOP` partir [parar](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Requisitos

Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll