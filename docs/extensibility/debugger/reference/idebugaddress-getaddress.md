---
title: IDebugAddress::GetAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 162a64c9118bdcde23208082350005e607a237b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736609"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Retorna uma estrutura descrevendo um objeto e sua localização dentro de seu escopo ou contêiner.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>parâmetros
`pAddress`\
[dentro, fora] Uma [estrutura DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) que é preenchida por este método.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A [estrutura DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) é passada para este método, que então preenche-o com as informações apropriadas. A forma como essas informações são interpretadas depende do tipo de informação devolvida e do próprio manipulador de símbolos. Consulte [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) para mais detalhes.

## <a name="see-also"></a>Confira também
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
