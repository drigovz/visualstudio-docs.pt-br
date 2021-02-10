---
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67a94f3f88d85d1e74ce7b1d67e1ef3d44546132
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965688"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Representa a capacidade de criar um campo que representa um tipo.

## <a name="syntax"></a>Sintaxe

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é obtida do provedor de símbolos.

## <a name="methods"></a>Métodos
 Essa interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Cria um objeto que representa um tipo primitivo.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Cria um ponteiro para o tipo especificado.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
