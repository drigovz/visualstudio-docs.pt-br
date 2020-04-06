---
title: IDebugDocumentContext2::GetStatementRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e521d98f10477d56dfece30e20fd000b87b632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731776"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
Obtém o intervalo de declaração de arquivo do contexto do documento.

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

## <a name="parameters"></a>parâmetros
`pBegPosition`\
[dentro, fora] Uma [estrutura TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que é preenchida com a posição inicial. Defina esse argumento como um valor nulo se essas informações não forem necessárias.

`pEndPosition`\
[dentro, fora] Uma [estrutura TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que é preenchida com a posição final. Defina esse argumento como um valor nulo se essas informações não forem necessárias.

## <a name="return-value"></a>Valor retornado
Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
Um intervalo de declaração é o intervalo das linhas que contribuíram com o código a que este contexto do documento se refere.

Para obter a gama de código-fonte (incluindo comentários) neste contexto de documento, ligue para o método [GetSourceRange.](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como `CDebugContext` implementar esse método para um objeto simples que expõe a interface [IDebugDocumentContext2.](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Este exemplo preenche a posição final somente se a posição inicial não for um valor nulo.

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

## <a name="see-also"></a>Confira também
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
