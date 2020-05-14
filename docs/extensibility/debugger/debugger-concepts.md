---
title: Conceitos de depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ad8a450f9e79c1d44b8e098c8a00bb4b816e1af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738988"
---
# <a name="debugger-concepts"></a>Conceitos de depurador
Para construir sobre o pacote de depuração do Visual Studio, você precisa estar familiarizado com os conceitos arquitetônicos usados na concepção do pacote.

## <a name="in-this-section"></a>Nesta seção
 [Sessão de depuração](../../extensibility/debugger/debug-session.md) Explica o papel de uma sessão na arquitetura de depuração.

 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md) Define o que é um servidor em termos de arquitetura de depuração, tanto em termos abstratos quanto físicos.

 [Fornecedores portuários](../../extensibility/debugger/port-suppliers.md) Define o que é um fornecedor de portas em termos de arquitetura de depuração.

 [Portos](../../extensibility/debugger/ports.md) Define o que é uma porta em termos de arquitetura de depuração.

 [Processos](../../extensibility/debugger/processes.md) Define o que é um processo em termos de arquitetura de depuração.

 [Nódulos do programa](../../extensibility/debugger/program-nodes.md) Define um nó de programa em termos de arquitetura de depuração, incluindo como ele pode se identificar e o processo em que está sendo executado.

 [Programas](../../extensibility/debugger/programs.md) Define um programa em termos de arquitetura de depuração.

 [Linhas](../../extensibility/debugger/threads.md) Define as características dos segmentos em termos de arquitetura de depuração.

 [Quadros de pilha](../../extensibility/debugger/stack-frames.md) Define um quadro de pilha em termos de arquitetura de depuração. Um quadro de pilha é uma abstração de uma pilha que fornece o contexto de execução de um segmento.

 [Módulos](../../extensibility/debugger/modules.md) Define um módulo, em termos de arquitetura de depuração, como um recipiente físico de código, como um arquivo executável ou um DLL.

 [Pontos de interrupção](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Define os três tipos de pontos de interrupção — pendentes, vinculados e erros — em termos de arquitetura de depuração.

## <a name="related-sections"></a>Seções relacionadas
 [Contextos de depuração](../../extensibility/debugger/debugger-contexts.md) Explica como o mecanismo de depuração (DE) opera simultaneamente dentro dos contextos de avaliação de código, documentação e expressão. Descreve, para cada um dos três contextos, a localização, posição ou avaliação relevantes para ele.

 [Componentes do depurador](../../extensibility/debugger/debugger-components.md) Fornece uma visão geral dos componentes de depuração do Visual Studio, que incluem o mecanismo de depuração (DE), o avaliador de expressão (EE) e o manipulador de símbolos (SH).

 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md) Contém links para várias tarefas de depuração, como o lançamento de um programa e a avaliação de expressões.
