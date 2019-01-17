---
title: Interface IDebugApplicationThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 262174d0daecd2c37bafbecee13532ba62e9967f
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347782"
---
# <a name="idebugapplicationthread-interface"></a>Interface IDebugApplicationThread
Permite que os mecanismos de linguagem e hosts para fornecer sincronização de thread e para manter informações de estado de depuração específicas de thread. Essa interface estende o `IRemoteDebugApplicationThread` interface para fornecer acesso de não remoto para o thread.  
  
 Além dos métodos herdados de `IRemoteDebugApplicationThread`, o `IDebugApplicationThread` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Fornece um mecanismo para que o chamador executar o código no thread do aplicativo.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Determina se esse thread é o thread em execução no momento.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Determina se este segmento é o depurador.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Define a descrição desse thread.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Define a descrição do estado do thread.|