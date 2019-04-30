---
title: IDebugDocumentInfo::GetDocumentClassId | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetDocumentClassId
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetDocumentClassId
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e86c42954fafd4135956845f9465629cde9990
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971076"
---
# <a name="idebugdocumentinfogetdocumentclassid"></a>IDebugDocumentInfo::GetDocumentClassId
Retorna um `CLSID` identificando o tipo de documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pclsidDocument`  
 [out] Um `CLSID` identificando o tipo de documento.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método permite que o IDE do depurador para visualizadores personalizados de host para este documento.  
  
 Se o documento não tiver dados visível, o valor de retorno `pclsidDocument` é `CLSID_NULL`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)