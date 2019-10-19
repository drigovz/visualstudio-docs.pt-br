---
title: 'IDebugDocumentHelper:: AddDBCSText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDBCSText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDBCSText
ms.assetid: 5e5011b2-bbb4-491b-9a11-eb2846be44aa
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71d0b7816a0b8801c5fb4eaab9cf7808a3f3bbfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577070"
---
# <a name="idebugdocumenthelperadddbcstext"></a>IDebugDocumentHelper::AddDBCSText
Anexa uma cadeia de caracteres DBCS ao final deste documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddDBCSText(  
   LPCSTR  pszText  
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
> Se esse método for chamado depois que `IDebugDocumentHelper::AddDeferredText` for chamado, `E_FAIL` será retornado.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [Interface IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)