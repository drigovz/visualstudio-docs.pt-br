---
title: IDebugDocumentHelper::SetDocumentAttr | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDocumentAttr
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDocumentAttr
ms.assetid: bd7ffdbd-de51-477d-bd3f-760db020fe70
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e743242366c040c02595642fd594ae184436d282
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090318"
---
# <a name="idebugdocumenthelpersetdocumentattr"></a>IDebugDocumentHelper::SetDocumentAttr
Define os atributos para este documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetDocumentAttr(  
   TEXT_DOC_ATTR  pszAttributes  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszAttributes`  
 [in] Os atributos a serem aplicados ao documento.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método define os atributos para este documento.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR Constants](../../winscript/reference/text-doc-attr-constants.md)