---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f81709e7146bbdef13daa3564bb784fd9c08d58e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714007"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Especificou que tipo de informação recuperar para um processo.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>Campos
 `PIF_FILE_NAME`\
 Inicializar/utilizar `bstrFileName` o campo da estrutura [PROCESS_INFO.](../../../extensibility/debugger/reference/process-info.md)

 `PIF_BASE_NAME`\
 Inicializar/utilizar `bstrBaseName` o campo `PROCESS_INFO` da estrutura.

 `PIF_TITLE`\
 Inicializar/utilizar `bstrTitle` o campo `PROCESS_INFO` da estrutura.

 `PIF_PROCESS_ID`\
 Inicializar/utilizar `ProcessId` o campo `PROCESS_INFO` da estrutura.

 `PIF_SESSION_ID`\
 Inicializar/utilizar `dwSessionId` o campo `PROCESS_INFO` da estrutura.

 `PIF_ATTACHED_SESSION_NAME`\
 Inicializar/utilizar `bstrAttachedSessionName` o campo `PROCESS_INFO` da estrutura.

 `PIF_CREATION_TIME`\
 Inicializar/utilizar `CreationTime` o campo `PROCESS_INFO` da estrutura.

 `PIF_FLAGS`\
 Inicializar/utilizar `Flags` o campo `PROCESS_INFO` da estrutura.

 `PIF_ALL`\
 Preenche todos os campos.

## <a name="remarks"></a>Comentários
 Passado para o método [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) para indicar quais campos da estrutura [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) devem ser inicializados.

 Também utilizado `Fields` no `PROCESS_INFO` campo da estrutura para indicar quais campos são usados e válidos.

 Essas bandeiras podem ser combinadas com um pouco `OR`.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
