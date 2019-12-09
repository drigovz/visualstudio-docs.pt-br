---
title: IDebugBinder3::FindAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8387a3302395d6e25c2b00dd360286e533531168
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344416"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Esse método localiza um alias, dado um nome. Isso irá procurar todos os aliases no programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parâmetros
`pcstrName`\
[in] Nome do alias para localizar.

`ppAlias`\
[out] Alias encontrada (se houver) representado pela [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interface.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` (se o alias não for encontrado) ou um código de erro.

## <a name="remarks"></a>Comentários
 Esse método inicializa o objeto de destino para nulo antes de chamar; em seguida, ele testa um valor nulo determinar se o alias foi encontrado.

## <a name="see-also"></a>Consulte também
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)