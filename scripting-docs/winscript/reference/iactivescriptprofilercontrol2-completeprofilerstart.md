---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b307352a3ba6d10ec3ae434536dee82d22504d33
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091280"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Notifica o criador de perfil que você tiver iniciado a criação de perfil em todos os mecanismos de script aplicáveis. Usando esse método, você pode obter a pilha de chamadas completa se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] estiver em execução quando você iniciar a criação de perfil.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 O método não leva nenhum parâmetro.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um HRESULT. Os valores possíveis são:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|Criação de perfil não pode ser iniciada.|  
|`S_FALSE`|Criação de perfil foi iniciada quando um script não estava em execução.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Criação de perfil não está habilitada. Nenhum retorno de chamada tiver sido definido.|  
|`E_OUTOFMEMORY`|A pilha de chamadas não pode ser obtida devido a uma condição de falta de memória.|  
  
## <a name="remarks"></a>Comentários  
 Chamar `IActiveScriptProfilerControl2::CompleteProfilerStart` garante que os eventos para as funções já na pilha de chamadas são enviados. Esse método deve ser chamado após a criação de perfil é iniciado em qualquer mecanismo de script que está na guia atual. O método pode ser chamado para qualquer mecanismo de script.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [Interface IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)