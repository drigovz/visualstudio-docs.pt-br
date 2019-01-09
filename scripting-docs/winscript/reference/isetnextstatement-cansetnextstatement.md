---
title: ISetNextStatement::CanSetNextStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.CanSetNextStatement
apilocation:
- scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5288b0cffc3b8bfca0e995e67d4b3e4bf3a6b2e2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090123"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
Este método determina se o ponto de execução, que determina a próxima instrução de código a ser executada, pode ser definido para o local especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CanSetNextStatement(  
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
|`S_OK`|A próxima instrução pode ser atualizada para o contexto de código especificada.|  
|`S_FALSE`|A próxima instrução não pode ser atualizada para o contexto de código especificada.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)