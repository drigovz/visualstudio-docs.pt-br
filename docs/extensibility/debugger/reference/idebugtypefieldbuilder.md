---
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81532e2616eefb9cb584eae1a70371fd2f963be1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718387"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Representa a capacidade de criar um campo que representa um tipo.

## <a name="syntax"></a>Sintaxe

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Observações para chamadores
 Esta interface é obtida do provedor de símbolos.

## <a name="methods"></a>Métodos
 Esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Cria um objeto que representa um tipo primitivo.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Cria um ponteiro para o tipo especificado.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
