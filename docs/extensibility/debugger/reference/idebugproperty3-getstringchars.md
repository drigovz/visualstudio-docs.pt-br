---
title: IDebugProperty3::GetStringChars | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 6ce59e1fcbc9b219f1436bd09d4d947cd6995c0f
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450419"
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

[C++ apenas], `rgString` é um ponteiro para um buffer que recebe os caracteres Unicode da cadeia de caracteres. Esse buffer deve ter pelo menos `buflen` caracteres (não em bytes) de tamanho.

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
[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)  
[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)  
[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
