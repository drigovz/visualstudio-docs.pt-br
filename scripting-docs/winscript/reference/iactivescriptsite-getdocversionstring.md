---
title: IActiveScriptSite::GetDocVersionString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a451f4883373978772643e11fe22feb9122be30e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349745"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Recupera uma cadeia de caracteres definida pelo host que identifica exclusivamente a versão atual do documento. Se o documento relacionado foi alterado fora do escopo de Script do Windows (como no caso de uma página HTML que está sendo editado com o bloco de notas), o mecanismo de script pode salvar isso juntamente com seu estado persistente, forçar uma recompilação na próxima vez em que o script é carregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstrVersionString`  
 [out] Endereço da cadeia de caracteres de versão do documento definido pelo host.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se for bem-sucedido, ou `E_NOTIMPL` se esse método não tem suporte.  
  
## <a name="remarks"></a>Comentários  
 Se `E_NOTIMPL` for retornado, o mecanismo de script deve pressupor que o script está em sincronizado com o documento.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)