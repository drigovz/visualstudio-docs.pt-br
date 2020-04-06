---
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 778602cc29049d855c418fd8fa416feb1ad8e9fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734218"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Esta interface representa a posição inicial de uma instrução de código. Para a maioria das arquiteturas em tempo de execução hoje, um contexto de código pode ser pensado como um endereço no fluxo de execução de um programa.

## <a name="syntax"></a>Sintaxe

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração implementa esta interface para relacionar a posição de uma instrução de código a uma posição de documento.

## <a name="notes-for-callers"></a>Observações para chamadores
 Métodos em muitas interfaces retornam essa interface, mais tipicamente, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Ele também é usado extensivamente com a interface [IDebugDisassemblyStream2,](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) bem como em informações de resolução de breakpoint.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos na interface [IDebugMemoryContext2,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Obtém o contexto do documento que corresponde ao contexto do código ativo.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtém as informações do idioma para este contexto de código.|

## <a name="remarks"></a>Comentários
 A principal diferença `IDebugCodeContext2` entre uma interface e uma interface `IDebugCodeContext2` [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) é que uma está sempre alinhada com instruções. Isso significa `IDebugCodeContext2` que um está sempre apontando para o `IDebugMemoryContext2` início de uma instrução, enquanto um pode apontar para qualquer byte de memória na arquitetura de tempo de execução. `IDebugCodeContext2`é incrementado por instruções e não pelo tamanho básico de armazenamento (tipicamente byte).

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Avançar](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
