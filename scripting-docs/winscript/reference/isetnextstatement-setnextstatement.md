---
title: ISetNextStatement::SetNextStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.SetNextStatement
apilocation:
- scrobj.dll
ms.assetid: c5534f3b-39a5-4466-b8fc-69b717c6eee9
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f21814d0739b304921108fcfdb3c3da80bee9b6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093113"
---
# <a name="isetnextstatementsetnextstatement"></a>ISetNextStatement::SetNextStatement
Esse método atualiza o contexto de código próxima que o interpretador de script pode ser executados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStackFrame`  
 [in] Ponteiro para um objeto de quadro de pilha.  
  
 `pCodeContext`  
 [in] Ponteiro para um objeto de contexto de código.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)