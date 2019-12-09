---
title: 'IActiveScriptProfilerCallback:: Initialize | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Initialize
apilocation:
- scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbbd61d6b3c10dcfffe2df215cc5a60d685dd803
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576452"
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
Chamado para inicializar o objeto Profiler sempre que a criação de perfil é iniciada em um mecanismo de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwContext`  
 no Um valor de 4 bytes que é passado para [IActiveScriptProfilerControl:: StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md).  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um HRESULT. Os valores possíveis são:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Se o método não puder inicializar o objeto Profiler, ele deverá retornar um HRESULT de falha para notificar o mecanismo de script. Nesse caso, o mecanismo de script deve chamar diretamente [IActiveScriptProfilerCallback:: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md), passando o HRESULT no parâmetro e, em seguida, liberar o objeto Profiler.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)