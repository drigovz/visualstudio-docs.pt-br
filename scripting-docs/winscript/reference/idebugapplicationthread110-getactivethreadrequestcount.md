---
title: IDebugApplicationThread110::GetActiveThreadRequestCount | Microsoft Docs
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
ms.openlocfilehash: 3df2f0c44e42cf9e2c2aa846db4b88821fd73996
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440562"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Retorna o número de solicitações de segmento de thread do PDM alternância mecanismos que estão sendo processados. Geralmente, esse número é 0 ou 1. No entanto, o número pode ser maior se uma chamada thread começa a processar, mas dispara uma chamada síncrona fora do thread, ou caso contrário, suspende o thread e permite que as chamadas de entrada a ser processada novamente (por exemplo, disparando uma [ IRemoteDebugApplicationEvents Interface](../../winscript/reference/iremotedebugapplicationevents-interface.md) evento, que é emitido no thread do depurador).  
  
> [!IMPORTANT]
> [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) é implementada pelo PDM v11.0 e maior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `puiThreadRequests`  
 [out] O número de solicitações de thread.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)