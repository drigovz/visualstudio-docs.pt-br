---
title: 'IActiveScriptProfilerControl:: SetProfilerEventMask | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.SetProfilerEventMask
apilocation:
- scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4162cf2e5325bfb41bce9c3a47a52b1b36d74f2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571584"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
Define um bitmask de 4 bytes que especifica os tipos de eventos que o mecanismo de script deve gerar.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwEventMask`  
 no Um bitmask de 4 bytes que especifica os tipos de eventos. Os bits são definidos na [Enumeração PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um HRESULT. Os valores possíveis são:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|A criação de perfil não está habilitada.|  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)