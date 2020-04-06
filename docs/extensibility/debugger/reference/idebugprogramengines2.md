---
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94df9acc6a0478ba2cb36022bc8618c69be97b8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722393"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Esta interface é usada por nós de programa para especificar todos os possíveis mecanismos de depuração (DE) que podem depurar este programa.

## <a name="syntax"></a>Sintaxe

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um dede ou um fornecedor de porta personalizado implementa essa interface no mesmo objeto que implementa [o IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para suportar o estabelecimento de um DE específico para usar em um programa específico.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para o `IDebugProgramNode2` [QueryInterface](/cpp/atl/queryinterface) em uma interface para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugProgramEngines2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Indica todos os possíveis DEs que podem depurar este programa.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Seleciona o DE para usar para depurar este programa.|

## <a name="remarks"></a>Comentários
 Uma vez que um DE é escolhido pelo usuário, essa escolha é registrada no nó do programa ligando para [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). O motor selecionado torna-se o motor retornado pelo [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
