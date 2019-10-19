---
title: 'IActiveScriptWinRTErrorDebug:: GetRestrictedErrorString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
ms.assetid: d901e049-fb1b-4101-a04a-1395d657f1cf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 498d929fb06eea1d6717bfdecb09107bbdaafd98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577901"
---
# <a name="iactivescriptwinrterrordebuggetrestrictederrorstring"></a>IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
Retorna a Windows Runtime cadeia de caracteres de erro restrita, se disponível.  
  
> [!IMPORTANT]
> A [interface IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) é implementada pelo PDM v 11.0 e superior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRestrictedErrorString([out] BSTR * errorString);   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `errorString`  
 fora A cadeia de caracteres de erro restrita.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptWinRTErrorDebug Interface](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)