---
title: 'IEnumDebugReferenceInfo2:: clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Clone
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Clone
ms.assetid: 49c5a301-a33a-428f-b83b-e734c71af4ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d522fb7a9b63f634f312924e3c0b0337688aa430
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715318"
---
# <a name="ienumdebugreferenceinfo2clone"></a>IEnumDebugReferenceInfo2::Clone
Retorna uma cópia da enumeração atual como um objeto separado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Clone(
   IEnumDebugReferenceInfo2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugReferenceInfo2 ppEnum
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
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
