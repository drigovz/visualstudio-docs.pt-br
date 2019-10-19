---
title: 'IActiveScriptSite:: getlcid | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 913ca23ac687fdd080a778afb1dcba2e4dcdd6b8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570743"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Recupera o identificador de localidade associado à interface do usuário do host. O mecanismo de script usa o identificador para garantir que as cadeias de caracteres de erro e outros elementos de interface do usuário gerados pelo mecanismo apareçam no idioma apropriado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `plcid`  
 fora Endereço de uma variável que recebe o identificador de localidade para elementos de interface do usuário exibidos pelo mecanismo de script.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_NOTIMPL`|Este método não está implementado. Use a localidade definida pelo sistema.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
  
## <a name="remarks"></a>Comentários  
 Se esse método retornar `E_NOTIMPL`, o identificador de localidade definido pelo sistema deverá ser usado.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)