---
title: 'IDebugPortSupplier3:: EnumPersistedPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92b31a6b6898b0031e4a01d5a6433d0ce77e64f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724447"
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
no Uma estrutura de [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) que contém uma lista de nomes de porta para localizar e retornar entre as portas persistentes. Somente as portas persistentes com esses nomes serão retornadas.

`ppEnum`\
fora Um objeto que implementa a interface [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) .

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 As portas persistentes são carregadas quando um fornecedor de porta é instanciado e salvo quando o fornecedor da porta é destruído.

## <a name="see-also"></a>Confira também
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
