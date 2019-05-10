---
title: SEEK_START | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 341b321b529bc1359ba576cc26ec20cc99e96cb3
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458390"
---
# <a name="seekstart"></a>SEEK_START
Especifica a posição da qual iniciar a busca em um fluxo de desmontagem.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>Campos
 `SEEK_START_BEGIN`\
 Inicia a busca no início do documento atual.

 `SEEK_START_END`\
 Inicia a busca no final do documento atual.

 `SEEK_START_CURRENT`\
 Inicia a busca da posição atual do documento atual.

 `SEEK_START_CODECONTEXT`\
 Inicia a busca no contexto do código fornecido do documento atual.

 `SEEK_START_CODELOCID`\
 Inicia a busca no identificador de local de código fornecida. Identificadores de local de código são obtidos chamando [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).

## <a name="remarks"></a>Comentários
 Passado como um argumento para o [busca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) método.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Buscar](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)