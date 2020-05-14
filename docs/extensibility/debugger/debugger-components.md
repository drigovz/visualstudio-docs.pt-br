---
title: Componentes de depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03c400fd03c5ee0f2629e9f436b65f53f8f2ac8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739015"
---
# <a name="debugger-components"></a>Componentes do depurador
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador é implementado como um VSPackage e gerencia toda a sessão de depuração. A sessão de depuração compreende os seguintes elementos:

- **Pacote de depuração:** O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador fornece a mesma interface de usuário, não importa o que esteja sendo depurado.

- **Gerenciador de depuração de sessão (SDM):** Fornece uma interface programática [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consistente para o Depurador para o gerenciamento de uma variedade de motores de depuração. É implementado [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]por .

- **Gerenciador de depuração de processos (PDM):** Gerencia, para todas as [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]instâncias em execução, uma lista de todos os programas que podem ser ou estão sendo depurados. É implementado [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]por .

- **Motor de depuração (DE):** É responsável por monitorar um programa que está sendo depurado, comunicar o estado do programa em execução para o SDM e o PDM, e interagir com o avaliador de expressão e provedor de símbolos para fornecer análise em tempo real do estado da memória e variáveis de um programa. Ele é [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementado por (para os idiomas que ele suporta) e fornecedores de terceiros que desejam apoiar seu próprio tempo de execução.

- **Avaliador de expressão (EE):** Fornece suporte para avaliar dinamicamente variáveis e expressões fornecidas pelo usuário quando um programa foi interrompido em um determinado ponto. Ele é [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementado por (para os idiomas que ele suporta) e fornecedores de terceiros que querem apoiar seus próprios idiomas.

- **Provedor de símbolos (SP):** Também chamado de manipulador de símbolos, mapeia os símbolos de depuração de um programa para uma instância em execução do programa para que informações significativas possam ser fornecidas (como depuração no nível de código-fonte e avaliação de expressão). Ele é [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementado por (para os símbolos Common Language Runtime [CLR] e o formato de arquivo de símbolos Program DataBase [PDB]) e por fornecedores de terceiros que têm seu próprio método proprietário de armazenar informações de depuração.

  O diagrama a seguir mostra a relação entre esses elementos do depurador visual studio.

  ![Visão geral dos componentes de depuração](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>Nesta seção
 [Pacote de depuração](../../extensibility/debugger/debug-package.md) Discute o pacote de depuração, que funciona na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] concha e lida com toda a ui.

 [Gerente de depuração de processos](../../extensibility/debugger/process-debug-manager.md) Fornece uma visão geral dos recursos do PDM, que é o gerenciador dos processos que podem ser depurados.

 [Gerente de depuração de sessão](../../extensibility/debugger/session-debug-manager.md) Define o SDM, que fornece uma visão unificada da sessão de depuração para o IDE. O SDM gerencia o DE.

 [Motor de depuração](../../extensibility/debugger/debug-engine.md) Documenta os serviços de depuração que o DE fornece.

 [Modos operacionais](../../extensibility/debugger/operational-modes.md) Fornece uma visão geral dos três modos em que o IDE pode operar: modo de design, modo de execução e modo de quebra. Também são discutidos mecanismos de transição.

 [Avaliador de expressão](../../extensibility/debugger/expression-evaluator.md) Explica o propósito do EE em tempo de execução.

 [Provedor de símbolos](../../extensibility/debugger/symbol-provider.md) Discute como, na implementação, o provedor de símbolos avalia variáveis e expressões.

 [Digite visualizador e visualizador personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Discute o que é um visualizador de tipo e o espectador personalizado e qual o papel do avaliador de expressão no apoio a ambos.

## <a name="related-sections"></a>Seções relacionadas
 [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md) Descreve os principais conceitos arquitetônicos de depuração.

 [Contextos de depuração](../../extensibility/debugger/debugger-contexts.md) Explica como o DE opera simultaneamente dentro de contextos de avaliação de código, documentação e expressão. Descreve, para cada um dos três contextos, a localização, posição ou avaliação relevantes para ele.

 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md) Contém links para várias tarefas de depuração, como o lançamento de um programa e a avaliação de expressões.

## <a name="see-also"></a>Confira também
- [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
