---
title: 'IDebugApplicationNode100:: SetFilterForEventSink | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f85241bee7b35d40bf193a613a6fefda4265be6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574732"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Define o filtro em uma implementação de [interface IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) específica. Ele permite que os depuradores de script filtrem nós de aplicativos filho gerados pelo compilador para que o PDM não envie mais eventos quando eles forem criados ou removidos. Por padrão, todos os nós serão enviados.  
  
> [!IMPORTANT]
> A [interface IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) é implementada pelo PDM v 10.0 e superior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwCookie`  
 O cookie do filtro.  
  
 `filter`  
 O filtro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplicationNode100 Interface](../../winscript/reference/idebugapplicationnode100-interface.md)