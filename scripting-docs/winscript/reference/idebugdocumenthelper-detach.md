---
title: IDebugDocumentHelper::D Etach | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Detach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Detach
ms.assetid: 820b9a8c-9a88-479a-b095-daea99394f9c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 876e23d3466352cb244cc445b2435f556bb88160
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576970"
---
# <a name="idebugdocumenthelperdetach"></a>IDebugDocumentHelper::Detach
Remove este documento da árvore de documentos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Detach();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método remove este documento da árvore de documentos.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentHelper:: anexar](../../winscript/reference/idebugdocumenthelper-attach.md)    
 [IDebugDocumentHelper Interface](../../winscript/reference/idebugdocumenthelper-interface.md)