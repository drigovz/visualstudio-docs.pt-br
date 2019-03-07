---
title: Contextos do depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4d1dd6d8f4d64400b4b2358dd47971f3111dcf1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700686"
---
# <a name="debugger-contexts"></a>Contextos do depurador
No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, o mecanismo de depuração (DES) opera simultaneamente em vários contextos distintos, da seguinte maneira:

-   O contexto de código, que descreve o local atual no fluxo de execução de um programa.

-   O contexto de documentação ou posição, que descreve a posição atual dentro de um documento de origem.

-   O contexto de avaliação de expressão, que descreve o contexto em que a expressão a avaliação será realizada.

## <a name="in-this-section"></a>Nesta seção
 [Contexto de código](../../extensibility/debugger/code-context.md) aborda o contexto de código como um endereço no fluxo de instruções de um programa em arquiteturas de tempo de execução de hoje versus idiomas não tradicionais, onde código não pode ser representado por instruções, mas outros meios.

 [Posição de documento](../../extensibility/debugger/document-position.md) define a posição do documento na depuração do Visual Studio por meio de uma abstração de uma posição em um arquivo de origem como o IDE conhecido.

 [Contexto de documento](../../extensibility/debugger/document-context.md) aborda qual contexto de documento representa em depuração do Visual Studio em relação a um arquivo de origem. Também discute como o manipulador de símbolo mapeia um contexto de código para o contexto da documentação.

 [Contexto de avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md) fornece informações sobre um contexto de avaliação de expressão no Visual Studio. Por exemplo, um contexto de avaliação de expressão associado com um quadro de pilha fornece o contexto para avaliar as variáveis locais, parâmetros de método e membros de classe.

## <a name="related-sections"></a>Seções relacionadas
 [Conceitos de depuração](../../extensibility/debugger/debugger-concepts.md) descreve os principais conceitos de arquiteturas de depuração.

 [Componentes de depuração](../../extensibility/debugger/debugger-components.md) fornece uma visão geral dos componentes, que incluem o mecanismo de depuração (DE), o avaliador de expressão (EE) e o manipulador de símbolo (SH) de depuração do Visual Studio.

 [As tarefas de depuração](../../extensibility/debugger/debugging-tasks.md) contém links para várias tarefas de depuração, como iniciar um programa e avaliar expressões.