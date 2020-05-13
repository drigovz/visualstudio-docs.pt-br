---
title: IEnumDebugCustomAttributes::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Clone
helpviewer_keywords:
- IEnumDebugCustomAttributes::Clone
ms.assetid: e6825000-e195-42b4-b296-bfe1e533d79b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3c6cd55293bf34b0c2780dd76eaf8f4ee81bb69
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717266"
---
# <a name="ienumdebugcustomattributesclone"></a>IEnumDebugCustomAttributes::Clone
Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Clone ( 
   IEnumCustomAttributes** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>parâmetros
`ppEnum`\
[fora] Retorna uma cópia desta enumeração como um objeto separado.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A cópia da enumeração tem o mesmo estado do original no momento em que este método é chamado. No entanto, os estados da cópia e do original são separados e podem ser alterados individualmente.

## <a name="see-also"></a>Confira também
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
