---
title: 'IDebugDocumentText:: GetLineOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetLineOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetLineOfPosition
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8ce32e46c42ee864a88e169a79539efb8b05633
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572118"
---
# <a name="idebugdocumenttextgetlineofposition"></a>IDebugDocumentText::GetLineOfPosition
Retorna o número de linha e, opcionalmente, o deslocamento de caractere dentro da linha que corresponde à posição de caractere fornecida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cCharacterPosition`  
 no Local inicial do intervalo de posição de caracteres.  
  
 `pcLineNumber`  
 fora O número de linha do intervalo.  
  
 `pcCharacterOffsetInLine`  
 [entrada, saída] O deslocamento de caractere do intervalo dentro da linha `pcLineNumber`. Se esse parâmetro for `NULL`, o método não retornará um valor.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o número de linha e, opcionalmente, o deslocamento de caractere dentro da linha que corresponde à posição de caractere especificada.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)