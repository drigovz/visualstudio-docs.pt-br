---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2a6a6e69bf47751706710801dd78c832ccd2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546909"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

O mecanismo de depuração (DE) pode enviar esse evento opcional para o SDM (Gerenciador de depuração de sessão) quando um programa for interrompido.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 Essa é uma nova interface para o [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] . Versões anteriores não suportavam a interrupção assíncrona.  
  
 [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) é chamado pelo SDM em cenários de vários processos ou vários programas. Quando um programa envia um evento de parada para o SDM, o SDM solicita que outros programas parem também.  
  
 Ele é usado para informar de forma assíncrona o SDM que um programa parou. Isso é útil para um mecanismo de depuração de intérprete, no qual às vezes nenhum código está sendo executado dentro do programa depurado, portanto, [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) não pode ser concluído de forma síncrona. Se um mecanismo de depuração quiser empregar essa notificação assíncrona, ele deverá retornar `S_ASYNC_STOP` de [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
