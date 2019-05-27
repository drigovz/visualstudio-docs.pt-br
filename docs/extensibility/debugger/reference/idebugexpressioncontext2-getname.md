---
title: IDebugExpressionContext2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1961ac778dab2d17a87748cae8e1210f6b13422d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66201058"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Recupera o nome do contexto de avaliação.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parâmetros
`pbstrName`\
[out] Retorna o nome do contexto de avaliação.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O nome é a descrição deste contexto de avaliação. Geralmente, é algo que pode ser analisado por um avaliador de expressão que se refere a este contexto de avaliação exato. Por exemplo, em C++ o nome é da seguinte maneira:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>Consulte também
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)