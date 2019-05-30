---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8f05596b12151b3a40b87c6fc2f15659a38e3431
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337684"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
Especifica o estado de exceção.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>Campos
`EXCEPTION_NONE`\
Não pare na exceção.

`EXCEPTION_STOP_FIRST_CHANCE`\
Pare no primeiro disparo da exceção. Ao descrever um evento de exceção, esse sinalizador indica que o evento de exceção é um evento de exceção de primeira chance.

`EXCEPTION_STOP_SECOND_CHANCE`\
Pare no segundo acionamento da exceção. Ao descrever um evento de exceção, indica que o evento de exceção é um evento de exceção de segunda chance.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Pare no primeiro acionamento de uma exceção do modo de usuário. Ao descrever um evento de exceção, indica que o evento de exceção é um evento de exceção do usuário de primeira chance.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Interrompa quando uma exceção do modo de usuário não é capturada. Ao descrever um evento de exceção, indica que o evento de exceção é um evento de exceção de modo de usuário não identificadas.

`EXCEPTION_STOP_ALL`\
Interrompa qualquer exceção. Não é usado para descrever um evento de exceção.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Ao descrever um evento de exceção, indica que a exceção não pode ser continuada de.

`EXCEPTION_CODE_SUPPORTED`\
Indica que a exceção tem código que dão suporte a ele. Usados para exibir uma exceção

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Indica que o código de exceção deve ser exibido em hexadecimal. Usados para exibir uma exceção.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Indica que o código de exceção oferece suporte a JustMyCode. Usados para exibir uma exceção.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Indica que o depurador de código gerenciado deve lidar com exceções. Se não for definido, o depurador padrão manipula as exceções. Isso é passado para o [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) método e não usado na [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estrutura.

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
OBSOLETO, NÃO USE.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
OBSOLETO, NÃO USE.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
OBSOLETO, NÃO USE.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
OBSOLETO, NÃO USE.

## <a name="remarks"></a>Comentários
Usado como o `dwState` membro a [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estrutura para indicar o estado da exceção e o que pode ser feito sobre isso.

Esses valores também são passados para o [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) método para definir o estado de todas as exceções.

Esses sinalizadores podem ser combinados com um OR bit a bit.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
