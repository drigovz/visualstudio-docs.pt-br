---
title: IDebugObject2::IsUserData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94c3f6adc9dd75e1ed4ecc4c5fd7f37635099566
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317251"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Determina se o objeto representa dados de usuário.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>Parâmetros
`pfUser`\
[out] Retorna não zero (`TRUE`) se o objeto representa dados de usuário; zero (`FALSE`) se não existir.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Dados de usuário são qualquer objeto que faz parte de um módulo designado como JustMyCode (uma opção configurável pelo usuário que marca um módulo, como código de usuário e, portanto, visíveis em um rastreamento de pilha).

## <a name="see-also"></a>Consulte também
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)