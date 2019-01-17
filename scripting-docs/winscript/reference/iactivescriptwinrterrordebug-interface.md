---
title: IActiveScriptWinRTErrorDebug Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2355b9aa38abbed2ca66964a07bb47082eb76c32
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346495"
---
# <a name="iactivescriptwinrterrordebug-interface"></a>Interface IActiveScriptWinRTErrorDebug
Implementado pelo mecanismo de JavaScript para fornecer informações estendidas de erro de tempo de execução do Windows de um [enumeração BREAKREASON](../../winscript/reference/breakreason-enumeration.md) eventos. Você pode fazer uma QueryInterface para obtê-lo de um [IActiveScriptError](../../winscript/reference/iactivescripterror.md) objeto.  
  
> [!IMPORTANT]
>  Esta interface é implementada pelo PDM v11.0 e superiores. Localizado em. activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 A interface `IActiveScriptWinRTErrorDebug` expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Retorna o SID do recurso para o erro de tempo de execução do Windows, se disponível.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Retorna o tempo de execução do Windows restrita a cadeia de caracteres de referência de erro, se disponível.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Retorna o tempo de execução do Windows restrita a cadeia de caracteres de erro, se disponível.|