---
title: IDebugProperty3::GetStringChars | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 693a29bc30ef206428713ace36275389de1b7f0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721087"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Recupera a string associada a esta propriedade e armazena-a em um buffer fornecido pelo usuário.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetStringChars(
    ULONG  buflen,
    WCHAR* rgString,
    ULONG* pceltFetched
);
```

```csharp
int GetStringChars(
    uint       buflen,
    out string rgString,
    out uint   pceltFetched
);
```

## <a name="parameters"></a>parâmetros
`buflen`\
[em] Número máximo de caracteres que o buffer fornecido pelo usuário pode conter.

`rgString`\
[fora] Devolve a corda.

 [C++ somente], `rgString` é um ponteiro para um buffer que recebe os caracteres Unicode da string. Este buffer deve `buflen` ser pelo menos caracteres (não bytes) em tamanho.

`pceltFetched`\
[fora] Onde o número de caracteres realmente armazenados no buffer é devolvido. (Pode `NULL` estar em C++.)

## <a name="return-value"></a>Valor retornado
Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
Em C++, deve-se tomar cuidado para garantir `buflen` que o buffer tenha pelo menos caracteres Unicode. Observe que um caractere Unicode tem 2 bytes de comprimento.

> [!NOTE]
> Em C++, a seqüência retornada não inclui um caractere nulo final. Se dado, `pceltFetched` especificará o número de caracteres na seqüência.

## <a name="example"></a>Exemplo

```cpp
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)
{
    CStringW returnString = L"";
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;
    If (pProp3 != NULL) {
        ULONG dwStrLen = 0;
        HRESULT hr;
        hr = pProp3->GetStringCharLength(&dwStrLen);
        if (SUCCEEDED(hr) && dwStrLen > 0) {
            ULONG dwRead;
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);
            hr = pProp3->GetStringChars(dwStrLen,
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),
                                        &dwRead);
        }
    }
    return(returnString);
}
```

## <a name="see-also"></a>Confira também
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
