---
title: 'IActiveScriptProfilerControl:: StartProfiling | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StartProfiling
apilocation:
- scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b37b60f50351496faceb97190ae0d173eba3a5f4
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983265"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Inicia a criação de perfil no mecanismo de script. O mecanismo de script cria uma instância do objeto Profiler fazendo uma chamada para [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `clsidProfilerObject`  
 no Identificador de classe (CLSID) do objeto do criador de perfil a ser criado.  
  
 `dwEventMask`  
 no Um bitmask de 4 bytes que especifica os tipos de eventos. Os bits são definidos na [Enumeração PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 no Um valor de 4 bytes que é passado para o objeto Profiler.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um HRESULT. Os valores possíveis são:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|A criação de perfil já está habilitada.|  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)