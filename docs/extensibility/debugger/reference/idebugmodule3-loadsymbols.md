---
title: IDebugModule3::LoadSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c61339305200acc9a6c572a1a96595dc4cb6f50
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726778"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Carrega os símbolos para o módulo atual.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Valor retornado
 Se o método for bem-sucedido, retornará `S_OK`. Se falhar, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Este método carrega os símbolos do caminho de pesquisa atual (que pode ser alterado chamando o método [SetSymbolPath).](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)

 Este método é preferido em relação ao método [ReloadSymbols_Deprecated.](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)

## <a name="see-also"></a>Confira também
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
