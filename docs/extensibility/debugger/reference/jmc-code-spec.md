---
title: JMC_CODE_SPEC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab69cdaa450ffd083aca25de1cab038a4b891baa
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56449589"
---
# <a name="jmccodespec"></a>JMC_CODE_SPEC
Essa estrutura é usada para definir as informações de JustMyCode para um módulo.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _JMC_CODE_SPEC {
    BOOL fIsUserCode;
    BSTR bstrModuleName;
} JMC_CODE_SPEC;
```

```csharp
public struct JMC_CODE_SPEC {
    public int    fIsUserCode;
    public string bstrModuleName;
};
```

## <a name="members"></a>Membros
fIsUserCode diferente de zero (`TRUE`) se o módulo seja considerado código de usuário; caso contrário, zero (`FALSE`) se o módulo for sejam tratados como código externo e não a ser depurado.

bstrModuleName nome do módulo em questão.

## <a name="remarks"></a>Comentários
Essa estrutura é passada como uma lista dessas estruturas para o [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) método.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
[Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)  
[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
