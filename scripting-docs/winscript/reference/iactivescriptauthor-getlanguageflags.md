---
title: 'IActiveScriptAuthor:: GetLanguageFlags | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68da16513050bd87642be2c96212a330a0916608
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576199"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Retorna informações de idioma.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pgrfasa`  
 fora Os sinalizadores que contêm informações de idioma. Pode ser uma combinação dos seguintes valores:  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|O idioma prefere a criação do manipulador de eventos de script pelo mecanismo de criação de scripts em vez do aplicativo.|  
|fasaSupportInternalHandler|0x0002|O idioma dá suporte a manipuladores de eventos de script criados pelo mecanismo de criação de scripts.|  
|fasaCaseSensitive|0x0004|A linguagem de script diferencia maiúsculas de minúsculas.|  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Se o mecanismo de criação de scripts gerencia manipuladores de eventos, seu aplicativo deve chamar `CreateChildHandler` de um objeto `IScriptEntry`. Isso cria um objeto `IScriptScriptlet` que corresponde ao manipulador de eventos. O mecanismo também adiciona um manipulador de eventos à entrada de script. O manipulador de eventos é uma função vazia que contém as informações de assinatura especificadas.  
  
 Se seu aplicativo gerencia manipuladores de eventos, ele deve chamar `CreateChildHandler` de um objeto `IScriptNode` que representa um Scriptlet manipulador de eventos. Isso cria um objeto `IScriptScriptlet` que está associado ao scriptlet do manipulador de eventos. O aplicativo também precisa adicionar uma função vazia como um manipulador de eventos a um objeto de `IScriptEntry` novo ou existente.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptAuthor Interface](../../winscript/reference/iactivescriptauthor-interface.md)