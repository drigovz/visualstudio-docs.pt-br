---
title: IDebugProperty3::GetStringChars | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01558ccf2d4f0e06231a9cbe152c47b1601bfdb2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658092"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Recupera a cadeia de caracteres associada a essa propriedade e o armazena em um buffer fornecido pelo usuário.

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

#### <a name="parameters"></a>Parâmetros
`buflen`

 [in] Número máximo de caracteres em que o buffer fornecido pelo usuário pode conter.

`rgString`

 [out] Retorna a cadeia de caracteres.

 [C++ somente], `rgString` é um ponteiro para um buffer que recebe os caracteres Unicode da cadeia de caracteres. Esse buffer deve ter pelo menos `buflen` caracteres (não em bytes) de tamanho.

`pceltFetched`

 [out] Em que o número de caracteres, na verdade, são armazenados no buffer é retornado. (Pode ser `NULL` em C++.)

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
No C++, tome cuidado para garantir que o buffer seja pelo menos `buflen` caracteres Unicode. Observe que um caractere Unicode é de 2 bytes de comprimento.

> [!NOTE]
> No C++, a cadeia de caracteres retornada não inclui um caractere nulo de terminação. Se fornecido, `pceltFetched` especificará o número de caracteres na cadeia de caracteres.

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

## <a name="see-also"></a>Consulte também
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
