---
title: 'IActiveScriptError:: GetSourcePosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ed307f988a3e5bf77ff978c466eda6e5dfee18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576894"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Recupera o local no código-fonte em que ocorreu um erro enquanto o mecanismo de script estava executando um script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwSourceContext`  
 fora Endereço de uma variável que recebe um cookie que identifica o contexto. A interpretação desse parâmetro depende do aplicativo host.  
  
 `pulLineNumber`  
 fora Endereço de uma variável que recebe o número de linha no arquivo de origem em que o erro ocorreu.  
  
 `pichCharPosition`  
 fora Endereço de uma variável que recebe a posição do caractere na linha em que ocorreu o erro.  
  
## <a name="return-value"></a>Valor retornado  
 Retornará `S_OK` se for bem-sucedido ou `E_FAIL` se o local não tiver sido recuperado.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)