---
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e142ed1229f59cfc22ff33cba48e9e35eb4e4406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726986"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Representa um modificador opcional de depuração.

## <a name="syntax"></a>Sintaxe

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Observações para chamadores
 Obtido a partir de um objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa uma classe ou método.

## <a name="methods"></a>Métodos
 Esta interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Recupera uma lista de modificadores opcionais.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
