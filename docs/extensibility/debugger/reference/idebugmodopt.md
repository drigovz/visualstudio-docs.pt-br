---
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1bbfbc6b6e567e0e56aa369f9c0d1f13a4cbe34
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918628"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Representa um modificador opcional de depuração.

## <a name="syntax"></a>Sintaxe

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Observações para chamadores
 Obtido de um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa uma classe ou método.

## <a name="methods"></a>Métodos
 Essa interface implementa o método a seguir:

|Método|Descrição|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Recupera uma lista de modificadores opcionais.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll