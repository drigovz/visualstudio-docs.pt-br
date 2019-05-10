---
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 548bcd0328f7bdf52e47eb9a4295168ca47a2517
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226697"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Essa interface enumera uma lista de módulos.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O mecanismo de depuração (DES) implementa essa interface para representar uma lista de módulos carregados para um programa.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chamadas do Visual Studio [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IEnumDebugModules2`.

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Recupera um número especificado de módulos em uma sequência de enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Ignora um número especificado de módulos em uma sequência de enumeração.|
|[Reiniciar](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Redefine uma sequência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Obtém o número de módulos.|

## <a name="remarks"></a>Comentários
 O Visual Studio usa essa interface principalmente para atualizar o **módulos** janela.

 Para fins de depuração no Visual Studio, um programa é uma sequência lógica de instruções de código que pode cruzar os limites do módulo, portanto, a necessidade de uma lista de módulos para uma única [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface. O primeiro módulo na lista normalmente contém o ponto de entrada inicial para o programa associado.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)