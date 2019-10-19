---
title: 'Método IJsDebugFrame:: Evaluate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6227b97c1fd5fae32db3e13ef72751726c36b043
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573493"
---
# <a name="ijsdebugframeevaluate-method"></a>Método IJsDebugFrame::Evaluate
Avalie uma expressão no contexto deste quadro de pilhas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pExpressionText`  
 no A expressão a ser avaliada.  
  
 `ppDebugProperty`  
 fora Objeto que representa o navegador de propriedades.  
  
 `pError`  
 fora A mensagem de erro, se ocorrer um erro.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="remarks"></a>Comentários  
 Retorna o seguinte: S_OK: Evaluation tem sucesso, * ppDebugProperty contém o resultado da avaliação. S_FALSE: a avaliação gera um erro (ou a operação de avaliação não tem suporte), \*pError contém a mensagem de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)