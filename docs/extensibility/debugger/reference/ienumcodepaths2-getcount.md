---
title: IEnumCodePaths2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::GetCount
helpviewer_keywords:
- IEnumCodePaths2::GetCount
ms.assetid: 988c5092-fcc5-43a1-a94c-c261edd56ebf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9356b58131e8478840d68a3965d0f6fabf314a55
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310063"
---
# <a name="ienumcodepaths2getcount"></a>IEnumCodePaths2::GetCount
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
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)