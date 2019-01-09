---
title: IDebugDocumentInfo::GetName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f3ecde4fbde1a265596a01d7f0f953763363e797
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097689"
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
 [in] O tipo de nome de documento a ser retornado.  
  
 `pbstrName`  
 [out] Cadeia de caracteres que contém o nome.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|O nome do documento especificado não é conhecido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o nome do documento especificado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE Enumeration](../../winscript/reference/documentnametype-enumeration.md)