---
title: IActiveScriptProfilerCallback2 Interface | Microsoft Docs
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
ms.openlocfilehash: b0a0df287db477c5bf768798f200ea0d97de6d1e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385938"
---
# <a name="iactivescriptprofilercallback2-interface"></a>Interface IActiveScriptProfilerCallback2
Fornece métodos que são usados pelo mecanismo de script para notificar um objeto do criador de perfil quando ocorrem eventos de modelo de objeto de documento (DOM). Essa interface é implementada pelo objeto do criador de perfil.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Notifica o objeto de criador de perfil que o mecanismo de script será executado uma chamada de função do DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Notifica o criador de perfil de objeto que o script do mecanismo de concluir a execução de uma chamada de função do DOM.|  
  
## <a name="remarks"></a>Comentários  
 O `IActiveScriptProfilerCallback2` interface lançado pela primeira vez com o Internet Explorer 9.  
  
 Notificação de chamadas de função que não são chamadas no DOM é fornecida pelos [IActiveScriptProfilerCallback Interface](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
> Para adicionar a capacidade de iniciar e parar a criação de perfil quando um script é executado, chame os métodos a seguir. Usando esses métodos, você pode obter a pilha de chamadas completa se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] estiver em execução quando você iniciar ou parar a criação de perfil.  
> 
> - Chame [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) para notificar o criador de perfil que você tiver iniciado a criação de perfil.  
>   - Chame [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) para notificar o criador de perfil que você irá parar em breve de criação de perfil.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do criador de perfil de script ativo](../../winscript/reference/active-script-profiler-interfaces.md)