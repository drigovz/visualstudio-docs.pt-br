---
title: Controle de execução e avaliação de estado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6476c925f37d70ab45bae129a8b8a379ee519c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152765"
---
# <a name="execution-control-and-state-evaluation"></a>Controle de execução e avaliação de estado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A depuração de um aplicativo requer a implementação desses recursos de controle de execução como depuração em funções, parando em pontos de interrupção e continuando a execução. A depuração do Visual Studio baseia seu controle de execução em eventos enviados entre componentes do depurador.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Controle do programa](../../extensibility/debugger/program-control.md)  
 Lista as seguintes rotinas que ocorrem no nível do programa: definindo a próxima instrução, executando, percorrendo, continuando, suspendendo e retomando.  
  
 [Métodos relacionados ao ponto de interrupção](../../extensibility/debugger/breakpoint-related-methods.md)  
 Define os tipos associados e pendentes de pontos de interrupção aos quais o Visual Studio dá suporte.  
  
 [Avaliação de pilha de chamadas](../../extensibility/debugger/call-stack-evaluation.md)  
 Discute a implementação dos métodos que permitem a exibição dos quadros de pilha da pilha de chamadas durante o modo de interrupção.  
  
 [Avaliação de expressão](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Explica como o mecanismo de depuração (DE), a avaliação de expressão (EE) e o Gerenciador de depuração de sessão estão envolvidos na análise e na avaliação de uma expressão inserida em uma das janelas do IDE.  
  
 [Eventos de controle](../../extensibility/debugger/control-events.md)  
 Discute a interface usada para enviar eventos durante a execução controlada do programa.
