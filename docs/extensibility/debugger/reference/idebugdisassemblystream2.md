---
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 352d0c71151a7c99822f5ad9f15250c47541fb19
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705814"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Essa interface representa um fluxo de instruções.

## <a name="syntax"></a>Sintaxe

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um mecanismo de depuração implementa essa interface para dar suporte a desmontagem do código do programa.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma chamada para o [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) método retorna essa interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDebugDisassemblyStream2`.

|Método|Descrição|
|------------|-----------------|
|[Ler](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Lê a partir da posição atual no fluxo de desmontagem de instruções.|
|[Buscar](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Move o ponteiro de leitura no fluxo de desmontagem um determinado número de instruções em relação a uma posição especificada.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Retorna um identificador de local de código para um contexto de código em particular.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Retorna um objeto de contexto de código correspondente a um identificador de local de código especificada.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Retorna um identificador de local do código que representa o local atual do código.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Obtém o documento de origem associado a este fluxo de desmontagem.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Obtém o escopo deste fluxo de desmontagem.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Obtém o tamanho deste fluxo de desmontagem.|

## <a name="remarks"></a>Comentários
 O fluxo de desmontagem pode ser criado para representar o espaço de endereço inteiro ou apenas uma função ou módulo dentro do espaço. Cada instrução é representada por um [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estrutura retornada por uma chamada para o [leitura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)