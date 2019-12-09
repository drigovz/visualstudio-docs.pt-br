---
title: 'IApplicationDebuggerUI:: BringDocumentToTop | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b51e7b588750fc72e61840c4748c006eea732c22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577804"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Traz a janela que contém o documento de depuração especificado para a parte superior da interface do usuário do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pddt`  
 no Documento de depuração para trazer para a parte superior na interface do usuário do depurador.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_INVALIDARG`|O documento não é conhecido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método traz a janela que contém o documento de depuração especificado para a parte superior da interface do usuário do depurador.  
  
## <a name="see-also"></a>Consulte também  
 [IApplicationDebuggerUI Interface](../../winscript/reference/iapplicationdebuggerui-interface.md)