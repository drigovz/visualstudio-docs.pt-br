---
title: IDebugDefaultPort2::QueryIsLocal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42a21419af9be56647a835ee1d8ddab62e20f842
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351749"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Este método determina se essa porta é no computador local.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Valor de retorno
 Retorna `S_OK` se essa porta é local (no mesmo computador que o chamador) ou `S_FALSE` se a porta estiver em outro computador.

## <a name="see-also"></a>Consulte também
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)