---
title: 'Idebugdocumenthelper:: Addunicodetext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 190df1f621b450c6d3b34c339d21f947f48636f2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093516"
---
# <a name="idebugdocumenthelperaddunicodetext"></a>IDebugDocumentHelper::AddUnicodeText
Acrescenta uma cadeia de caracteres Unicode no final deste documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszText`  
 [in] Ponteiro para uma cadeia de caracteres terminada em nulo que contém o texto.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|O método não pôde adicionar os caracteres.|  
  
## <a name="remarks"></a>Comentários  
 Este método gera `IDebugDocumentTextEvents` notificações.  
  
> [!NOTE]
>  Se esse método é chamado após `AddDeferredText` foi chamado, `E_FAIL` será retornado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Idebugdocumenthelper:: Adddeferredtext](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Interface IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)