---
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5ad1f7a3f954116350e8accbdc9db02d0ac920d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319604"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Essa interface representa uma lista de caminhos de código.

## <a name="syntax"></a>Sintaxe

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O mecanismo de depuração (DES) implementa essa interface para representar uma lista de caminhos de código.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chame [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IEnumCodePaths2`.

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Recupera um número especificado de caminhos de código em uma sequência de enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Ignora um número especificado de caminhos de código em uma sequência de enumeração.|
|[Reiniciar](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Redefine uma sequência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Obtém o número de caminhos de código em um enumerador.|

## <a name="remarks"></a>Comentários
 Um caminho de código representa uma chamada de função ou o ponto de ramificação em um programa. Uma lista de caminhos de código representa o caminho por meio do qual assumiu a execução do código.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)