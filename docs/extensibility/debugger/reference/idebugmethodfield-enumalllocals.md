---
title: IDebugMethodField::EnumAllLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbbc610dad6ab5915efe07718ad9a80592af4034
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708180"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Cria um enumerador para todas as variáveis locais do método, inclusive aquelas geradas internamente por um compilador.

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

#### <a name="parameters"></a>Parâmetros
 `pAddress`

 [in] Uma [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) que representa um endereço de depuração dentro do método, que aponta para um determinado escopo ou contexto de objeto.

 `ppLocals`

 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de todos os locais no escopo especificado; caso contrário, retornará um valor nulo que indica nenhuma locais.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhum locais. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Somente as variáveis definidas dentro do bloco que contém o endereço de depuração determinado são enumeradas. Esse método inclui qualquer locais gerados pelo compilador. Se tudo o que é necessário são os locais definidos explicitamente na origem, a chamada a [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) método.

 Um método pode conter vários contextos ou blocos de escopo.

## <a name="see-also"></a>Consulte também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)