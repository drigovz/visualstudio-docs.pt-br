---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1bdcbc4171c8a481ee0c45456ef5600f5150c6d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317577"
---
# <a name="getnametype"></a>GETNAME_TYPE
Especifica o tipo de nome de arquivos a serem recuperados.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>Campos
`GN_NAME`\
Especifica um nome amigável do documento ou do contexto.

`GN_FILENAME`\
Especifica o caminho completo do documento ou do contexto.

`GN_BASENAME`\
Especifica um nome de arquivo base, em vez de um caminho completo do documento ou do contexto.

`GN_MONIKERNAME`\
Especifica um nome exclusivo do documento ou no contexto na forma de um moniker.

`GN_URL`\
Especifica um nome de URL do documento ou do contexto.

`GN_TITLE`\
Especifica um título do documento, se houver.

`GN_STARTPAGEURL`\
Obtém a URL da página inicial para processos.

## <a name="remarks"></a>Comentários
Esses valores são passados como parâmetros para o [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), e [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) métodos para especificar que tipo de nome a ser retornado.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
