---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbbe047c08f8e91264163d028c1b40d94cde97fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715096"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Esta interface enumera os segmentos em execução na sessão de depuração atual.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa esta interface para representar uma lista de threads em um programa.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para [a EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) para obter esta interface representando uma lista de todos os threads em todos os programas em execução em um processo. Ligue para [a EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) para obter essa interface representando uma lista de threads em execução em um programa.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IEnumDebugThreads2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Recupera um número especificado de roscas na seqüência de enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Salta um número especificado de threads em uma seqüência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Reinicia uma seqüência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Obtém o número de fios em um enumerador.|

## <a name="remarks"></a>Comentários
 O Visual Studio normalmente obtém esta interface para atualizar a janela **Threads,** bem como para obter o primeiro segmento da lista, a fim de chamar [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)e [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Etapa](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Executar](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
