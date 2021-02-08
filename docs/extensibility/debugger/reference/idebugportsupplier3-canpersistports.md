---
title: 'IDebugPortSupplier3:: CanPersistPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2914d56f2d74629a30bc63bad281bb0cdcdc0de8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840334"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Esse método determina se o fornecedor da porta pode persistir portas (gravando-as no disco) entre invocações do depurador.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parâmetros
 Nenhum.

## <a name="return-value"></a>Valor retornado
 `S_OK` Se as portas puderem ser persistidas ou `S_FALSE` para indicar que as portas não podem ser persistentes.

## <a name="remarks"></a>Comentários
 Se o fornecedor da porta persistir portas, ele deverá fazer isso quando for destruído e, em seguida, recarregá-las quando ela for instanciada novamente.

## <a name="see-also"></a>Consulte também
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
