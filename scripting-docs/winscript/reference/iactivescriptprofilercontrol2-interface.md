---
title: Interface IActiveScriptProfilerControl2 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7059868ae65c5093b24f342bd303ec70172171c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571538"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>Interface IActiveScriptProfilerControl2
Fornece métodos que adicionam a capacidade de iniciar ou parar a criação de perfil quando um script é executado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Notifica o criador de perfil de que você iniciou a criação de perfis em todos os mecanismos de script aplicáveis. Isso permite que você obtenha a pilha de chamadas completa se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] estiver em execução quando você iniciar a criação de perfil.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Notifica o criador de perfil de que você vai parar a criação de perfil em todos os mecanismos de script aplicáveis. Isso permite que você obtenha a pilha de chamadas completa se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] estiver em execução quando você parar a criação de perfil.|  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)  
 [Interfaces do criador de perfil de script ativo](../../winscript/reference/active-script-profiler-interfaces.md)