---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 54bb93fa6f88c02731691728bceacdd4a5fe2036
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694342"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Especifica as informações a serem recuperadas sobre um objeto de quadro de pilha.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="members"></a>Membros
FIF_FUNCNAME Initialize/usar o `m_bstrFuncName` campo.

FIF_RETURNTYPE Initialize/usar o `m_bstrReturnType` campo.

FIF_ARGS Initialize/usar o `m_bstrArgs` campo.

FIF_LANGUAGE Initialize/usar o `m_bstrLanguage` campo.

FIF_MODULE Initialize/usar o `m_bstrModule` campo.

FIF_STACKRANGE Initialize/usar o `m_addrMin` e `m_addrMax` campos (intervalo de pilha).

FIF_FRAME Initialize/usar o `m_pFrame` campo.

FIF_DEBUGINFO Initialize/usar o `m_fHasDebugInfo` campo.

FIF_STALECODE Initialize/usar o `m_fStaleCode` campo.

FIF_ANNOTATEDFRAME Initialize/usar o `m_fAnnotatedFrame` campo.

FIF_DEBUG_MODULEP Initialize/usar o `m_pModule` campo.

FIF_FUNCNAME_FORMAT formata o nome da função. O resultado é retornado no `m_bstrFunName` campo e não outros campos são preenchidos.

FIF_FUNCNAME_RETURNTYPE adiciona o tipo de retorno para o `m_bstrFuncName` campo.

FIF_FUNCNAME_ARGS adiciona os argumentos para o `m_bstrFuncName` campo.

FIF_FUNCNAME_LANGUAGE adiciona o idioma para o `m_bstrFuncName` campo.

FIF_FUNCNAME_MODULE adiciona o nome do módulo para o `m_bstrFuncName` campo.

FIF_FUNCNAME_LINES adiciona o número de linhas para o `m_bstrFuncName` campo.

FIF_FUNCNAME_OFFSET adiciona para o `m_bstrFuncName` campo o deslocamento em bytes desde o início da linha se `FIF_FUNCNAME_LINES` for especificado. Se `FIF_FUNCNAME_LINES` não for especificado, ou se os números de linha não estiverem disponíveis, adiciona o deslocamento em bytes desde o início da função.

FIF_FUNCNAME_ARGS_TYPES adiciona o tipo de cada argumento de função para o `m_bstrFuncName` campo.

FIF_FUNCNAME_ARGS_NAMES adiciona o nome de cada argumento de função para o `m_bstrFuncName` campo.

FIF_FUNCNAME_ARGS_VALUES adiciona o valor de cada argumento de função para o `m_bstrFuncName` campo.

FIF_FUNCNAME_ARGS_ALL adiciona o tipo, nome e valor de todos os argumentos para o `m_bstrFuncName` campo.

FIF_ARGS_TYPES os tipos de argumento são recuperados e formatados.

FIF_ARGS_NAMES os nomes de argumento são recuperados e formatados.

FIF_ARGS_VALUES os valores de argumento são recuperados e formatados.

Recuperar FIF_ARGS_ALL e o tipo de formato, nome e valor de todos os argumentos.

Não FIF_ARGS_NOFORMAT Especifica que os argumentos são formatados (por exemplo, não adicione abrindo e fechando a lista de argumentos entre parênteses nem adicionar um separador entre argumentos).

FIF_ARGS_NO_FUNC_EVAL Especifica que a função de avaliação (propriedade) não deve ser usado ao recuperar valores de argumento.

FIF_FILTER_NON_USER_CODE o mecanismo de depuração é filtrar quadros de código de não usuário para que eles não estão incluídos.

FIF_ARGS_NO_TOSTRING não permitir `ToString()` formatação ao retornar os argumentos de função ou avaliação de função.

Informações de quadro FIF_DESIGN_TIME_EXPR_EVAL devem ser obtidas de domínio de aplicativo hospedado em vez do processo de hospedagem.

## <a name="remarks"></a>Comentários
Esses sinalizadores são passados para o [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) e [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) métodos para indicar quais campos devem ser inicializados no [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estrutura ou estruturas.

Esses sinalizadores também são usados para indicar quais campos do [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estrutura são usados e válidos quando a estrutura é retornada. Esses valores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
