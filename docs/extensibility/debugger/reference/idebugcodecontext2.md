---
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e15692a94e3f1c80d6bd6f12ecb0c2ce7271c8d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692600"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Essa interface representa a posição inicial de uma instrução de código. Para a maioria das arquiteturas de tempo de execução atualmente, um contexto de código pode ser pensado como um endereço no fluxo de execução de um programa.

## <a name="syntax"></a>Sintaxe

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O mecanismo de depuração implementa essa interface para relacionar a posição de uma instrução de código para uma posição do documento.

## <a name="notes-for-callers"></a>Observações para chamadores
 Métodos em várias interfaces retornam essa interface, em geral, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Ele também é usado extensivamente com o [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) interface, bem como informações de resolução de ponto de interrupção.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Além dos métodos na [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interface, essa interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Obtém o contexto do documento que corresponde ao contexto de código ativo.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtém as informações de idioma para este contexto de código.|

## <a name="remarks"></a>Comentários
 A principal diferença entre um `IDebugCodeContext2` interface e uma [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interface é que um `IDebugCodeContext2` sempre é alinhado à instrução. Isso significa que um `IDebugCodeContext2` sempre está apontando para o início de uma instrução, enquanto um `IDebugMemoryContext2` podem apontar para qualquer byte de memória na arquitetura de tempo de execução. `IDebugCodeContext2` é incrementado por instruções em vez do tamanho de armazenamento básico (normalmente bytes).

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Avançar](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)