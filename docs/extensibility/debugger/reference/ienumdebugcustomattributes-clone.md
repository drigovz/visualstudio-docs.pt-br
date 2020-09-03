---
title: 'IEnumDebugCustomAttributes:: clone | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717266"
---
# <a name="ienumdebugcustomattributesclone"></a>IEnumDebugCustomAttributes::Clone
Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.

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

## <a name="parameters"></a>Parâmetros
`ppEnum`\
fora Retorna uma cópia dessa enumeração como um objeto separado.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A cópia da enumeração tem o mesmo estado que o original no momento em que esse método é chamado. No entanto, os Estados da cópia e do original são separados e podem ser alterados individualmente.

## <a name="see-also"></a>Confira também
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
