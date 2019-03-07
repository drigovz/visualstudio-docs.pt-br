---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad31d015048d8e0732c32652141b7be060628663
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722623"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Este método determina se o fornecedor de porta pode persistir portas (gravando-os em disco) entre as invocações do depurador.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

#### <a name="parameters"></a>Parâmetros
 nenhuma.

## <a name="return-value"></a>Valor de retorno
 `S_OK` Se as portas podem ser persistentes, ou `S_FALSE` para indicar que as portas não podem ser persistente.

## <a name="remarks"></a>Comentários
 Se o fornecedor de porta pode manter as portas, ele deverá fazê-lo quando ele é destruído e recarregá-los, em seguida, quando ela é instanciada novamente.

## <a name="see-also"></a>Consulte também
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)