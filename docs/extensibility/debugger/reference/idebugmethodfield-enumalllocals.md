---
title: IDebugMethodField::EnumAllLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727335"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Cria um enumerador para todas as variáveis locais do método, incluindo aquelas geradas internamente por um compilador.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>parâmetros
`pAddress`\
[em] Um objeto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) representando um endereço de depuração dentro do método, apontando para um escopo ou contexto específico.

`ppLocals`\
[fora] Retorna um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) representando a lista de todos os locais no escopo especificado; caso contrário, retorna um valor nulo indicando nenhum local.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK ou retorna S_FALSE se não houver moradores locais. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Apenas as variáveis definidas dentro do bloco que contém o endereço de depuração dado são enumeradas. Este método inclui qualquer local gerado pelo compilador. Se tudo o que é necessário são os locais explicitamente definidos na fonte, chame o método [EnumLocals.](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)

 Um método pode conter vários contextos de escopo ou blocos.

## <a name="see-also"></a>Confira também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
