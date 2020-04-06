---
title: IDebugStackFrame2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37acb9f2984c36130de494108ef4b76a59cc74e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719515"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Esta interface representa um único quadro de pilha em uma pilha de chamadas em um segmento específico.

## <a name="syntax"></a>Sintaxe

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa esta interface para representar um quadro de pilha.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para [enumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para recuperar uma interface [IEnumDebugFrameInfo2.](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) Ligue ao [lado](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) para recuperar uma `IDebugStackFrame2` estrutura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) que contenha a interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugStackFrame2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtém o contexto de código para este quadro de pilha.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtém o contexto do documento para este quadro de pilha.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Recebe o nome da moldura da pilha.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Obtém uma descrição do quadro da pilha.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Obtém uma representação dependente da máquina da gama de endereços físicos associados a um quadro de pilha.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Obtém um contexto de avaliação para fazer avaliação de expressão dentro do contexto atual de um quadro de pilha e segmento.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Obtém a linguagem associada a um quadro de pilha.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Obtém uma descrição das propriedades associadas a um quadro de pilha.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Cria um enumerador para propriedades de quadro de pilha.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Obtém o fio associado a um quadro de pilha.|

## <a name="remarks"></a>Comentários
 Esta interface só é obtida quando o programa que está sendo depurado foi interrompido em um ponto de ruptura (seja causado por um ponto de ruptura definido pelo usuário ou por uma exceção). A partir desta interface, um contexto de expressão pode ser obtido para avaliar expressões, uma lista de registros pode ser devolvida ou a pilha de chamadas pode ser obtida e examinada.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
