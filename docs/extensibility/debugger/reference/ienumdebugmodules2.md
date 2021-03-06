---
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dfcd594ab8764cedb8cbe2ea312675f884ae2338
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957147"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Essa interface enumera uma lista de módulos.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface para representar uma lista de módulos carregados para um programa.

## <a name="notes-for-callers"></a>Observações para chamadores
 O Visual Studio chama [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 A tabela a seguir mostra os métodos de `IEnumDebugModules2` .

|Método|Descrição|
|------------|-----------------|
|[Próximo](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Recupera um número especificado de módulos em uma sequência de enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Ignora um número especificado de módulos em uma sequência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Redefine uma sequência de enumeração para o início.|
|[8i](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Obtém o número de módulos.|

## <a name="remarks"></a>Comentários
 O Visual Studio usa essa interface principalmente para atualizar a janela de **módulos** .

 Para fins de depuração no Visual Studio, um programa é uma sequência lógica de instruções de código que podem cruzar os limites do módulo, portanto, a necessidade de uma lista de módulos para uma única interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . O primeiro módulo na lista normalmente contém o ponto de entrada inicial para o programa associado.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
