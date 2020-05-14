---
title: IDebugProgram2::Terminate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913c90e34e308ce5bb4ceecface739afc8d03f3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722753"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Termina o programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Se possível, o programa será encerrado e descarregado do processo; caso contrário, o motor de depuração (DE) realizará qualquer limpeza necessária.

 Este método ou o método [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) é chamado pelo IDE, normalmente em resposta ao usuário parar toda a depuração. A implementação desse método deve, idealmente, encerrar o programa dentro do processo. Se isso não for possível, o DE deve impedir que o programa seja executado mais neste processo (e faça qualquer limpeza necessária). Se `IDebugProcess2::Terminate` o método foi chamado pelo IDE, todo o processo `IDebugProgram2::Terminate` será encerrado algum tempo após o método ser chamado.

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Encerrar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
