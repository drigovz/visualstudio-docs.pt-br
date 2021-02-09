---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0593a2ee8c519169bd8cb2eb23a83c4f5f3506a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898625"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Preterido. NÃO USE.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Valor retornado

Uma implementação sempre deve retornar `E_NOTIMPL` .

## <a name="remarks"></a>Comentários

> [!WARNING]
> A partir do Visual Studio 2005, esse método não é mais usado e sempre deve retornar `E_NOTIMPL` .

Esse método é chamado quando o depurador é encerrado inesperadamente. Quando esse método é chamado, o DE deve retomar o programa como se o usuário fosse desanexado dele. Não devem ser enviados mais eventos de depuração. O programa deve estar em um estado no qual é possível anexá-lo de outra instância do depurador.

## <a name="see-also"></a>Confira também

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
