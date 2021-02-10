---
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0aff72199b6b79f2cca30e99533311ac617816b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941769"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Representa um modificador opcional de depuração.

## <a name="syntax"></a>Sintaxe

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Observações para chamadores
 Obtido de um objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa uma classe ou um método.

## <a name="methods"></a>Métodos
 Essa interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Recupera uma lista de modificadores opcionais.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
