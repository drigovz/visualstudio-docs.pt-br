---
title: IDebugDocumentContext2::GetStatementRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90f1e9288221efb1a0627d116839772b41b69541
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204619"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
Obtém o intervalo de instrução de arquivo do contexto do documento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetStatementRange(
    TEXT_POSITION* pBegPosition,
    TEXT_POSITION* pEndPosition
);
```

```csharp
int GetStatementRange(
    TEXT_POSITION[] pBegPosition,
    TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parâmetros
`pBegPosition`\
[no, out] Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura será preenchida com a posição inicial. Defina este argumento como um valor nulo se essa informação não é necessária.

`pEndPosition`\
[no, out] Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura será preenchida com a posição final. Defina este argumento como um valor nulo se essa informação não é necessária.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
Um intervalo de instrução é o intervalo de linhas que contribuiu com o código ao qual se refere a este contexto de documento.

Para obter o intervalo de código-fonte (incluindo comentários) dentro desse contexto de documento, chame o [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) método.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como implementar esse método para um simples `CDebugContext` objeto que expõe o [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface. Este exemplo preenche a posição final somente se a posição de início não é um valor nulo.

```cpp
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,
                                         TEXT_POSITION* pEndPosition)
{
    HRESULT hr;

    // Check for a valid beginning position argument pointer.
    if (pBegPosition)
    {
        // Copy the member TEXT_POSITION into the local pBegPosition.
        memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));

        // Check for a valid ending position argument pointer.
        if (pEndPosition)
        {
            // Copy the member TEXT_POSITION into the local pEndPosition.
            memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));
        }
        hr = S_OK;
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Consulte também
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
