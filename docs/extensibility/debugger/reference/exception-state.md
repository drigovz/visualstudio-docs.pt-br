---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd2e280cd03ae413e0853950d13fbfefb69bc15f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736961"
---
# <a name="exception_state"></a>EXCEPTION_STATE
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
Pare na primeira exceção. Ao descrever um evento de exceção, esta bandeira indica que o evento de exceção é um evento de exceção de primeira chance.

`EXCEPTION_STOP_SECOND_CHANCE`\
Pare no segundo disparo de exceção. Ao descrever um evento de exceção, indica que o evento de exceção é um evento de exceção de segunda chance.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Pare na primeira demissão de uma exceção de modo de usuário. Ao descrever um evento de exceção, indica que o evento de exceção é um evento de exceção de primeira chance do usuário.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Pare quando uma exceção de modo de usuário não for capturada. Ao descrever um evento de exceção, indica que o evento de exceção é um evento de exceção do modo de usuário não capturado.

`EXCEPTION_STOP_ALL`\
Pare em qualquer exceção. Não usado ao descrever um evento de exceção.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Ao descrever um evento de exceção, indica que a exceção não pode ser continuada.

`EXCEPTION_CODE_SUPPORTED`\
Indica que a exceção tem código que o suporta. Usado na exibição de uma exceção

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Indica que o código de exceção deve ser exibido em hexadecimal. Usado na exibição de uma exceção.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Indica que o código de exceção suporta JustMyCode. Usado na exibição de uma exceção.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Indica que o depurador de código gerenciado deve lidar com exceções. Se não estiver definido, o depurador padrão lida com as exceções. Isso é passado para o método [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) e não é usado na estrutura [EXCEPTION_INFO.](../../../extensibility/debugger/reference/exception-info.md)

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
OBSOLETO, NÃO USE.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
OBSOLETO, NÃO USE.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
OBSOLETO, NÃO USE.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
OBSOLETO, NÃO USE.

## <a name="remarks"></a>Comentários
Usado como `dwState` membro da [estrutura EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) para indicar o estado da exceção e o que pode ser feito sobre ela.

Esses valores também são passados para o método [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) para definir o estado de todas as exceções.

Essas bandeiras podem ser combinadas com um pouco de OR.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
