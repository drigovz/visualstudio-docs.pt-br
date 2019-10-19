---
title: IActiveScriptProfilerControl2::P repareProfilerStop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 24d4d73e0263882ad028ea66d3fac5e24f3af9ba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571437"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Notifica o criador de perfil de que você vai parar a criação de perfil em todos os mecanismos de script aplicáveis. Usando esse método, você pode obter a pilha de chamadas completa se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] estiver em execução quando você parar a criação de perfil.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 O método não pega nenhum parâmetro.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um HRESULT. Os valores possíveis são:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|Não foi possível iniciar a criação de perfil.|  
|`S_FALSE`|A criação de perfil foi interrompida quando um script não estava em execução.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|A criação de perfil não está habilitada.|  
  
## <a name="remarks"></a>Comentários  
 Chamar `IActiveScriptProfilerControl2::PrepareProfilerStop` garante que os eventos para funções na pilha de chamadas sejam enviados. Esse método deve ser chamado antes de você parar a criação de perfil em qualquer mecanismo de script que esteja na guia atual. O método pode ser chamado para qualquer mecanismo de script.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptProfilerControl2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)    
 [Interface IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)