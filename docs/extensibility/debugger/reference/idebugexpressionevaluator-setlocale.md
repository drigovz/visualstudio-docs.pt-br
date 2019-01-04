---
title: IDebugExpressionEvaluator::SetLocale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 128e00db6f648185c0404de3eddd4387c4067e8a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922345"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Esse método define o idioma a ser usado para criar resultados imprimíveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wLangID`  
 [in] O identificador de idioma.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método pode ser chamado várias vezes enquanto o avaliador de expressão (EE) é carregado, portanto, o EE deve ser capaz de alternar os idiomas em tempo real. O EE usa essa localidade para retornar cadeias de caracteres e mensagens de erro no idioma apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)