---
title: Controle de execução e avaliação de estado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a90f1fa098cfb60e6a3939332095dca5e52e3eb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852093"
---
# <a name="execution-control-and-state-evaluation"></a>Avaliação de controle e o estado de execução
Depurando um aplicativo requer a implementação de recursos de controle, execução, como entrar em funções, parando em pontos de interrupção e continuando a execução. Bases de depuração do Visual Studio seu controle de execução em eventos enviados entre os componentes do depurador.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Controle do programa](../../extensibility/debugger/program-control.md)  
 Lista as seguintes rotinas que ocorrem no nível do programa: definir a próxima instrução, executando, passo a passo, continuando, suspender e retomar.  
  
 [Métodos relacionados ao ponto de interrupção](../../extensibility/debugger/breakpoint-related-methods.md)  
 Define o limite e pendentes tipos de pontos de interrupção que dá suporte ao Visual Studio.  
  
 [Avaliação de pilha de chamadas](../../extensibility/debugger/call-stack-evaluation.md)  
 Discute a implementação dos métodos que permitem a visualização dos quadros de pilhas da pilha de chamadas durante o modo de interrupção.  
  
 [Avaliação de expressão](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Explica como o mecanismo de depuração (DE), Gerenciador de depuração de avaliação (EE) e a sessão de expressões estão envolvidos na análise de e avaliação de uma expressão inserida em uma das janelas do IDE.  
  
 [Eventos de controle](../../extensibility/debugger/control-events.md)  
 Discute a interface usada para enviar eventos durante a execução controlada do programa.