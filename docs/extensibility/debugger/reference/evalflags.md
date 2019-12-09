---
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a56f7d5fe4741fa887814691eddcf8df93030cd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337889"
---
# <a name="evalflags"></a>EVALFLAGS
Especifica sinalizadores que controlam a avaliação da expressão.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
};
typedef DWORD EVALFLAGS;
```

```csharp
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="fields"></a>Campos
`EVAL_RETURNVALUE`\
Especifica que o valor de retorno, se houver, ser avaliado.

`EVAL_NOSIDEEFFECTS`\
Especifica que os efeitos colaterais não serão permitidas.

`EVAL_ALLOWBPS`\
Especifica parando em pontos de interrupção.

`EVAL_ALLOWERRORREPORT`\
Especifica o relatório de erros para o host a ser permitido. Usado principalmente para a avaliação da expressão no script no Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
Funções de força a ser avaliada como endereços, em vez de invocar a função.

`EVAL_NOFUNCEVAL`\
Impede que a função que está sendo avaliado. Por exemplo, considere a `int` token na expressão `myExpression(int) + 10`. Essa função pode ser avaliada corretamente como um endereço, mas não como um valor.

`EVAL_NOEVENTS`\
Sinalizador para indicar que os eventos que ocorrem durante a avaliação da expressão não devem ser enviados para o Gerenciador de sessão de depuração (SDM) ou para o IDE.

## <a name="remarks"></a>Comentários
Esses sinalizadores são passados como um argumento para o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) e [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) métodos.

Esses sinalizadores podem ser combinados com um OR bit a bit.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
