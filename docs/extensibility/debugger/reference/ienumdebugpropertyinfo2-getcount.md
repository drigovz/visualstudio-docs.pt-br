---
title: IEnumDebugPropertyInfo2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::GetCount
helpviewer_keywords:
- IEnumDebugPropertyInfo2::GetCount
ms.assetid: 9b0b3ce6-08cb-46fd-a6d9-92b36e60da19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d1bdf42f52334b0b3bbc8e7044a4f1297831b24c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212060"
---
# <a name="ienumdebugpropertyinfo2getcount"></a>IEnumDebugPropertyInfo2::GetCount
Retorna o número de elementos na enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parâmetros
`pcelt`\
[out] Retorna o número de elementos na enumeração.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método não é parte do que a interface de enumeração COM habitual que especifica que somente o `Next`, `Clone`, `Skip`, e `Reset` métodos precisam ser implementados.

## <a name="see-also"></a>Consulte também
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)