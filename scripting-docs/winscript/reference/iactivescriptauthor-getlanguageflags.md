---
title: IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs
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
ms.openlocfilehash: d9f1a68db05ac0d909108ce77587ae4b071c9a2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935465"
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
 [out] Os sinalizadores que contêm informações de idioma. Pode ser uma combinação dos seguintes valores:  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|A linguagem prefere a criação do manipulador de eventos de script pelo script do mecanismo, em vez do aplicativo de criação.|  
|fasaSupportInternalHandler|0x0002|A linguagem dá suporte a manipuladores de eventos de script criados pelo script do mecanismo de criação.|  
|fasaCaseSensitive|0x0004|A linguagem de script diferencia maiusculas de minúsculas.|  
  
## <a name="return-value"></a>Valor de retorno  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Se o mecanismo de criação de script gerencia manipuladores de eventos, seu aplicativo deve chamar `CreateChildHandler` de um `IScriptEntry` objeto. Isso cria um `IScriptScriptlet` objeto que corresponde ao manipulador de eventos. O mecanismo também adiciona um manipulador de eventos para a entrada de script. O manipulador de eventos é uma função vazia que contém as informações de assinatura especificada.  
  
 Se seu aplicativo gerencia a manipuladores de eventos, ele deverá chamar `CreateChildHandler` de um `IScriptNode` objeto que representa um scriptlet de manipulador de eventos. Isso cria um `IScriptScriptlet` objeto que está associado com o scriptlet de manipulador de eventos. O aplicativo também tem que adicionar uma função vazia como um evento de manipulador para um novo ou existente `IScriptEntry` objeto.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptAuthor Interface](../../winscript/reference/iactivescriptauthor-interface.md)