---
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3f81168d9af7fbbb93b5c59f3ab19a17107b56b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734193"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Estende a interface [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) para permitir a recuperação de interfaces de módulo e processo.

## <a name="syntax"></a>Sintaxe

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Implementado por motores de depuração e consumido pelo pacote [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debug.

## <a name="methods"></a>Métodos
 Além dos métodos na `IDebugCodeContext2` interface, esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[Getmodule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera uma referência à interface do módulo de depuração.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera uma referência à interface do processo de depuração.|

## <a name="remarks"></a>Comentários
 Esta é uma interface opcional que geralmente não precisa ser implementada.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
