---
title: IDebugDocumentText::GetLineOfPosition | Microsoft Docs
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
ms.openlocfilehash: 4d5d33a68b4bc87307281e37ff96f84834257a22
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970868"
---
# <a name="idebugdocumenttextgetlineofposition"></a>IDebugDocumentText::GetLineOfPosition
Retorna o número de linha e, opcionalmente, o deslocamento de caractere dentro da linha que corresponde à posição do caractere especificada.  
  
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
 [in] Local do intervalo de posição do caractere inicial.  
  
 `pcLineNumber`  
 [out] O número da linha do intervalo.  
  
 `pcCharacterOffsetInLine`  
 [no, out] O deslocamento de caractere do intervalo na linha `pcLineNumber`. Se esse parâmetro for `NULL`, o método não retorna um valor.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o número de linha e, opcionalmente, o deslocamento de caractere dentro da linha que corresponde à posição do caractere especificada.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)