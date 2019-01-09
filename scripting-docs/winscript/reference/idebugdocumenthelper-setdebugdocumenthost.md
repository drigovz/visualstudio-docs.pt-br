---
title: 'Idebugdocumenthelper:: Setdebugdocumenthost | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDebugDocumentHost
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDebugDocumentHost
ms.assetid: b26a03c3-8a3f-47b0-b916-4c65d5500f10
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c4a935d849fed2b617abf5ee33ca2901b9c944c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088212"
---
# <a name="idebugdocumenthelpersetdebugdocumenthost"></a>IDebugDocumentHelper::SetDebugDocumentHost
Conjuntos de `IDebugDocumentHost` para este documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetDebugDocumentHost(  
   IDebugDocumentHost*  pddh  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pddh`  
 [in] O host do documento de depuração.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O `IDebugDocumentHost` interface é usada para coloração de sintaxe de host inteligente, buscar texto adiado e retornando objetos de controle para recentemente criado contextos de documento.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHost Interface](../../winscript/reference/idebugdocumenthost-interface.md)