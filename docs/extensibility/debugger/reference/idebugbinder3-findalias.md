---
title: IDebugBinder3::FindAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735868"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Este método localiza um alias, dado um nome. Isso irá procurar todos os pseudônimos no programa.

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

## <a name="parameters"></a>parâmetros
`pcstrName`\
[em] Nome do pseudônimo para encontrar.

`ppAlias`\
[fora] Alias encontrado (se houver) representado pela interface [IDebugAlias.](../../../extensibility/debugger/reference/idebugalias.md)

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, `S_FALSE` retornas (se alias não for encontrado) ou um código de erro.

## <a name="remarks"></a>Comentários
 Este método inicializa o objeto de destino a nulo antes de chamar; em seguida, ele testa um valor nulo depois para determinar se o alias foi encontrado ou não.

## <a name="see-also"></a>Confira também
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
