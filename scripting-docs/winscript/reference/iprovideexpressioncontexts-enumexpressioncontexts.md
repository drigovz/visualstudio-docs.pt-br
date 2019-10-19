---
title: 'IProvideExpressionContexts:: EnumExpressionContexts | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f161c1591267af1398d5c04d00623381cfae2ad4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572395"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Retorna um enumerador de contextos de expressão conhecidos por este componente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppedec`  
 fora Um enumerador de contextos de expressão conhecidos por este componente.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O Gerenciador de depuração de processo usa esse método para localizar todos os contextos de expressão global associados a um determinado thread.  
  
> [!NOTE]
> Esse método é chamado de dentro do thread de interesse. Cabe ao implementador identificar o thread atual e retornar um enumerador apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [IProvideExpressionContexts Interface](../../winscript/reference/iprovideexpressioncontexts-interface.md)