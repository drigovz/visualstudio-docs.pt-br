---
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 14bcfb7498ad22156ae18998ebe5958aad1b9026
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928751"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Estende a interface [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) para habilitar a recuperação de interfaces de módulo e de processo.

## <a name="syntax"></a>Sintaxe

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Implementado por mecanismos de depuração e consumido pelo [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pacote de depuração.

## <a name="methods"></a>Métodos
 Além dos métodos na `IDebugCodeContext2` interface, essa interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera uma referência à interface do módulo de depuração.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera uma referência à interface do processo de depuração.|

## <a name="remarks"></a>Comentários
 Essa é uma interface opcional que geralmente não precisa ser implementada.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
