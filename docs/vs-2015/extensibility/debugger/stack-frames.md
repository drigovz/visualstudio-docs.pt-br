---
title: Quadros de pilhas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3050e89db2f5cbb138f3d358b10c7cd936c560e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423381"
---
# <a name="stack-frames"></a>Quadros de pilhas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em termos da arquitetura do depurador, um registro de **ativação**:  
  
- É uma abstração de uma pilha que fornece o contexto de execução de um thread. Um thread sempre é executado dentro de uma função. Um registro de ativação contém as variáveis locais da função e os argumentos para ela. Para depurar com o Visual Studio, a linguagem ou o ambiente que está sendo depurado deve dar suporte a quadros de pilha.  
  
- Pode identificar e descrever a si mesmo e pode retornar o thread associado. Um quadro de pilha também pode retornar o contexto de código que representa o ponteiro de instrução atual, bem como os contextos de avaliação de documentação e expressão associados.  
  
- Tem propriedades que descrevem o nome, o tipo e o valor de variáveis e argumentos locais, e que aparecem em várias janelas de depuração do IDE.  
  
- É representado por uma interface [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , normalmente criada por um mecanismo de depuração (de) ou máquina virtual como consequência da execução de um thread.  
  
## <a name="see-also"></a>Consulte Também  
 [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
