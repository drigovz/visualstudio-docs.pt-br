---
title: Controle de Execução e Avaliação do Estado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc76ae97e8baa6ce78dd4d565109d6a19e2051e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738747"
---
# <a name="execution-control-and-state-evaluation"></a>Controle de execução e avaliação do estado
A depuração de um aplicativo requer a implementação de tais recursos de controle de execução como entrar em funções, parar em pontos de interrupção e execução contínua. A depuração do Visual Studio baseia seu controle de execução em eventos enviados entre componentes de depurador.

## <a name="in-this-section"></a>Nesta seção
 [Controle do programa](../../extensibility/debugger/program-control.md) Lista as seguintes rotinas que ocorrem no nível do programa: definindo a próxima declaração, executando, pisando, continuando, suspendendo e retomando.

 [Métodos relacionados a pontos de ruptura](../../extensibility/debugger/breakpoint-related-methods.md) Define os tipos de pontos de interrupção vinculados e pendentes que o Visual Studio suporta.

 [Avaliação de pilha de chamadas](../../extensibility/debugger/call-stack-evaluation.md) Discute a implementação dos métodos que permitem a visualização dos quadros de pilha da pilha de chamadas durante o modo de pausa.

 [Avaliação de expressão](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Explica como o motor de depuração (DE), a avaliação de expressão (EE) e o gerenciador de depuração de sessão estão envolvidos na análise e avaliação de uma expressão inserida em uma das janelas do IDE.

 [Eventos de controle](../../extensibility/debugger/control-events.md) Discute a interface usada para enviar eventos durante a execução controlada do programa.
