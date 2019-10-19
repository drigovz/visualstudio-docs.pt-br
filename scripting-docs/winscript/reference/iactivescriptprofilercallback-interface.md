---
title: Interface IActiveScriptProfilerCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ae520dcb36e00dfaba8702db6294a5a47484b0a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571718"
---
# <a name="iactivescriptprofilercallback-interface"></a>Interface IActiveScriptProfilerCallback
Fornece métodos que são usados pelo mecanismo de script para notificar um objeto de criador de perfil quando ocorrem eventos. Essa interface é implementada pelo objeto Profiler.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Chamado para inicializar o objeto Profiler sempre que a criação de perfil é iniciada em um mecanismo de script.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Chamado para liberar e liberar o objeto Profiler sempre que a criação de perfil for interrompida em um mecanismo de script.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Notifica o objeto Profiler que o mecanismo de script compilou o script.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Notifica o objeto Profiler que o mecanismo de script encontrou uma função ao compilar um script.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Notifica o objeto Profiler que o mecanismo de script está prestes a executar uma chamada de função que não é uma chamada para o Modelo de Objeto do Documento (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Notifica o objeto Profiler de que o mecanismo de script concluiu a execução de uma chamada de função que não é uma chamada para o DOM.|  
  
## <a name="remarks"></a>Comentários  
 A notificação de chamadas de função para o Modelo de Objeto do Documento (DOM) é fornecida pela [interface IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
> Para adicionar a capacidade de iniciar e parar a criação de perfil quando um script estiver em execução, chame os métodos a seguir. Usando esses métodos, você pode obter a pilha de chamadas completa se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] estiver em execução quando você iniciar ou parar a criação de perfil.  
> 
> - Chame [IActiveScriptProfilerControl2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) para notificar o criador de perfil de que você iniciou a criação de perfis.  
>   - Chame [IActiveScriptProfilerControl2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) para notificar o criador de perfil de que você irá parar em breve a criação de perfil.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do criador de perfil de script ativo](../../winscript/reference/active-script-profiler-interfaces.md)