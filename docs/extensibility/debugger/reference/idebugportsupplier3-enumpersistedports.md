---
title: IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d37ec7c2a81b036c80e7fab30fc794d51f21703
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204288"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Esse método recupera um objeto que permite a enumeração da lista de portas persistentes.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parâmetros
`PortNames`\
[in] Um [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) estrutura que contém uma lista de nomes de porta para encontrar e retornar entre as portas persistentes. Somente as portas persistentes com esses nomes serão retornadas.

`ppEnum`\
[out] Um objeto que implementa o [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) interface.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Portas persistentes são carregadas quando um fornecedor de porta é instanciado e salvo quando o fornecedor de porta é destruído.

## <a name="see-also"></a>Consulte também
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)