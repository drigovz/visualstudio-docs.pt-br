---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3510726400623c5ddf3e7a4d58a4903763b91245
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736801"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
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

## <a name="fields"></a>Campos
`FIF_FUNCNAME`\
Inicializar/usar `m_bstrFuncName` o campo.

`FIF_RETURNTYPE`\
Inicializar/usar `m_bstrReturnType` o campo.

`FIF_ARGS`\
Inicializar/usar `m_bstrArgs` o campo.

`FIF_LANGUAGE`\
Inicializar/usar `m_bstrLanguage` o campo.

`FIF_MODULE`\
Inicializar/usar `m_bstrModule` o campo.

`FIF_STACKRANGE`\
Inicializar/usar `m_addrMin` os `m_addrMax` campos e (intervalo de pilha).

`FIF_FRAME`\
Inicializar/usar `m_pFrame` o campo.

`FIF_DEBUGINFO`\
Inicializar/usar `m_fHasDebugInfo` o campo.

`FIF_STALECODE`\
Inicializar/usar `m_fStaleCode` o campo.

`FIF_ANNOTATEDFRAME`\
Inicializar/usar `m_fAnnotatedFrame` o campo.

`FIF_DEBUG_MODULEP`\
Inicializar/usar `m_pModule` o campo.

`FIF_FUNCNAME_FORMAT`\
Formata o nome da função. O resultado é devolvido `m_bstrFunName` no campo e nenhum outro campo é preenchido.

`FIF_FUNCNAME_RETURNTYPE`\
Adiciona o tipo `m_bstrFuncName` de retorno ao campo.

`FIF_FUNCNAME_ARGS`\
Adiciona os argumentos `m_bstrFuncName` ao campo.

`FIF_FUNCNAME_LANGUAGE`\
Adiciona a linguagem `m_bstrFuncName` ao campo.

`FIF_FUNCNAME_MODULE`\
Adiciona o nome `m_bstrFuncName` do módulo ao campo.

`FIF_FUNCNAME_LINES`\
Adiciona o número de `m_bstrFuncName` linhas ao campo.

`FIF_FUNCNAME_OFFSET`\
Adiciona ao `m_bstrFuncName` campo o deslocamento em bytes desde `FIF_FUNCNAME_LINES` o início da linha, se for especificado. Se `FIF_FUNCNAME_LINES` não for especificado ou se os números de linha não estiverem disponíveis, adicione o deslocamento em bytes desde o início da função.

`FIF_FUNCNAME_ARGS_TYPES`\
Adiciona o tipo de argumento `m_bstrFuncName` de cada função ao campo.

`FIF_FUNCNAME_ARGS_NAMES`\
Adiciona o nome de cada `m_bstrFuncName` argumento de função ao campo.

`FIF_FUNCNAME_ARGS_VALUES`\
Adiciona o valor de cada `m_bstrFuncName` argumento de função ao campo.

`FIF_FUNCNAME_ARGS_ALL`\
Adiciona o tipo, nome e valor de `m_bstrFuncName` todos os argumentos ao campo.

`FIF_ARGS_TYPES`\
Os tipos de argumento são recuperados e formatados.

`FIF_ARGS_NAMES`\
Os nomes dos argumentos são recuperados e formatados.

`FIF_ARGS_VALUES`\
Os valores do argumento são recuperados e formatados.

`FIF_ARGS_ALL`\
Recupere e forme o tipo, nome e valor de todos os argumentos.

`FIF_ARGS_NOFORMAT`\
Especifica que os argumentos não estão formatados (por exemplo, não adicione parênteses de abertura e fechamento em torno da lista de argumentos nem adicione um separador entre argumentos).

`FIF_ARGS_NO_FUNC_EVAL`\
Especifica que a avaliação de função (propriedade) não deve ser usada ao recuperar valores de argumento.

`FIF_FILTER_NON_USER_CODE`\
O mecanismo de depuração é filtrar quadros de código não-usuários para que eles não sejam incluídos.

`FIF_ARGS_NO_TOSTRING`\
Não permita `ToString()` a avaliação ou formatação da função ao retornar argumentos de função.

`FIF_DESIGN_TIME_EXPR_EVAL`\
As informações do quadro devem ser obtidas do domínio do aplicativo hospedado em vez do processo de hospedagem.

## <a name="remarks"></a>Comentários
Esses sinalizadores são passados para os métodos [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) e [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) para indicar quais campos devem ser inicializados na estrutura ou estruturas [frameinfo.](../../../extensibility/debugger/reference/frameinfo.md)

Essas bandeiras também são usadas para indicar quais campos da estrutura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) são usados e válidos quando a estrutura é devolvida. Esses valores podem ser combinados com um pouco `OR`.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
