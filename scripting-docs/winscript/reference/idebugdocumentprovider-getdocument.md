---
title: IDebugDocumentProvider::GetDocument | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentProvider.GetDocument
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentProvider::GetDocument
ms.assetid: da67dab0-778a-4dab-8ca3-055ee7a4f141
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f6b816f455d213cb81065f1909930bf50eeb415
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970881"
---
# <a name="idebugdocumentprovidergetdocument"></a>IDebugDocumentProvider::GetDocument
Faz com que o documento a ser instanciado se ele ainda não existir.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDocument(  
   IDebugDocument**  ppssd  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppssd`  
 [out] O documento de depuração correspondente ao documento.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método faz com que o documento a ser instanciado se ele ainda não existir.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentProvider](../../winscript/reference/idebugdocumentprovider-interface.md)