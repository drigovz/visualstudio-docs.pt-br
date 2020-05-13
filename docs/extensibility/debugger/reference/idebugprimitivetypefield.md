---
title: IDebugPrimitiveTypeField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07cd3d1a1f80d1c5e816877b7e70a9e65d24d650
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724275"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Representa um valor de enumeração do tipo primitivo a partir de uma interface [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Sintaxe

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>Métodos
 Além dos métodos na interface [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) esta interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Recupera o tipo primitivo associado a este campo.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
