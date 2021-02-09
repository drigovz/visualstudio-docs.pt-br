---
title: 'IDebugExpressionEvaluationCompleteEvent2:: GetResult | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9abc7ce472543b6d2fd6e82fbd5a01f97e4d1784
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930441"
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
Obtém o resultado da avaliação de expressão.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetResult( 
   IDebugProperty2** ppResult
);
```

```csharp
int GetResult( 
   out IDebugProperty2 ppResult
);
```

## <a name="parameters"></a>Parâmetros
`ppResult` fora Retorna um objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa o resultado da avaliação da expressão.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) retornado contém o valor da expressão avaliada. Observe que esse valor pode ser um valor complexo, como uma matriz, mas o resultado final deve ser um valor numérico ou de cadeia de caracteres que é exibido para o usuário.

## <a name="see-also"></a>Confira também
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
