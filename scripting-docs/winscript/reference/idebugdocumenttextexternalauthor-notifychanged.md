---
title: IDebugDocumentTextExternalAuthor::NotifyChanged | Microsoft Docs
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
ms.openlocfilehash: 1290de76f8bec5018ad83eb4499c3d92cbf9eba9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147716"
---
# <a name="idebugdocumenttextexternalauthornotifychanged"></a>IDebugDocumentTextExternalAuthor::NotifyChanged
Notifica o host que a origem do documento foi alterado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado por um editor externo depois que um documento do depurador com base em arquivo é modificado e salvo para notificar o host que a origem do documento foi alterado. O host, em seguida, atualiza o documento do arquivo de origem.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentTextExternalAuthor Interface](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)