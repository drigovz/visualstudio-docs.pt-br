---
title: IEnumDebugEndereços::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Skip
helpviewer_keywords:
- IEnumDebugAddresses::Skip method
ms.assetid: ed9a8e71-30ef-414b-9da5-c9a2a251b84e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4803b447ba049fd934d60a41adb5403335029a9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717595"
---
# <a name="ienumdebugaddressesskip"></a>IEnumDebugAddresses::Skip
Este método ignora o número especificado de elementos.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>parâmetros
`celt`\
[em] Número de elementos para pular.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. `S_FALSE` Retornos `celt` se for maior do que o número de elementos restantes; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Se `celt` especificar um valor maior do que o número de elementos `S_FALSE` restantes, a enumeração é definida até o final e é devolvida.

## <a name="see-also"></a>Confira também
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
