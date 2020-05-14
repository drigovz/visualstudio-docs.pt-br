---
title: Contextos de depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56825fe299147e60c5ed9dfcefa491a427ab59e4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738968"
---
# <a name="debugger-contexts"></a>Contextos de depuração
Na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, o mecanismo de depuração (DE) opera simultaneamente dentro de vários contextos distintos, da seguinte forma:

- O contexto de código, que descreve a localização atual no fluxo de execução de um programa.

- O contexto ou posição da documentação, que descreve a posição atual dentro de um documento de origem.

- O contexto de avaliação de expressão, que descreve o contexto em que a avaliação de expressão ocorrerá.

## <a name="in-this-section"></a>Nesta seção
 [Contexto de código](../../extensibility/debugger/code-context.md) Discute o contexto de código como um endereço no fluxo de instruções de um programa nas arquiteturas de tempo de execução de hoje versus línguas não tradicionais, onde o código pode não ser representado por instruções, mas alguns outros meios.

 [Posição do documento](../../extensibility/debugger/document-position.md) Define a posição do documento na depuração do Visual Studio por meio de uma abstração de uma posição em um arquivo de origem conhecido pelo IDE.

 [Contexto do documento](../../extensibility/debugger/document-context.md) Discute o contexto do documento na depuração do Visual Studio em relação a um arquivo de origem. Também discute como o manipulador de símbolos mapeia um contexto de código para o contexto da documentação.

 [Contexto de avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md) Fornece informações sobre um contexto de avaliação de expressão no Visual Studio. Por exemplo, um contexto de avaliação de expressão associado a um quadro de pilha fornece o contexto para avaliar variáveis locais, parâmetros de método e membros de classe.

## <a name="related-sections"></a>Seções relacionadas
 [Conceitos de depuração](../../extensibility/debugger/debugger-concepts.md) Descreve os principais conceitos arquitetônicos de depuração.

 [Componentes de depuração](../../extensibility/debugger/debugger-components.md) Fornece uma visão geral dos componentes de depuração do Visual Studio, que incluem o mecanismo de depuração (DE), o avaliador de expressão (EE) e o manipulador de símbolos (SH).

 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md) Contém links para várias tarefas de depuração, como o lançamento de um programa e a avaliação de expressões.
