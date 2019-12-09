---
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b45cbe8cd1b68e1681b07fcdf1fc715973a11295
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325258"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Essa interface é usada por nós de programa para especificar todos os possíveis depuração mecanismos (DES) que podem depurá-lo.

## <a name="syntax"></a>Sintaxe

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 A DE ou de um fornecedor de porta personalizada implementa essa interface no mesmo objeto que implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para dar suporte ao estabelecimento de uma DE específico a ser usado para um determinado programa.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chame [QueryInterface](/cpp/atl/queryinterface) em um `IDebugProgramNode2` interface para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDebugProgramEngines2`.

|Método|Descrição|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Indica o DEs possíveis que podem depurar este programa.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Seleciona o DE ser usado para depurar este programa.|

## <a name="remarks"></a>Comentários
 Depois que a DE é escolhida pelo usuário, essa opção está registrada com o nó de programa chamando [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). O mecanismo selecionado se tornará o mecanismo retornado por [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)