---
title: IDebugDocumentTextEvents::onReplaceText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onReplaceText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onReplaceText
ms.assetid: 3cb053c4-1f7f-4aed-aee6-f8a9e9e69d29
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b65496f3bf64dfaf1a4fc1f1180dd6715277cd59
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152974"
---
# <a name="idebugdocumenttexteventsonreplacetext"></a>IDebugDocumentTextEvents::onReplaceText
Indica que o texto foi substituído.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT onReplaceText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToReplace  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cCharacterPosition`  
 [in] A posição do caractere do primeiro caractere é substituído.  
  
 `cNumToReplace`  
 [in] O número de caracteres serão substituídos.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Este método indica que o texto foi substituído.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)