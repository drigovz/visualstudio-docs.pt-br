---
title: 'IActiveScriptProfilerControl2:: CompleteProfilerStart | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0230ecb480792b5b24b7375f5b95926735d0a61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571559"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Notifica o criador de perfil de que você iniciou a criação de perfis em todos os mecanismos de script aplicáveis. Usando esse método, você pode obter a pilha de chamadas completa se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] estiver em execução quando você iniciar a criação de perfil.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 O método não pega nenhum parâmetro.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um HRESULT. Os valores possíveis são:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|A criação de perfil não pode ser iniciada.|  
|`S_FALSE`|A criação de perfil foi iniciada quando um script não estava em execução.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|A criação de perfil não está habilitada. Nenhum retorno de chamada foi definido.|  
|`E_OUTOFMEMORY`|A pilha de chamadas não pode ser obtida devido a uma condição de memória insuficiente.|  
  
## <a name="remarks"></a>Comentários  
 Chamar `IActiveScriptProfilerControl2::CompleteProfilerStart` garante que os eventos para as funções que já estão na pilha de chamadas sejam enviados. Esse método deve ser chamado depois que a criação de perfil é iniciada em qualquer mecanismo de script que esteja na guia atual. O método pode ser chamado para qualquer mecanismo de script.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptProfilerControl2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)    
 [Interface IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)