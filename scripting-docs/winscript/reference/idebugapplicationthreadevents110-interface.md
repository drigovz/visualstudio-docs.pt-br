---
title: Interface IDebugApplicationThreadEvents110 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0051f18c67fffc9801ad326745a0dc9dd63f4391
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148848"
---
# <a name="idebugapplicationthreadevents110-interface"></a>Interface IDebugApplicationThreadEvents110
Adiciona mais eventos de thread. Esses eventos são apenas locais. Ou seja, você pode se inscrever neles apenas no processo que está sendo depurado, usando o [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) aconselhá- e não recomendar métodos em objetos de thread de aplicativo do PDM (objetos que implementam [IDebugApplicationThread Interface](../../winscript/reference/idebugapplicationthread-interface.md)). Eles ocorrem no thread em que eles são provenientes.  
  
> [!IMPORTANT]
>  Esta interface é implementada pelo PDM v11.0 e superiores. Localizado em. activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 A interface `IDebugActivationThreadEvents110` expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Uma chamada o thread usando o thread do PDM alternância foi iniciado.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|O thread está voltando de um ponto de interrupção e estará ativo novamente.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|O thread está suspenso para um ponto de interrupção e pode lidar com chamadas que exigem o thread a ser suspenso totalmente.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Uma chamada para o thread usando o thread do PDM troca foi concluída.|