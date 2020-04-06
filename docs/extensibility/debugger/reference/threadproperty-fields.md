---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b31c43187d1136f7a194c42749c430de6cd064a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713406"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Especifica quais informações sobre um segmento devem ser recuperadas.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Campos
 `TPF_ID`\
 Inicializar/usar `dwThreadId` o campo da estrutura [THREADPROPERTIES.](../../../extensibility/debugger/reference/threadproperties.md)

 `TPF_SUSPENDCOUNT`\
 Inicializar/usar `dwSuspendCount` o campo `THREADPROPERTIE`da estrutura S.

 `TPF_STATE`\
 Inicializar/usar `dwThreadState` o campo `THREADPROPERTIE`da estrutura S.

 `TPF_PRIORITY`\
 Inicializar/usar `bstrPriority` o campo `THREADPROPERTIE`da estrutura S.

 `TPF_NAME`\
 Inicializar/usar `bstrName` o campo `THREADPROPERTIE`da estrutura S.

 `TPF_LOCATION`\
 Inicializar/usar `bstrLocation` o campo `THREADPROPERTIE`da estrutura S.

 `TPF_ALLFIELDS`\
 Especifica todos os campos.

## <a name="remarks"></a>Comentários
 Esses valores são passados como um argumento para o método [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) para indicar quais campos da estrutura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) devem ser inicializados.

 Esses valores também `dwFields` são `THREADPROPERTIES` utilizados em membros da estrutura para indicar quais campos são usados e válidos.

 Essas bandeiras podem ser combinadas com um pouco `OR`.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
