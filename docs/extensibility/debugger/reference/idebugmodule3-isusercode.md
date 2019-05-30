---
title: IDebugModule3::IsUserCode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1869b9b4bda263d72db9c949be730e51fdc02d01
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323893"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Recupera informações sobre se o módulo representa o código do usuário ou não.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>Parâmetros
`pfUser`\
[out] Diferente de zero (`TRUE`) se o módulo representa o código do usuário, zero (`FALSE`) se não existir.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)