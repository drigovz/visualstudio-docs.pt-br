---
title: IDebugMethodField::EnumLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08872160860d0d442f9807705dea70190dff9b28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727211"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Cria um enumerador para variáveis locais selecionadas do método.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>parâmetros
`pAddress`\
[em] Um objeto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) representando o endereço de depuração que seleciona o contexto ou o escopo a partir do qual obter os locais.

`ppLocals`\
[fora] Retorna um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) representando uma lista dos locais; caso contrário, retorna um valor nulo se não houver locais.

## <a name="return-value"></a>Valor retornado
Se for bem sucedido, retorna S_OK ou retorna S_FALSE se não houver moradores locais. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
Apenas as variáveis definidas dentro do bloco que contém o endereço de depuração dado são enumeradas. Se todos os locais, incluindo qualquer local gerado pelo compilador, chame o método [EnumAllLocals.](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)

Um método pode conter vários contextos de escopo ou blocos. Por exemplo, o seguinte método inventado contém três escopos, os dois blocos internos e o próprio corpo do método.

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

O objeto [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) `func` representa o método em si. Chamar `EnumLocals` o método com um [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) definido para o `Inner Scope 1` `temp1` endereço retorna uma enumeração contendo a variável, por exemplo.

## <a name="see-also"></a>Confira também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
