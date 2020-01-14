---
title: Visualizar código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9dcb6edf8ce69d48805c3ad8c3c25ef9cc0ed591
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851354"
---
# <a name="visualize-code"></a>Visualizar código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar as ferramentas de visualização e modelagem no Visual Studio para ajudá-lo a entender o código existente e a descrever seu aplicativo. Isso permite aprender visualmente como suas mudanças poderiam afetar o código e ajudar a avaliar o trabalho e os riscos resultantes dessas mudanças. Por exemplo:

- Para entender as relações em seu código, mapeie essas relações visualmente.

- Para descrever a arquitetura do seu sistema e manter o código consistente com seu design, crie diagramas de camada e valide o código em relação a esses diagramas.

- Para descrever estruturas de classe, crie diagramas de classe.

- Para modelar e comunicar vários aspectos do sistema, Desenhe diagramas Unified Modeling Language (UML). Por exemplo, você pode modelar os componentes, tipos, interações e processos de um sistema.

  Essas ferramentas também ajudam você a se comunicar com mais facilidade com as pessoas envolvidas com seu projeto. Por exemplo, você pode usar diagramas de classe UML para criar um glossário comum para discutir o sistema com participantes do projeto, usuários e membros da equipe.

  Para ver quais versões do Visual Studio oferecem suporte a cada recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>O que você deseja fazer?

|||
|-|-|
|**Entenda o código e suas relações:**<br /><br /> Mapeie as relações entre partes específicas do código.<br /><br /> Consulte uma visão geral das relações em seu código para a solução inteira.<br /><br /> **Observação**: nesta versão do Visual Studio, o termo *mapa de código* é usado no lugar do *grafo de dependência*.|-   [mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />-   [usar mapas de código para depurar seus aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [encontrar possíveis problemas usando analisadores de mapa de código](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [métodos de mapeamento na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Entenda as estruturas de classe:**<br /><br /> Visualize a estrutura de classes em um projeto Criando diagramas de classe do código.|[Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Descreva o design do sistema de alto nível e valide o código em relação a este design:**<br /><br /> Descreva o design do sistema de alto nível e suas dependências pretendidas Criando diagramas de camada. Valide o código em relação a esse design para garantir que as dependências no código permaneçam consistentes com o design.|-   [criar diagramas de camada do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />[diagramas de camada de -   : referência](../modeling/layer-diagrams-reference.md)<br />[diagramas de camada de -   : diretrizes](../modeling/layer-diagrams-guidelines.md)<br />-   [validar o código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)|
|**Comunique os requisitos e a arquitetura do usuário:**<br /><br /> Modele os requisitos de usuário e a arquitetura do seu sistema de software desenhando os seguintes diagramas UML: atividade, componente, classe, sequência e caso de uso.|-   [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md)<br />[requisitos de usuário do modelo](../modeling/model-user-requirements.md) de -   <br />-   [modelar a arquitetura de seu aplicativo](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Recursos Externos

|**Categoria**|**Links**|
|------------------|---------------|
|**Fóruns**|[ferramentas de modelagem & de visualização do Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch) -   <br />[SDK de modelagem do & de visualização do Visual Studio (ferramentas DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx) -   |
|**Blogs**|[Visual Studio ALM + Team Foundation Server Blog](https://blogs.msdn.com/b/visualstudioalm)|
|**Artigos técnicos e diários**|[Fórum de arquitetura do MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Veja também
 [Cenário: alterar o design usando visualização e modelagem](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [análise e arquitetura de modelagem](../modeling/analyze-and-model-your-architecture.md) [criar modelos para o modelo de aplicativo](../modeling/create-models-for-your-app.md) [modelo de requisitos de usuário](../modeling/model-user-requirements.md) [a arquitetura de seu aplicativo](../modeling/model-your-app-s-architecture.md) [usa modelos em seu processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)
