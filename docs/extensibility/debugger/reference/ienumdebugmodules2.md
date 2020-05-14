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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 612285aa4d5a249c0f922ccae88d98a7df83187b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716438"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Esta interface enumera uma lista de módulos.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa esta interface para representar uma lista de módulos carregados para um programa.

## <a name="notes-for-callers"></a>Observações para chamadores
 O Visual Studio chama [enumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) para obter esta interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IEnumDebugModules2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Recupera um número especificado de módulos em uma seqüência de enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Salta um número especificado de módulos em uma seqüência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Reinicia uma seqüência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Obtém o número de módulos.|

## <a name="remarks"></a>Comentários
 O Visual Studio usa esta interface principalmente para atualizar a janela **Módulos.**

 Para efeitos de depuração no Visual Studio, um programa é uma seqüência lógica de instruções de código que podem cruzar os limites do módulo, daí a necessidade de uma lista de módulos para uma única interface [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md) O primeiro módulo da lista normalmente contém o ponto de entrada inicial para o programa associado.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
