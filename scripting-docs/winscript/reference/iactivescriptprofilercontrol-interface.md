---
title: Interface IActiveScriptProfilerControl | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef127e3a4463d112b9ea424702fb2650c80cce7d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571593"
---
# <a name="iactivescriptprofilercontrol-interface"></a>Interface IActiveScriptProfilerControl
Implementado pelo mecanismo de script que dá suporte à criação de perfil. Normalmente, um objeto que implementa o `IActiveScriptProfilerControl` também implementa a interface [IActiveScript](../../winscript/reference/iactivescript.md) . Nesse caso, você pode obter um identificador para a interface `IActiveScriptProfilerControl` chamando o método `IUnknown::QueryInterface` no objeto. A interface fornece os métodos necessários para parar e iniciar a criação de perfil no mecanismo de script.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Inicia a criação de perfil no mecanismo de script.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Define a máscara de evento do criador de perfil no mecanismo de script.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Interrompe a criação de perfil no mecanismo de script.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do criador de perfil de script ativo](../../winscript/reference/active-script-profiler-interfaces.md)