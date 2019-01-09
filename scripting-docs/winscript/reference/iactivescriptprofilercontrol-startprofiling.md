---
title: IActiveScriptProfilerControl::StartProfiling | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3a64bbb790933513d29ee1a534472ac92c2072cf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088290"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Inicia a criação de perfil no mecanismo de script. O mecanismo de script cria uma instância do objeto criador de perfil, fazendo uma chamada para [CoCreateInstance](https://docs.microsoft.com/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `clsidProfilerObject`  
 [in] Identificador de classe (CLSID) do objeto criador de perfil a ser criado.  
  
 `dwEventMask`  
 [in] Um bitmask de 4 bytes que especifica os tipos de eventos. Os bits são definidos no [enumeração PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 [in] Um valor de 4 bytes que é passado para o objeto de criador de perfil.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um HRESULT. Os valores possíveis são:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Criação de perfil já está habilitada.|  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)