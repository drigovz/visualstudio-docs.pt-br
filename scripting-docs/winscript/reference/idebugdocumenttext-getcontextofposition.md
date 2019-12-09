---
title: 'IDebugDocumentText:: GetContextOfPosition | Microsoft Docs'
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
ms.openlocfilehash: d6a35a85a6e4761e1bd0db67caafd0913e7e28a3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572147"
---
# <a name="idebugdocumenttextgetcontextofposition"></a>IDebugDocumentText::GetContextOfPosition
Cria um objeto de contexto de documento correspondente ao intervalo de posição de caracteres fornecido.  
  
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
 no Local inicial do intervalo de posição de caracteres.  
  
 `cNumChars`  
 no Número de caracteres no intervalo.  
  
 `ppsc`  
 fora O objeto de contexto do documento correspondente ao intervalo de posição de caracteres especificado.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método cria um objeto de contexto de documento correspondente ao intervalo de posição de caracteres fornecido.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)