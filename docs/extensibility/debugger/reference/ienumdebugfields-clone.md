---
title: IEnumDebugFields::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d78427fd3f5e949560be4abb4e1a55616cea859
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66208102"
---
# <a name="ienumdebugfieldsclone"></a>IEnumDebugFields::Clone
Esse método retorna uma cópia da enumeração atual como um objeto separado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Clone(
   IEnumDebugFields** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parâmetros
`ppEnum`\
[out] Retorna uma cópia dessa enumeração como um objeto separado.

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A cópia da enumeração tem o mesmo estado original no momento em que esse método é chamado. No entanto, a cópia e o original estados são separados e podem ser alterados individualmente.

## <a name="see-also"></a>Consulte também
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)