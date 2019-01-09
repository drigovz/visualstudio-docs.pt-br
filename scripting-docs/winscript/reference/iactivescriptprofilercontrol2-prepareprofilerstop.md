---
title: IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 086ec8b4a126c65162638afde4d8081269757e1c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089512"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Notifica o criador de perfil que você pretende parar criação de perfil em todos os mecanismos de script aplicáveis. Usando esse método, você pode obter a pilha de chamadas completa se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] estiver em execução quando você interrompe a criação de perfil.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 O método não leva nenhum parâmetro.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um HRESULT. Os valores possíveis são:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|Não foi possível iniciar a criação de perfil.|  
|`S_FALSE`|Criação de perfil foi interrompida quando um script não estava em execução.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Criação de perfil não está habilitada.|  
  
## <a name="remarks"></a>Comentários  
 Chamar `IActiveScriptProfilerControl2::PrepareProfilerStop` garante que os eventos para as funções na pilha de chamadas são enviados. Esse método deve ser chamado antes de interromper a criação de perfil em qualquer mecanismo de script que está na guia atual. O método pode ser chamado para qualquer mecanismo de script.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [Interface IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)