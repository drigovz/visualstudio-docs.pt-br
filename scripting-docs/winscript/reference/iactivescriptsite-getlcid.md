---
title: IActiveScriptSite::GetLCID | Microsoft Docs
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
ms.openlocfilehash: c6ebcfec9764aae98f7d74ac98e0c88ecec7c4da
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155505"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Recupera o identificador de localidade associado com a interface do usuário do host. O mecanismo de script usa o identificador para garantir que as cadeias de caracteres de erro e outros elementos de interface do usuário gerados pelo mecanismo aparecem no idioma apropriado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `plcid`  
 [out] Endereço de uma variável que recebe o identificador de localidade para elementos de interface do usuário exibida pelo mecanismo de script.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_NOTIMPL`|Este método não está implementado. Use a localidade definida pelo sistema.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
  
## <a name="remarks"></a>Comentários  
 Se esse método retornar `E_NOTIMPL`, o identificador de localidade definida pelo sistema deve ser usado.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)