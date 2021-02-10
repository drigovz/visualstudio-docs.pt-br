---
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c90e63e8ea7b00ff7d342ef6b1a0e624779e13d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965597"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Permite consultar informações sobre o computador de destino.

## <a name="syntax"></a>Sintaxe

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Essa interface é implementada por objetos de porta do Gerenciador de depuração de sessão.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugWindowsComputerPort2` .

|Método|Descrição|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Recupera informações sobre o computador no qual o depurador está em execução.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
