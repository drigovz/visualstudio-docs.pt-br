---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2bf436d788b517300bee9a13b66b0ca3747bcc43
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724466"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Este método determina se o fornecedor de portas pode persistir portas (escrevendo-as em disco) entre invocações do depurador.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>parâmetros
 Nenhum.

## <a name="return-value"></a>Valor retornado
 `S_OK`se as portas puderem `S_FALSE` ser persistindo ou indicar que as portas não podem ser permaneciadas.

## <a name="remarks"></a>Comentários
 Se o fornecedor de porto puder persistir nas portas, ele deve fazê-lo quando for destruído e, em seguida, recarregá-los quando for instanciado novamente.

## <a name="see-also"></a>Confira também
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
