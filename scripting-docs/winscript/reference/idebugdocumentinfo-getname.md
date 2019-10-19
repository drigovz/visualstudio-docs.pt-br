---
title: 'IDebugDocumentInfo:: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc098da29367a322bd93b4f60ba0e090aee9ee91
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570965"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Retorna o nome do documento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dnt`  
 no O tipo de nome do documento a ser retornado.  
  
 `pbstrName`  
 fora Cadeia de caracteres que contém o nome.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|O nome do documento especificado não é conhecido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o nome do documento especificado.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)  
 [DOCUMENTNAMETYPE Enumeration](../../winscript/reference/documentnametype-enumeration.md)