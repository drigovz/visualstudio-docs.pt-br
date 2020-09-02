---
title: Avaliação da pilha de chamadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 15fecbc61fec8ba7aa62ca7d79cf11c56b7ce938
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146411"
---
# <a name="call-stack-evaluation"></a>Avaliação de pilha de chamadas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para exibir os quadros de pilha da pilha de chamadas durante o modo de interrupção, você deve implementar o método [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .  
  
## <a name="methods-for-evaluation"></a>Métodos para avaliação  
 Para um mecanismo DE depuração simples (DE), pode haver apenas um quadro de pilha. Para examinar o quadro de pilhas durante o modo de interrupção, você deve implementar os seguintes métodos de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtém o contexto do código para um registro de ativação. O contexto de código representa o ponteiro de instrução atual em um registro de ativação.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtém o contexto do documento para um quadro de pilha. O contexto do documento representa o local atual no código-fonte de um registro de ativação. Necessário para exibir o código-fonte quando você está parado em um programa.|  
  
 Esses métodos exigem a implementação de várias interfaces e métodos relacionados ao contexto. Portanto, você deve implementar o método [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) e os seguintes métodos de [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtém o intervalo de instruções de arquivo de um contexto de documento.|  
  
 Para enumerar contextos de código, você deve implementar todos os métodos de [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
