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
ms.openlocfilehash: 5dd666d825c40155675714f5945209f22198993c
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984400"
---
# <a name="idebugapplicationthreadevents110-interface"></a>Interface IDebugApplicationThreadEvents110
Adiciona mais eventos de thread. Esses eventos são apenas locais. Ou seja, você pode assiná-los somente no processo que está sendo depurado, usando os métodos Advise e Unadvise do [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) em objetos de thread do aplicativo PDM (objetos que implementam a [interface IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)). Elas ocorrem no thread de origem.  
  
> [!IMPORTANT]
> Esta interface é implementada pelo PDM v11.0 e superiores. Localizado em. activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 A interface `IDebugActivationThreadEvents110` expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Uma chamada para o thread usando a alternância de threads do PDM foi iniciada.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|O thread está retomando de um ponto de interrupção e estará ativo mais uma vez.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|O thread está suspendendo para um ponto de interrupção e pode manipular chamadas que exigem que o thread seja totalmente suspenso.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Uma chamada para o thread usando a alternância de threads do PDM foi concluída.|