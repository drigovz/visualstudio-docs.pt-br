---
title: 'IActiveScriptWinRTErrorDebug:: GetRestrictedErrorReference | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference
ms.assetid: fcf60971-9518-4b24-a3a6-1e2e30a02cea
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4665071fe26ed3dadbaadbcbaa79217562d311c6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577909"
---
# <a name="iactivescriptwinrterrordebuggetrestrictederrorreference"></a>IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference
Retorna o Windows Runtime erro de referência restrita, se disponível.  
  
> [!IMPORTANT]
> A [interface IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) é implementada pelo PDM v 11.0 e superior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRestrictedErrorReference([out] BSTR * referenceString);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `referenceString`  
 fora A cadeia de caracteres de erro de referência.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptWinRTErrorDebug Interface](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)