---
title: Interface IDebugApplication110 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0991f27077cf3ac3eb5cbfdcbb409fd5903d9a66
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446382"
---
# <a name="idebugapplication110-interface"></a>Interface IDebugApplication110
O `IDebugApplication110` interface estende a funcionalidade dos [IDebugApplication Interface](../../winscript/reference/idebugapplication-interface.md). Você pode obter uma instância dessa interface chamando QueryInterface em uma implementação de [IDebugApplication Interface](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
> Esta interface é implementada pelo PDM v11.0 e superiores. Localizado em. activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 A interface `IDebugApplication110` expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Faz uma chamada síncrona no thread principal.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Faz uma chamada assíncrona no thread principal.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Aguarda qualquer uma das alças especificadas a ser sinalizado, permitindo que chamadas entre threads a ser postada a esse thread. Esse método deve ser chamado do thread do depurador.|