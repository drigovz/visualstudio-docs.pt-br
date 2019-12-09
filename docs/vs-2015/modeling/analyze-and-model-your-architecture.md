---
title: Analise e modele sua arquitetura | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 49c421af5aa6c91535b05f0beca88099ea7a2eaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297947"
---
# <a name="analyze-and-model-your-architecture"></a>Analisar e modelar a sua arquitetura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verifique se seu aplicativo atende aos requisitos de usuário usando ferramentas de arquitetura e modelagem do Visual Studio para criar e modelar seu aplicativo. Entenda o código do programa existente mais facilmente usando o Visual Studio para visualizar a estrutura, o comportamento e as relações do código.

 Crie modelos em diferentes níveis de detalhes ao longo do ciclo de vida do aplicativo como parte do seu processo de desenvolvimento. Acompanhe os requisitos, as tarefas, os casos de teste, os bugs e outros trabalhos associados aos seus modelos vinculando elementos de modelo a Team Foundation Server itens de trabalho e seu plano de desenvolvimento. Consulte [cenário: alterar o design usando visualização e modelagem](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 Para ver quais versões do Visual Studio oferecem suporte a cada recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="to"></a>{1&gt;Para&lt;1}

|||
|-|-|
|**Visualizar código**:<br /><br /> -Consulte a organização do código e as relações Criando mapas de código. Visualize dependências entre assemblies, namespaces, classes, métodos e assim por diante.<br />-Consulte a estrutura de classe e os membros de um projeto específico Criando diagramas de classe do código.<br />-Encontre conflitos entre seu código e seu design criando diagramas de camada para validar o código.<br /><br /> **Observação**: nesta versão do Visual Studio, o termo *mapa de código* é usado no lugar do *grafo de dependência*. O termo *grafo* quando usado sozinha geralmente refere-se a um gráfico direcionado ou diagrama DGML (ou documento). Mapas de código são um tipo especializado de diagrama DGML.|-   [Visualizar código](../modeling/visualize-code.md)<br />-   [trabalhando com classes e outros tipos (Designer de classe)](../ide/working-with-classes-and-other-types-class-designer.md)<br />[vídeo de -   : entenda suas dependências de código por meio de visualização (canal 9)](https://go.microsoft.com/fwlink/?LinkID=252065)<br />[vídeo de -   : Visualizar o impacto de uma alteração (canal 9)](https://go.microsoft.com/fwlink/?LinkID=252068)|
|**Descrever e comunicar os requisitos de usuário**:<br /><br /> -Esclareça histórias de usuários, regras de negócios e outros requisitos e ajude a garantir sua consistência, desenhando diagramas UML como casos de uso, atividade e diagramas de classe.|-   [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md)<br />[requisitos de usuário do modelo](../modeling/model-user-requirements.md) de -   <br />[vídeo de -   : melhorar a arquitetura por meio de modelagem (canal 9)](https://go.microsoft.com/fwlink/?LinkID=252078)|
|**Defina a arquitetura**:<br /><br /> -Modelar a estrutura em larga escala do seu sistema de software e os padrões de design por desenho de diagramas UML, classes e componentes de sequência.<br />-Definir e impor restrições em dependências entre os componentes do seu código Criando diagramas de camada.|-   [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md)<br />-   [modelar a arquitetura de seu aplicativo](../modeling/model-your-app-s-architecture.md)<br />[vídeo de -   : melhorar a arquitetura por meio de modelagem (canal 9)](https://go.microsoft.com/fwlink/?LinkID=252078)<br />Vídeo de -   [: Use diagramas de camada para projetar e validar sua arquitetura (canal 9)](https://go.microsoft.com/fwlink/?LinkID=252073)|
|**Valide seu sistema com os requisitos e o design pretendido:**<br /><br /> -Definir testes de aceitação ou testes de sistema com base nos modelos de requisitos. Isso cria uma relação forte entre os testes e os requisitos dos seus usuários e ajuda a atualizar o sistema mais facilmente quando os requisitos mudam.<br />– Valide dependências de código com diagramas de camada que descrevem a arquitetura desejada e evite alterações que possam entrar em conflito com o design.|-   [validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)<br />Vídeo de -   [: Use diagramas de camada para projetar e validar sua arquitetura (canal 9)](https://go.microsoft.com/fwlink/?LinkID=252073)|
|**Compartilhe modelos, diagramas e mapas de código usando o controle de versão do Team Foundation**:<br /><br /> -Coloque mapas de código, modelagem de projetos, diagramas UML e diagramas de camada sob o controle de versão do Team Foundation para que você possa compartilhá-los.|Quando você tiver vários usuários que trabalham com esses itens sob o controle de versão do Team Foundation, use estas diretrizes para ajudá-lo a evitar problemas de controle de versão:<br /><br /> -   [gerenciar modelos e diagramas sob controle de versão](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**Gere ou configure partes do seu aplicativo de UML ou de linguagens específicas de domínio**:<br /><br /> -Tornar seu design mais responsivo às alterações de requisitos e facilmente uma variável em uma linha de produtos.|-   [gerar e configurar seu aplicativo com base em modelos](../modeling/generate-and-configure-your-app-from-models.md)|
|**Personalizar modelos e diagramas**:<br /><br /> – Adapte modelos de como seu projeto os utiliza definindo propriedades adicionais para elementos UML, restrições de validação para garantir que seus modelos estejam em conformidade com suas regras de negócio, além de comandos de menu e itens de caixa de ferramentas adicionais.<br />-Crie suas próprias linguagens específicas de domínio.|-   [estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md)<br />[SDK de modelagem de -   para Visual Studio-linguagens específicas de domínio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Gerar texto usando modelos T4**:<br /><br /> -Use blocos de texto e lógica de controle dentro de modelos para gerar arquivos baseados em texto.|[modelos de texto de geração de código e T4 de](../modeling/code-generation-and-t4-text-templates.md) -   |

## <a name="types-of-models-and-their-uses"></a>Tipos de modelos e seus usos

|**Tipo de modelo e usos típicos**|
|-------------------------------------|
|**Mapas de código**<br /><br /> Os mapas de código ajudam você a ver a organização e as relações em seu código.<br /><br /> Usos típicos:<br /><br /> -Examine o código do programa para que você possa entender melhor sua estrutura e suas dependências, como atualizá-lo e estimar o custo das alterações propostas.<br /><br /> Consulte:<br /><br /> -   [mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />-   [usar mapas de código para depurar seus aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [encontrar possíveis problemas usando analisadores de mapa de código](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Diagrama de camada**<br /><br /> Os diagramas de camada permitem que você defina a estrutura de um aplicativo como um conjunto de camadas ou blocos com dependências explícitas. Você pode executar a validação para descobrir conflitos entre dependências no código e as dependências descritas em um diagrama de camada.<br /><br /> Usos típicos:<br /><br /> – Estabilizar a estrutura do aplicativo por meio de várias alterações ao longo de sua vida.<br />-Descobrir conflitos de dependências não intencionais antes de fazer check-in de alterações no código.<br /><br /> Consulte:<br /><br /> -   [criar diagramas de camada do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />[diagramas de camada de -   : referência](../modeling/layer-diagrams-reference.md)<br />-   [validar o código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)|
|**Modelo UML**<br /><br /> Um modelo UML inclui vários modos de exibição, incluindo classe, componente, casos de uso, atividade e diagramas de sequência. Você pode personalizar o UML para se adequar ao domínio do aplicativo. Por exemplo, você pode anexar marcas, informações adicionais e restrições aos elementos do modelo. Você também pode definir ferramentas que operam nos modelos. Consulte [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md).<br /><br /> Usos típicos:<br /><br /> -Descrever os requisitos e o design. Você pode aplicar o UML rapidamente ao desenvolvimento de qualquer aplicativo. Consulte [usar modelos em seu processo de desenvolvimento](../modeling/use-models-in-your-development-process.md).<br />-Gerar ou configurar testes ou partes de um aplicativo. Alguns trabalhos são necessários para personalizar a notação e desenvolver os modelos de geração ou o aplicativo configurável. Consulte [gerar e configurar seu aplicativo com base em modelos](../modeling/generate-and-configure-your-app-from-models.md).<br />-Para descrição geral e para geração de código ou configuração em projetos menores.|
|**DSL (linguagem específica de domínio)**<br /><br /> Uma DSL é uma notação que você cria para uma finalidade específica. No Visual Studio, geralmente é gráfico.<br /><br /> Usos típicos:<br /><br /> – Gerar ou configurar partes do aplicativo. O trabalho é necessário para desenvolver a notação e as ferramentas. O resultado pode ser uma melhor opção para seu domínio do que uma personalização de UML.<br />-Para projetos grandes ou em linhas de produtos em que o investimento no desenvolvimento da DSL e suas ferramentas são retornados por seu uso em mais de um projeto.<br /><br /> Consulte:<br /><br /> [SDK de modelagem de -   para Visual Studio-linguagens específicas de domínio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Onde posso obter mais informações?

|||
|-|-|
|**Nos**|[ferramentas de modelagem & de visualização do Visual Studio](https://go.microsoft.com/fwlink/?LinkId=184720) -   <br />[SDK de modelagem do & de visualização do Visual Studio (ferramentas DSL)](https://go.microsoft.com/fwlink/?LinkId=184721) -   |

## <a name="see-also"></a>Consulte também

- [O que há de novo para modelagem no Visual Studio 2015](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps e gerenciamento de ciclo de vida do aplicativo](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
