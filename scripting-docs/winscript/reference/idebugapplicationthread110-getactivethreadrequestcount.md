---
title: 'IDebugApplicationThread110:: GetActiveThreadRequestCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7f038c1d0958701a14899825a2adb0a11cf604d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574487"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Retorna o número de solicitações de thread dos mecanismos de troca de thread do PDM que estão sendo processados no momento. Esse número é geralmente 0 ou 1. No entanto, o número pode ser maior se uma chamada de thread iniciar o processamento, mas disparar uma chamada síncrona fora do thread, ou suspender o thread e permitir que as chamadas de entrada sejam processadas novamente (por exemplo, disparando um [IRemoteDebugApplicationEvents ](../../winscript/reference/iremotedebugapplicationevents-interface.md)Evento de interface, que é emitido no thread do depurador).  
  
> [!IMPORTANT]
> A [interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) é implementada pelo PDM v 11.0 e superior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `puiThreadRequests`  
 fora O número de solicitações de thread.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)