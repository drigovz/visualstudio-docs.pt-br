---
title: IDebugExpressionEvaluator::P grosseira | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d1af9d3f253a9849f54bb5a50d432b98eb4ad7b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729497"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Esse método converte uma cadeia de caracteres de expressão em uma expressão analisada.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parâmetros
`upstrExpression`\
no A cadeia de caracteres de expressão a ser analisada.

`dwFlags`\
no Uma coleção de constantes [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) que determinam como a expressão deve ser analisada.

`nRadix`\
no Base a ser usada para interpretar qualquer informação numérica.

`pbstrError`\
fora Retorna o erro como texto legível.

`pichError`\
fora Retorna a posição do caractere do início do erro na cadeia de caracteres da expressão.

`ppParsedExpression`\
fora Retorna a expressão analisada em um objeto [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) .

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método produz uma expressão analisada, não um valor real. Uma expressão analisada está pronta para ser avaliada, ou seja, convertida em um valor.

## <a name="see-also"></a>Confira também
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
