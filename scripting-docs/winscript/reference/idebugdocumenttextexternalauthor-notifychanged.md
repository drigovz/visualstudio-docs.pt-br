---
title: 'IDebugDocumentTextExternalAuthor:: NotifyChanged | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::NotifyChanged
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad02db80bd24a8a5ba96abaa61e85be9d69e553e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575952"
---
# <a name="idebugdocumenttextexternalauthornotifychanged"></a>IDebugDocumentTextExternalAuthor::NotifyChanged
Notifica o host de que a origem do documento foi alterada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado por um editor externo depois que um documento de depurador baseado em arquivo é modificado e salvo para notificar o host de que a origem do documento foi alterada. O host, em seguida, atualiza o documento do arquivo de origem.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentTextExternalAuthor Interface](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)