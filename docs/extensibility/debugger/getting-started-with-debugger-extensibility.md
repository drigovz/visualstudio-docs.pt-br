---
title: Começando com extensibilidade de depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153db8889c78890a31a2e8003e6aa95ed24a02eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738597"
---
# <a name="get-started-with-debugger-extensibility"></a>Comece com a extensibilidade do depurador
O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornece as informações necessárias para criar e personalizar componentes dedepuradores usados para depurar programas de dentro do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]a depuração adicionou melhorias derivadas do extenso [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] teste de usabilidade realizado em depuradores anteriores. Você pode [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usar a depuração para passar por um aplicativo de vários idiomas ou implementar a edição on-the-fly de variáveis enquanto depura aplicativos e soluções multi-idiomas.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]a depuração é executada fora de processo com o programa sendo depurado e, portanto, menos intrusivo no espaço de processo do aplicativo. Consequentemente, é mais fácil escrever componentes que interagem com o depurador sem afetar seu programa de depuração.

 Para melhor [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]usar o , você deve estar familiarizado com os seguintes itens:

- O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE)

- A linguagem de programação C++

- ATL COM

## <a name="in-this-section"></a>Nesta seção
 [Roteiro para a extensão do depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Descreve o processo de implementação da depuração em seu produto, dependendo do seu compilador e sua saída.

 [Componentes do depurador](../../extensibility/debugger/debugger-components.md) Fornece uma visão [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geral dos componentes de depuração, que incluem o mecanismo de depuração (DE), o avaliador de expressão (EE) e o manipulador de símbolos (SH).

 [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md) Descreve os principais conceitos arquitetônicos de depuração.

 [Contextos de depuração](../../extensibility/debugger/debugger-contexts.md) Explica como o mecanismo de depuração (DE) opera simultaneamente dentro dos contextos de avaliação de código, documentação e expressão. Descreve, para cada um dos três contextos, a localização, posição ou avaliação relevantes para ele.

 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md) Contém links para várias tarefas de depuração, como o lançamento de um programa e a avaliação de expressões.
