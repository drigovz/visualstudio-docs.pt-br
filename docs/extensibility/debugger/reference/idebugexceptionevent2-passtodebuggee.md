---
title: IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aec6f460295b59b2b5455b83d5b0be554bca24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729838"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Especifica se a exceção deve ser transmitida ao programa que está sendo depurado quando a execução é retomada ou se a exceção deve ser descartada.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>parâmetros
`fPass`\
[em] Não zero`TRUE`( ) se a exceção deve ser repassada ao programa`FALSE`que está sendo depurado quando a execução for retomada, ou zero ( ) se a exceção deve ser descartada.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Chamar esse método não faz com que nenhum código seja executado no programa que está sendo depurado. A chamada é apenas para definir o estado para a próxima execução do código. Por exemplo, chamadas para o método [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) podem retornar `S_OK` com o [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` campo definido `EXCEPTION_STOP_SECOND_CHANCE`para .

 O IDE pode receber o evento [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) e chamar o método [Continuar.](../../../extensibility/debugger/reference/idebugprogram2-continue.md) O mecanismo de depuração (DE) deve ter `PassToDebuggee` um comportamento padrão para lidar com o caso se o método não for chamado.

## <a name="see-also"></a>Confira também
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
