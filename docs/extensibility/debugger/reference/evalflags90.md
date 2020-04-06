---
title: EVALFLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01951885541ba4acce33f3e4f06f7106116ccc62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737094"
---
# <a name="evalflags90"></a>EVALFLAGS90
Enumera os valores válidos para bandeiras que controlam a avaliação de expressão. Esta enumeração estende a [enumeração EVALFLAGS.](../../../extensibility/debugger/reference/evalflags.md)

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>Campos
`EVAL90_RETURNVALUE`\
Especifica que o valor de retorno, se houver, seja avaliado.

`EVAL90_NOSIDEEFFECTS`\
Especifica que efeitos colaterais não são permitidos.

`EVAL90_ALLOWBPS`\
Especifica parar em pontos de interrupção.

`EVAL90_ALLOWERRORREPORT`\
Especifica que o relatório de erro para o host é permitido. Usado principalmente para avaliação de expressão em script no Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
As forças funcionam para serem avaliadas como endereços, em vez de invocar a função.

`EVAL90_NOFUNCEVAL`\
Impede que a função seja avaliada. Por exemplo, `int` considere o token na expressão `myExpression(int) + 10`. Esta função pode ser avaliada corretamente como um endereço, mas não como um valor.

`EVAL90_NOEVENTS`\
Sinalizar para indicar que os eventos que ocorrem durante a avaliação de expressão não devem ser enviados ao gerente de depuração de sessão (SDM) ou ao IDE.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Permite a avaliação da expressão de tempo de projeto.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Permite a criação implícita de variáveis.

`EVAL90_FORCE_EVALUATION_NOW`\
A avaliação das forças ocorrerá imediatamente. Isso é útil ao atender a uma solicitação, como uma solicitação de usuário.

## <a name="requirements"></a>Requisitos
Cabeçalho: Msdbg90.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
