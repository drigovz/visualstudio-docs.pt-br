---
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca871d9dac2b6f37018af925eece5c1a6f3d1585
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738129"
---
# <a name="attach_reason"></a>ATTACH_REASON
Especifica o motivo para o mecanismo de depuração (DE) ser anexado a um nó de programa.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
typedef DWORD ATTACH_REASON;
```

```csharp
public enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
```

## <a name="fields"></a>Campos
`ATTACH_REASON_AUTO`\
Conecte-se porque o processo está atualmente no modo de depuração.

`ATTACH_REASON_LAUNCH`\
Anexe porque o processo foi iniciado.

`ATTACH_REASON_USER`\
Anexar por causa de uma solicitação do usuário.

## <a name="remarks"></a>Comentários
Esses valores são usados como parâmetro para os métodos [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md) e [Anexar.](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
