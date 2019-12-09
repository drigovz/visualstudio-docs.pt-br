---
title: 'IActiveScriptAuthor:: GetChars | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetChars
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ce2b46d65c2ce92111bc4b6f44f66ce9dc4ce5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576247"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Retorna o conjunto de caracteres de conclusão para um contexto de conclusão solicitado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fRequestedList`  
 no O contexto de conclusão solicitado.  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Solicita a enumeração do lado esquerdo.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Solicita o contexto de conclusão do membro.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Solicita a lista de parâmetros.|  
|SCRIPT_CMPL_COMMIT|0x0004|Solicita a conclusão da lista de parâmetros.|  
  
 `pbstrChars`  
 fora Os caracteres que correspondem ao contexto de conclusão solicitado.  
  
|Parâmetro `fRequestedList`|Caracteres retornados|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptAuthor Interface](../../winscript/reference/iactivescriptauthor-interface.md)