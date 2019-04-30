---
title: IDebugDocumentText::GetContextOfPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetContextOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetContextOfPosition
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df63362c422289652d45ed4bbc80f117e17fb73c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008711"
---
# <a name="idebugdocumenttextgetcontextofposition"></a>IDebugDocumentText::GetContextOfPosition
Cria um objeto de contexto do documento correspondente ao intervalo de posição de caractere fornecidos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cCharacterPosition`  
 [in] Local do intervalo de posição do caractere inicial.  
  
 `cNumChars`  
 [in] Número de caracteres no intervalo.  
  
 `ppsc`  
 [out] O objeto de contexto de documento correspondentes ao intervalo de posição do caractere especificado.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método cria um objeto de contexto do documento correspondente ao intervalo de posição de caractere fornecidos.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)