---
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 321004d1d0ef37597d477cff71435091a3123ccf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965636"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Estende o **IDebugTypeFieldBuilder** para poder criar tipos de matriz.

## <a name="syntax"></a>Sintaxe

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface pode ser obtida do provedor de símbolos.

## <a name="methods"></a>Métodos
 Além dos métodos na interface [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) , essa interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Cria uma matriz do tipo e do tamanho especificados.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
