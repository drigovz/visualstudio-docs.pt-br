---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db9a7eae6a0a37f8bd1f530afe067f4766197591
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708557"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Essa interface do enumera os threads em execução na sessão de depuração atual.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O mecanismo de depuração (DES) implementa essa interface para representar uma lista de threads em um programa.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chame [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) para obter essa interface que representa uma lista de todos os threads em todos os programas em execução em um processo. Chame [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) para obter essa interface que representa uma lista de threads em execução em um programa.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IEnumDebugThreads2`.

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Recupera um número especificado de threads na sequência de enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Ignora um número especificado de threads em uma sequência de enumeração.|
|[Reiniciar](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Redefine uma sequência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Obtém o número de threads em um enumerador.|

## <a name="remarks"></a>Comentários
 Visual Studio geralmente obtém essa interface para atualizar o **Threads** janela, bem como para obter o primeiro thread da lista, para chamar [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md), e [Etapa](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Executar](../../../extensibility/debugger/reference/idebugprocess3-execute.md)