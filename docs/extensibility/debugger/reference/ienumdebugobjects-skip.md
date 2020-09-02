---
title: 'IEnumDebugObjects:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Skip
helpviewer_keywords:
- IEnumDebugObjects::Skip method
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80d2ae53ea7732a2120cf0431f33f929a0a6bc05
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716276"
---
# <a name="ienumdebugobjectsskip"></a>IEnumDebugObjects::Skip
Esse método ignora o número especificado de elementos.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   [In] uint celt
);
```

## <a name="parameters"></a>Parâmetros
`celt`\
no Número de elementos a serem ignorados.

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se `celt` é maior que o número de elementos restantes; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Se `celt` o especificar um valor maior que o número de elementos restantes, a enumeração será definida como end e `S_FALSE` será retornada.

## <a name="see-also"></a>Confira também
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
