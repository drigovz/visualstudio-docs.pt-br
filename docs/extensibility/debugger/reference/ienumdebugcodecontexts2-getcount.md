---
title: IEnumDebugCodeContexts2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::GetCount
helpviewer_keywords:
- IEnumDebugCodeContexts2::GetCount
ms.assetid: 74c52fcf-688c-40df-9acd-29b3b84e6216
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d45d99d56ba95db9cbe2443c84c85ba87803eef
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223291"
---
# <a name="ienumdebugcodecontexts2getcount"></a>IEnumDebugCodeContexts2::GetCount
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
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)