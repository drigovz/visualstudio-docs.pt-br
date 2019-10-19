---
title: 'IRemoteDebugApplication110:: setdebuggeroptions | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7168a4ef8ec70368c0ff691ba1f721275f9d65d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577421"
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
Chamado para atualizar as opções do depurador. Esse método deve ser chamado após [IRemoteDebugApplication:: ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md). O método [IRemoteDebugApplication::D isconnectdebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) é automaticamente redefinido para as opções padrão. As opções são padrão como 0 (SDO_NONE).  
  
> [!IMPORTANT]
> A [interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) é implementada pelo PDM v 11.0 e superior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mask`  
 A máscara de [Enumeração SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
 `value`  
 O valor de [Enumeração SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)  
 [Interface IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)