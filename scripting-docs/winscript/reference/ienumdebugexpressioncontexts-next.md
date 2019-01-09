---
title: IEnumDebugExpressionContexts::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExpressionContexts.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugExpressionContexts::Next
ms.assetid: aa223b0b-f7c1-4368-a59e-677e60133baf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c401ba90e25dc88c4e64abab30bda63d037a3f8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087198"
---
# <a name="ienumdebugexpressioncontextsnext"></a>IEnumDebugExpressionContexts::Next
Recupera um número especificado de segmentos na sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Next(  
   ULONG                      celt,  
   IDebugExpressionContext**  ppdec,  
   ULONG*                     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] O número de segmentos para recuperar.  
  
 `ppdec`  
 [out] Retorna uma matriz de `IDebugExpressionContext` interfaces que representa os segmentos que estão sendo recuperados.  
  
 `pceltFetched`  
 [out] O número real de segmentos buscadas pelo enumerador.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método recupera um número especificado de segmentos na sequência de enumeração.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IEnumDebugExpressionContexts](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)