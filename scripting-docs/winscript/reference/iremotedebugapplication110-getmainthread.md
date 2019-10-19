---
title: 'IRemoteDebugApplication110:: GetMainThread | Microsoft Docs'
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
ms.openlocfilehash: ff99c43f633da8454eb5fa32463886877e06ed72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574116"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Retorna o thread principal para hosts que chamam [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), caso contrário retorna E_FAIL.  
  
> [!IMPORTANT]
> A [interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) é implementada pelo PDM v 11.0 e superior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppThread`  
 fora A [interface IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)principal.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)  
 [Interface IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)