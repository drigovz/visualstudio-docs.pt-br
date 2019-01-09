---
title: IActiveScriptError::GetSourceLineText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourceLineText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourceLineText
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3186ec3edcdd0c66f06f7b769eff31e8b050c428
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091670"
---
# <a name="iactivescripterrorgetsourcelinetext"></a>IActiveScriptError::GetSourceLineText
Recupera a linha no arquivo de origem em que ocorreu um erro enquanto um mecanismo de script estava em execução em um script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## <a name="parameter"></a>Parâmetro  
 `pbstrSourceLine`  
 [out] Endereço de um buffer que recebe a linha de código-fonte no qual ocorreu o erro.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se for bem-sucedido, ou `E_FAIL` se a linha no arquivo de origem não foi recuperada.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)