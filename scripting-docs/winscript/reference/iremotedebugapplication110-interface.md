---
title: Interface IRemoteDebugApplication110 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110 Interface
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea8f3f983cf7279cf6dc9600813a08268cef8301
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383490"
---
# <a name="iremotedebugapplication110-interface"></a>Interface IRemoteDebugApplication110
Usado para fornecer novos recursos que podem ser chamados por depuradores de script e os chamadores em processo.  
  
> [!IMPORTANT]
> Esta interface é implementada pelo PDM v11.0 e superiores. Localizado em. activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 A interface `IRemoteDebugApplication110` expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|Chamado para atualizar as opções do depurador. O padrão de opções como 0 (SDO_NONE).|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|Retorna o conjunto atual de opções que estão habilitados.|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|Retorna o thread principal para hosts que chamam SetSite.|