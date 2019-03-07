---
title: Introdução à extensibilidade do depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f3fe14cff05f37ef7ee6f10026fd727696a223f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696045"
---
# <a name="get-started-with-debugger-extensibility"></a>Introdução a extensibilidade do depurador
O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornece as informações que você precisa para criar e personalizar componentes do depurador usados para depurar programas de dentro do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração adicionou melhorias derivadas a usabilidade extenso teste realizado no anterior [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuradores. Você pode usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração para percorrer um aplicativo de vários idioma, ou você pode implementar em interrupções de edição de variáveis durante a depuração de aplicativos e soluções de vários idiomas.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração é executada fora do processo com o programa que está sendo depurado e, portanto, é menos intrusiva no espaço de processo do aplicativo. Consequentemente, é mais fácil escrever componentes que interagem com o depurador sem afetar o seu programa de depuração.

 Usar melhor o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], você deve estar familiarizado com os seguintes itens:

- O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE)

- A linguagem de programação do C++

- ATL COM

## <a name="in-this-section"></a>Nesta seção
 [Roteiro para estender o depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) descreve o processo de implementação de depuração no seu produto, dependendo do seu compilador e sua saída.

 [Componentes do depurador](../../extensibility/debugger/debugger-components.md) fornece uma visão geral de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração componentes, que incluem o mecanismo de depuração (DE), o avaliador de expressão (EE) e o manipulador de símbolo (SH).

 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md) descreve os principais conceitos de arquiteturas de depuração.

 [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md) explica como o mecanismo de depuração (DES) opera simultaneamente em contextos de avaliação de código, documentação e expressão. Descreve, para cada um dos três contextos, a localização, posição ou avaliação relevante a ele.

 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md) contém links para várias tarefas de depuração, como iniciar um programa e avaliar expressões.