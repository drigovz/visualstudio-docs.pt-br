---
title: IDebugExpressionContext2::ParseText | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8494c9c90c4cb6e94115c542a25e12e948f7064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729651"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Analisa uma expressão em forma de texto para avaliação posterior.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2** ppExpr,
    BSTR*               pbstrError,
    UINT*               pichError
);
```

```csharp
int ParseText(
    string                pszCode,
    enum_PARSEFLAGS       dwFlags,
    uint                  nRadix,
    out IDebugExpression2 ppExpr,
    out string            pbstrError,
    out uint              pichError
);
```

## <a name="parameters"></a>parâmetros
`pszCode`\
[em] A expressão a ser analisado.

`dwFlags`\
[em] Uma combinação de bandeiras da enumeração [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) que controla a análise.

`nRadix`\
[em] O rádio a ser usado na análise de qualquer `pszCode`informação numérica em .

`ppExpr`\
[fora] Retorna o objeto [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) que representa a expressão analisado, que está pronto para vinculação e avaliação.

`pbstrError`\
[fora] Retorna a mensagem de erro se a expressão contiver um erro.

`pichError`\
[fora] Retorna o índice de `pszCode` caracteres do erro se a expressão contiver um erro.

## <a name="return-value"></a>Valor retornado
Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
Quando este método é chamado, um mecanismo de depuração (DE) deve analisar a expressão e validá-la para correção. Os `pbstrError` `pichError` parâmetros podem ser preenchidos se a expressão for inválida.

Observe que a expressão não é avaliada, apenas analisado. Uma chamada posterior para os métodos [AssessSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [AssessAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) avalia a expressão analisado.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como `CEnvBlock` implementar esse método para um objeto simples que expõe a interface [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Este exemplo considera a expressão a ser analisado como o nome de uma variável de ambiente e recupera o valor dessa variável.

```cpp
HRESULT CEnvBlock::ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2 **ppExpr,
    BSTR               *pbstrError,
    UINT               *pichError)
{
    HRESULT hr = E_OUTOFMEMORY;
    // Create an integer variable with a value equal to one plus
    // twice the length of the passed expression to be parsed.
    int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;
    // Allocate a character string of the same length.
    char *pszAnsiCode = (char *) malloc(iAnsiLen);

    // Check for successful memory allocation.
    if (pszAnsiCode) {
        // Map the wide-character pszCode string to the new pszAnsiCode character string.
        WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);
        // Check to see if the app can succesfully get the environment variable.
        if (GetEnv(pszAnsiCode)) {

            // Create and initialize a CExpression object.
            CComObject<CExpression> *pExpr;
            CComObject<CExpression>::CreateInstance(&pExpr);
            pExpr->Init(pszAnsiCode, this, NULL);

            // Assign the pointer to the new object to the passed argument
            // and AddRef the object.
            *ppExpr = pExpr;
            (*ppExpr)->AddRef();
            hr = S_OK;
        // If the program cannot succesfully get the environment variable.
        } else {
            // Set the errror message and return E_FAIL.
            *pbstrError = SysAllocString(L"No such environment variable.");
            hr = E_FAIL;
        }
        // Free the local character string.
        free(pszAnsiCode);
    }
    return hr;
}
```

## <a name="see-also"></a>Confira também
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
