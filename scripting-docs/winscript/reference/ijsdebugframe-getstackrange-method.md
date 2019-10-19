---
title: 'Método IJsDebugFrame:: GetStackRange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1ac3cbee9d16296632477f4128ec36370ab0d4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574037"
---
# <a name="ijsdebugframegetstackrange-method"></a>Método IJsDebugFrame::GetStackRange
Retorna o intervalo de endereços absoluto do quadro de pilha JavaScript lógico.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStart`  
 fora Maior parte inferior do ponteiro de pilha do quadro.  
  
 `pEnd`  
 fora Maior parte do ponteiro do empilhador do quadro.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="remarks"></a>Comentários  
 Esse método é útil para compondo juntos rastreamentos de pilha intercalados coletados de vários tempos de execução. Os ponteiros de início de pilha final podem abranger vários quadros de pilha de máquina física (para quadros de tempo de execução JavaScript interpretados). Iniciar > terminar à medida que a pilha cresce de alto para baixo endereço.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)