---
title: IRemoteDebugApplication110::GetMainThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61939a015481d479804213163a9f4019be1b2e4e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152425"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Retorna o thread principal para hosts que chamam [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), caso contrário, retornará E_FAIL.  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md) é implementada pelo PDM v11.0 e maior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppThread`  
 [out] A principal [IRemoteDebugApplicationThread Interface](../../winscript/reference/iremotedebugapplicationthread-interface.md).  
  
## <a name="see-also"></a>Consulte também  
 [Interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Interface IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)