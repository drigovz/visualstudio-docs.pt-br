---
title: Avaliação de Pilha de Chamadas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5557d7eae0ffe54b0f01f1f9e95935d71455229
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739184"
---
# <a name="call-stack-evaluation"></a>Avaliação de pilha de chamadas
Para visualizar os quadros de pilha da pilha de chamadas durante o modo de pausa, você deve implementar o método [EnumFrameInfo.](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

## <a name="methods-for-evaluation"></a>Métodos para avaliação
 Para um simples motor de depuração (DE), pode haver apenas um quadro de pilha. Para examinar o quadro de pilha durante o modo de quebra, você deve implementar os seguintes métodos do [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).

|Método|Descrição|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtém o contexto de código para um quadro de pilha. O contexto de código representa o ponteiro de instrução atual em um quadro de pilha.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtém o contexto do documento para um quadro de pilha. O contexto do documento representa a localização atual no código-fonte de um quadro de pilha. Necessário para visualizar o código fonte quando você é parado em um programa.|

 Esses métodos exigem a implementação de várias interfaces e métodos relacionados ao contexto. Assim, você deve implementar o método [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) e os seguintes métodos do [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).

|Método|Descrição|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtém o intervalo de declaração de arquivo de um contexto de documento.|

 Para enumerar contextos de código, você deve implementar todos os métodos do [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).

## <a name="see-also"></a>Confira também
- [Controle de execução e avaliação do estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
