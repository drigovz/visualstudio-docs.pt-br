---
title: IDebugExpression2::AssessSync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 306ed6af2a0a0b8fdb4525a112e680e289e6e6df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729679"
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
Este método avalia a expressão de forma sincronizada.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EvaluateSync(
    EVALFLAGS             dwFlags,
    DWORD                 dwTimeout,
    IDebugEventCallback2* pExprCallback,
    IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
    enum_EVALFLAGS       dwFlags,
    uint                 dwTimeout,
    IDebugEventCallback2 pExprCallback,
    out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>parâmetros
`dwFlags`\
[em] Uma combinação de bandeiras da [enumeração EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que controlam a avaliação da expressão.

`dwTimeout`\
[em] Tempo máximo, em milissegundos, para esperar antes de retornar deste método. Use `INFINITE` para esperar indefinidamente.

`pExprCallback`\
[em] Este parâmetro é sempre um valor nulo.

`ppResult`\
[fora] Retorna o objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que contém o resultado da avaliação de expressão.

## <a name="return-value"></a>Valor retornado
Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. Alguns códigos de erro típicos são:

|Erro|Descrição|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Outra expressão está sendo avaliada e a avaliação simultânea de expressão não é suportada.|
|E_EVALUATE_TIMEOUT|Avaliação cronometrada.|

## <a name="remarks"></a>Comentários
Para avaliação síncrona, não é necessário enviar um evento de volta ao Visual Studio após a conclusão da avaliação.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como `CExpression` implementar esse método para um objeto simples que implementa a interface [IDebugExpression2.](../../../extensibility/debugger/reference/idebugexpression2.md)

```cpp
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,
                                  DWORD dwTimeout,
                                  IDebugEventCallback2* pExprCallback,
                                  IDebugProperty2** ppResult)
{
    // Set the aborted state to FALSE.
    m_bAborted = FALSE;
    // Delegate the evaluation to EvalExpression.
    return EvalExpression(TRUE, ppResult);
}

HRESULT CExpression::EvalExpression(BOOL bSynchronous,
                                    IDebugProperty2** ppResult)
{
    HRESULT hr;

    // Get the value of an environment variable.
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);
    // Create and initialize a CEnvVar object with the retrieved value.
    // CEnvVar implements the IDebugProperty2 interface.
    CComObject<CEnvVar> *pEnvVar;
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);

    if (pszVal) {
        // Check for synchronous evaluation.
        if (bSynchronous) {
            // Set and AddRef the result, IDebugProperty2 interface.
            *ppResult = pEnvVar;
            (*ppResult)->AddRef();
            hr = S_OK;
        } else {
            //For asynchronous evaluation, send an evaluation complete event.
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);
        }
    } else {
        // If a valid value is not retrieved, return E_FAIL.
        hr = E_FAIL;
    }
    return hr;
}
```

## <a name="see-also"></a>Confira também
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
