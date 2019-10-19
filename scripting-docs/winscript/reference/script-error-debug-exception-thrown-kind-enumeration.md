---
title: Enumeração SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8eb089efbf608b488465809f997ffc82fc2c2e3c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574406"
---
# <a name="script_error_debug_exception_thrown_kind-enumeration"></a>Enumeração SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Indica o tipo de exceção lançada. Essa enumeração é usada pelo método [IActiveScriptErrorDebug110:: GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) .  
  
> [!IMPORTANT]
> Essas constantes são implementadas pela versão 11.0 PDM e superiores. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Valor|Descrição|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|A exceção é uma exceção de primeira tentativa.|  
|ETK_USER_UNHANDLED|0x00000001|A exceção não é manipulada no código de usuário.|  
|ETK_UNHANDLED|0x00000002|A exceção não é manipulada no código.|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptErrorDebug110 Interface](../../winscript/reference/iactivescripterrordebug110-interface.md)