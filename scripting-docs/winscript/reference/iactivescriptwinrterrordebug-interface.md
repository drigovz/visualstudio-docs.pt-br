---
title: IActiveScriptWinRTErrorDebug Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 52e7728b4143231912227e5e55faa5eef01b7490
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425783"
---
# <a name="iactivescriptwinrterrordebug-interface"></a>Interface IActiveScriptWinRTErrorDebug
Implementado pelo mecanismo de JavaScript para fornecer informações estendidas de erro de tempo de execução do Windows de um [enumeração BREAKREASON](../../winscript/reference/breakreason-enumeration.md) eventos. Você pode fazer uma QueryInterface para obtê-lo de um [IActiveScriptError](../../winscript/reference/iactivescripterror.md) objeto.  
  
> [!IMPORTANT]
> Esta interface é implementada pelo PDM v11.0 e superiores. Localizado em. activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 A interface `IActiveScriptWinRTErrorDebug` expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Retorna o SID do recurso para o erro de tempo de execução do Windows, se disponível.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Retorna o tempo de execução do Windows restrita a cadeia de caracteres de referência de erro, se disponível.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Retorna o tempo de execução do Windows restrita a cadeia de caracteres de erro, se disponível.|