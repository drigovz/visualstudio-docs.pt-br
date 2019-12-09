---
title: 'IActiveScriptSite:: GetDocVersionString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ecc592b6b7fcae5f516a3c1dd111c027e67b6dc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571123"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Recupera uma cadeia de caracteres definida pelo host que identifica exclusivamente a versão atual do documento. Se o documento relacionado tiver sido alterado fora do escopo do script do Windows (como no caso de uma página HTML sendo editada com o bloco de notas), o mecanismo de script poderá salvá-lo junto com seu estado persistente, forçando uma recompilação na próxima vez em que o script for carregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstrVersionString`  
 fora Endereço da cadeia de caracteres de versão de documento definida pelo host.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `S_OK` se for bem-sucedido ou `E_NOTIMPL` se não houver suporte para esse método.  
  
## <a name="remarks"></a>Comentários  
 Se `E_NOTIMPL` for retornado, o mecanismo de script deverá assumir que o script está em sincronia com o documento.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)