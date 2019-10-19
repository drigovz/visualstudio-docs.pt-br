---
title: 'IActiveScriptAuthor:: AddTypeLib | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddTypeLib
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bd96732a905d3fc0732ccfeaf2b65ada82957f4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577223"
---
# <a name="iactivescriptauthoraddtypelib"></a>IActiveScriptAuthor::AddTypeLib
Adiciona uma biblioteca de tipos ao namespace para o script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `rguidTypeLib`  
 no O CLSID (identificador de classe) da biblioteca de tipos a ser adicionada.  
  
 `dwMajor`  
 no O número de versão principal.  
  
 `dwMinor`  
 no O número da versão secundária.  
  
 `dwFlags`  
 no Não usado.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método chama `LoadTypeLib` para carregar a biblioteca de tipos. Após o êxito, esse método chama `IActiveScriptAuthor::AddNamedItem` para adicionar informações de tipo.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor:: AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)    
 [LoadTypeLib](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelib)