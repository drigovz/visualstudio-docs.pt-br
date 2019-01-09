---
title: IDebugApplication::FCanJitDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FCanJitDebug
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6808c8bb7e27e7b416e79b2f23e323c3ae3a528f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095349"
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
Determina se um depurador do just-in-time (JIT) está registrado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido e um depurador JIT está registrado, o método retorna `TRUE`. Caso contrário, retornará `FALSE`.  
  
## <a name="remarks"></a>Comentários  
 Este método determina se um depurador JIT está registrado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplication Interface](../../winscript/reference/idebugapplication-interface.md)