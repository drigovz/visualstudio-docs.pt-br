---
title: 'IEnumDebugPorts2:: clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Clone
helpviewer_keywords:
- IEnumDebugPorts2::Clone
ms.assetid: d5ce77e8-bb99-409a-98fa-20fe5a0de25e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87842dfdb3de6ce120967bbbff785a1ec84f9ba4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716226"
---
# <a name="ienumdebugports2clone"></a>IEnumDebugPorts2::Clone
Retorna uma cópia da enumeração atual como um objeto separado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Clone(
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parâmetros
`ppEnum`\
fora Retorna uma cópia dessa enumeração como um objeto separado.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A cópia da enumeração tem o mesmo estado que o original no momento em que esse método é chamado. No entanto, os Estados da cópia e do original são separados e podem ser alterados individualmente.

## <a name="see-also"></a>Confira também
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
