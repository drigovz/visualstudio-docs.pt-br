---
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed34284e373a7d96761aabe5a7f179367649bc0f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718307"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Estende o **IDebugTypeFieldBuilder** para poder criar tipos de array.

## <a name="syntax"></a>Sintaxe

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Observações para chamadores
 Esta interface pode ser obtida do provedor de símbolos.

## <a name="methods"></a>Métodos
 Além dos métodos na interface [IDebugTypeFieldBuilder,](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) esta interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Cria uma matriz do tipo e tamanho especificados.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
