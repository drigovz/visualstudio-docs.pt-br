---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8393eb7bc712de28e2378a9ad09081efe76eca6b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933939"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> PRETERIDO. NÃO USE.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Valor de retorno

Uma implementação deve retornar sempre `E_NOTIMPL`.

## <a name="remarks"></a>Comentários

> [!WARNING]
> A partir do Visual Studio 2005, esse método não é mais usado e deve retornar sempre `E_NOTIMPL`.

Esse método é chamado quando o depurador fecha inesperadamente. Quando este método é chamado, o DE deve retomar o programa como se o usuário desanexado dele. Não há mais eventos de depuração devem ser enviados. O programa deve estar em um estado onde é anexável de outra instância do depurador.

## <a name="see-also"></a>Consulte também

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)