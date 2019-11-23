---
title: 'IDebugDocumentHelper:: Attach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3400a5bf6cd3e4a9726fdf4b2f20bbf43b9fc989
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577029"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
Adiciona este documento à árvore de documentos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pddhParent`  
 no A árvore de documentos onde este documento será adicionado. Pode ser NULL.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método adiciona este documento à árvore de documentos, usando `pddhParent` como o pai. Se o `pddhParent` for `NULL`, este documento será o documento de nível superior.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [IDebugDocumentHelper Interface](../../winscript/reference/idebugdocumenthelper-interface.md)