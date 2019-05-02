---
title: IActiveScriptWinRTErrorDebug::GetRestrictedErrorString | Microsoft Docs
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
ms.openlocfilehash: 154909183e044267053a04ebc489de6dddd55788
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425869"
---
# <a name="iactivescriptwinrterrordebuggetrestrictederrorstring"></a>IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
Retorna o tempo de execução do Windows restrita a cadeia de caracteres de erro, se disponível.  
  
> [!IMPORTANT]
> [IActiveScriptWinRTErrorDebug Interface](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) é implementada pelo PDM v11.0 e maior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRestrictedErrorString([out] BSTR * errorString);   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `errorString`  
 [out] A cadeia de caracteres de erro restrito.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptWinRTErrorDebug Interface](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)