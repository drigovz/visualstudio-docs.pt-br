---
title: IDebugBinder3::FindAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2b0185b0c3f7f26cfe9ffa8806c5049af323c517
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614961"
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