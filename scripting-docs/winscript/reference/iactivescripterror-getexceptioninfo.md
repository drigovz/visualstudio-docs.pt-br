---
title: 'IActiveScriptError:: GetExceptionInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetExceptionInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetExceptionInfo
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f776a5f1a60b1280ab1f133ead04fb275782e5c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576935"
---
# <a name="iactivescripterrorgetexceptioninfo"></a>IActiveScriptError::GetExceptionInfo
Recupera informações sobre um erro que ocorreu enquanto o mecanismo de script estava executando um script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pexcepinfo`  
 fora Endereço de uma estrutura de `EXCEPINFO` que recebe informações de erro.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `S_OK` se tiver êxito ou `E_FAIL` se ocorreu um erro.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)