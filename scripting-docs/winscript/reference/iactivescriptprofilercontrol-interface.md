---
title: IActiveScriptProfilerControl Interface | Microsoft Docs
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
ms.openlocfilehash: 86f4fb8dea97930f717800a14a27740b76eb6c2e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993052"
---
# <a name="iactivescriptprofilercontrol-interface"></a>Interface IActiveScriptProfilerControl
Implementado pelo mecanismo de script que dá suporte à criação de perfil. Normalmente, um objeto que implementa o `IActiveScriptProfilerControl` também implementa o [IActiveScript](../../winscript/reference/iactivescript.md) interface. Nesse caso, você pode obter um identificador para o `IActiveScriptProfilerControl` interface chamando o `IUnknown::QueryInterface` método no objeto. A interface fornece os métodos necessários para parar e iniciar a criação de perfil no mecanismo de script.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Inicia a criação de perfil no mecanismo de script.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Define o criador de perfil máscara de evento no mecanismo de script.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Interrompe a criação de perfil no mecanismo de script.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do criador de perfil de script ativo](../../winscript/reference/active-script-profiler-interfaces.md)