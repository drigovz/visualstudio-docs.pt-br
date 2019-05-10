---
title: STEPKIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa9c1805c7eaba480cd46ebc6e73ee370e3cbb22
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460780"
---
# <a name="stepkind"></a>STEPKIND
Especifica o tipo de etapa de passo a passo.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
typedef DWORD STEPKIND;
```

```csharp
public enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
```

## <a name="fields"></a>Campos
 `STEP_INTO`\
 Etapas em uma função.

 `STEP_OVER`\
 Etapas em uma função.

 `STEP_OUT`\
 Etapas de uma função.

 `STEP_BACKWARDS`\
 Etapas para trás em uma função.

## <a name="remarks"></a>Comentários
 Passado como um argumento para o [etapa](../../../extensibility/debugger/reference/idebugprocess3-step.md) método.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)