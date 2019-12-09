---
title: Interface IActiveScriptProfilerCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f9616497192659df67feedfe16bd9ea0c5e3b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577310"
---
# <a name="iactivescriptprofilercallback2-interface"></a>Interface IActiveScriptProfilerCallback2
Fornece métodos que são usados pelo mecanismo de script para notificar um objeto de criador de perfil quando ocorrerem eventos de Modelo de Objeto do Documento (DOM). Essa interface é implementada pelo objeto Profiler.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Notifica o objeto Profiler que o mecanismo de script vai executar uma chamada de função DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Notifica o objeto Profiler de que o mecanismo de script concluiu a execução de uma chamada de função DOM.|  
  
## <a name="remarks"></a>Comentários  
 A interface `IActiveScriptProfilerCallback2` lançada pela primeira vez com o Internet Explorer 9.  
  
 A notificação de chamadas de função que não são chamadas para o DOM é fornecida pela [interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
> Para adicionar a capacidade de iniciar e parar a criação de perfil quando um script estiver em execução, chame os métodos a seguir. Usando esses métodos, você pode obter a pilha de chamadas completa se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] estiver em execução quando você iniciar ou parar a criação de perfil.  
> 
> - Chame [IActiveScriptProfilerControl2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) para notificar o criador de perfil de que você iniciou a criação de perfis.  
>   - Chame [IActiveScriptProfilerControl2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) para notificar o criador de perfil de que você irá parar em breve a criação de perfil.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do criador de perfil de script ativo](../../winscript/reference/active-script-profiler-interfaces.md)