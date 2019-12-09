---
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6123c6438defff596351fff3d1ba31ea52a19f28
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349933"
---
# <a name="parseflags"></a>PARSEFLAGS
Especifica como analisar uma expressão.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Campos
 `PARSE_EXPRESSION`\
 Indica que a expressão não é uma instrução.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Indica que a expressão deve ser analisado (e avaliado mais tarde) como um endereço.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Indica que a expressão está sendo analisada durante o tempo de design (ou seja, quando um designer estiver aberto).

## <a name="remarks"></a>Comentários
 Passado como um parâmetro para o [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e [analisar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) métodos.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Analisar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)