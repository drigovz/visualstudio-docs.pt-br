---
title: 'IDebugDocumentHelper:: AddUnicodeText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddUnicodeText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddUnicodeText
ms.assetid: f4ef648e-c55d-4ef0-8df3-e808b798d3b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5820c380c92f2c3cd95763b440d5f9755db3e717
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577062"
---
# <a name="idebugdocumenthelperaddunicodetext"></a>IDebugDocumentHelper::AddUnicodeText
Anexa uma cadeia de caracteres Unicode ao final deste documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszText`  
 no Ponteiro para uma cadeia de caracteres terminada em nulo que contém o texto.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|O método não pôde adicionar os caracteres.|  
  
## <a name="remarks"></a>Comentários  
 Esse método gera notificações de `IDebugDocumentTextEvents`.  
  
> [!NOTE]
> Se esse método for chamado depois que `AddDeferredText` for chamado, `E_FAIL` será retornado.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [Interface IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)