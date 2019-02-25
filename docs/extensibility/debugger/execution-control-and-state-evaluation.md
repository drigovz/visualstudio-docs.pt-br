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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd04cfa1e271f94f1b37aa0fbd62e9b846d9a70d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714680"
---
# <a name="execution-control-and-state-evaluation"></a>Avaliação de controle e o estado de execução
Depurando um aplicativo requer a implementação de recursos de controle, execução, como entrar em funções, parando em pontos de interrupção e continuando a execução. Bases de depuração do Visual Studio seu controle de execução em eventos enviados entre os componentes do depurador.

## <a name="in-this-section"></a>Nesta seção
 [Controle do programa](../../extensibility/debugger/program-control.md) lista as seguintes rotinas que ocorrem no nível do programa: definir a próxima instrução, executando, passo a passo, continuando, suspender e retomar.

 [Métodos relacionados ao ponto de interrupção](../../extensibility/debugger/breakpoint-related-methods.md) define o limite e pendentes tipos de pontos de interrupção que dá suporte ao Visual Studio.

 [Avaliação de pilha de chamada](../../extensibility/debugger/call-stack-evaluation.md) aborda a implementação dos métodos que permitem a visualização dos quadros de pilhas da pilha de chamadas durante o modo de interrupção.

 [Avaliação de expressão](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) explica como o mecanismo de depuração (DE), a avaliação de expressão (EE) e o Gerenciador de sessão de depuração estão envolvidos na análise e avaliação de uma expressão inserida em uma das janelas do IDE.

 [Controlar eventos](../../extensibility/debugger/control-events.md) aborda a interface usada para enviar eventos durante a execução controlada do programa.