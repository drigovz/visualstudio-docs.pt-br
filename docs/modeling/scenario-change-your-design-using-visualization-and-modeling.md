---
title: 'Cenário: alterar o design usando visualização e modelagem'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1400f6d5881d5340ec452297d3579306111391b6
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759740"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Cenário: alterar o design usando visualização e modelagem

Certifique-se de que seu sistema de software atenda às necessidades dos usuários usando as ferramentas de visualização e modelagem no Visual Studio.
Use ferramentas como mapas de código, diagramas de dependência e diagramas de classe para:

Para ver quais versões do Visual Studio suportam cada ferramenta, consulte [suporte à versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Esclarecer as necessidades dos usuários e os processos de negócios.

- Visualize e explore o código existente.

- Descreva alterações em um sistema existente.

- Verifique se o sistema atende aos seus requisitos.

- Mantenha o código consistente com o design.

Este passo a passo:

- Descreve como essas ferramentas podem beneficiar seu projeto de software.

- Mostra como você pode usar essas ferramentas, independentemente da sua abordagem de desenvolvimento, com um cenário de exemplo.

Para saber mais sobre essas ferramentas e os cenários que eles suportam, veja:

- [Análise e modelagem de arquitetura](../modeling/analyze-and-model-your-architecture.md)

- [Visualizar código](../modeling/visualize-code.md)

## <a name="scenario-overview"></a>Visão geral do cenário

Este cenário descreve episódios dos ciclos de vida do desenvolvimento de software de duas empresas fictícias: Dinner Now e Lucerne Publishing. O Dinner Now oferece um serviço de entrega de refeições baseado na Web em Seattle. Os clientes podem pedir refeições e pagá-las no site do Dinner Now. Os pedidos são então enviados para o restaurante local apropriado para entrega. A Lucerne Publishing, uma empresa em Nova York, administra vários negócios fora e na Internet. Por exemplo, eles executam um site onde os clientes podem postar avaliações de restaurantes.

Lucerna adquiriu recentemente o Dinner Now e quer fazer as seguintes mudanças:

- Integre seus sites adicionando recursos de revisão de restaurantes ao Dinner Now.

- Substitua o sistema de pagamento do Dinner Now pelo sistema da Lucerna.

- Expanda o serviço Dinner Now em toda a região.

Jantar Agora usa PROGRAMAÇÃO SCRUM e eXtreme. Eles têm uma cobertura de teste muito alta e muito pouco código sem suporte. Eles minimizam os riscos criando versões pequenas, mas funcionando de um sistema e, em seguida, adicionando funcionalidade incrementalmente. Eles desenvolvem seu código sobre iterações curtas e freqüentes. Isso permite que eles abracem a mudança com confiança, refatorem o código com freqüência e evitem "grande design na frente".

Lucerna mantém uma coleção muito maior e complexa de sistemas, alguns dos quais têm mais de 40 anos. Eles são muito cautelosos em fazer mudanças devido à complexidade e escopo do código legado. Eles seguem um processo de desenvolvimento mais rigoroso, preferindo projetar soluções detalhadas e documentar o design e as mudanças que ocorrem durante o desenvolvimento.

Ambas as equipes usam diagramas de modelagem no Visual Studio para ajudá-los a desenvolver sistemas que atendam às necessidades dos usuários. Eles usam o Team Foundation Server juntamente com outras ferramentas para ajudá-los a planejar, organizar e gerenciar seu trabalho.

Para obter mais informações sobre o Team Foundation Server, consulte:

- [Planejar e acompanhar o trabalho](#plan-and-track-work)

- [Testando, validando e verificando em código atualizado](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a>Funções de Arquitetura e Diagramas de Modelagem no Desenvolvimento de Software

A tabela a seguir descreve funções que essas ferramentas podem desempenhar durante vários e vários estágios do ciclo de vida do desenvolvimento de software:

||**Modelagem de requisitos do usuário**|**Modelagem de processos de negócios**|**Arquitetura de sistema & Design**|**Visualização de códigos & Exploração**|**Verificação**|
|------|-|-|-|-|-|
|Diagrama dsl (Domain-Specific Language, linguagem específica de domínio)|Sim|Sim|Sim|||
|Diagrama de dependência, validação de camadas|||Sim|Sim|Sim|
|Mapa de código|||Sim|Sim|Sim|
|Class Designer (baseado em código)||||Sim||

Para desenhar diagramas de dependência, você deve criar um projeto de modelagem como parte de uma solução existente ou de uma nova. Esses diagramas devem ser criados no projeto de modelagem.
Os itens dos diagramas de dependência estão localizados no projeto de modelagem, mas não são armazenados no modelo comum. Mapas de código e diagramas de classe .NET criados a partir do código existem fora do projeto de modelagem.

Consulte:

- [Criar diagramas de dependência do código](../modeling/create-layer-diagrams-from-your-code.md)

- [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)

- [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [SDK de Modelagem para Visual Studio - linguagens específicas ao domínio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Ambas as equipes também usam validação de dependência para garantir que o código em desenvolvimento permaneça consistente com o design. Consulte:

- [Mantendo código consistente com o design](#ValidatingCode)

- [Descreva a arquitetura lógica: diagramas de dependência](#DescribeLayers)

- [Validar o código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Algumas versões do Visual Studio suportam validação de dependência e versões somente leitura de mapas de código para visualização e modelagem. Para ver quais edições do Visual Studio suportam esse recurso, consulte [o suporte do Edition para ferramentas de arquitetura e modelagem.](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="understand-and-communicate-information-about-the-system"></a>Entender e comunicar informações sobre o sistema

Não há nenhuma ordem prescrita para usar os diagramas de modelagem do Visual Studio, para que você possa usá-los conforme se encaixem com suas necessidades ou abordagem. Normalmente, as equipes revisitam seus modelos de forma iterativa e freqüente ao longo de um projeto. Cada diagrama oferece pontos fortes específicos para ajudá-lo a entender, descrever e comunicar diferentes aspectos do sistema em desenvolvimento.

Dinner Now e Lucerna se comunicam entre si e com os stakeholders do projeto usando diagramas como linguagem comum. Por exemplo, o Dinner Now usa diagramas para executar essas tarefas:

- Visualize o código existente.

- Comunique-se com Lucerna sobre histórias de usuários novas ou atualizadas.

- Identifique as alterações necessárias para suportar histórias de usuários novas ou atualizadas.

Lucerna usa diagramas para executar essas tarefas:

- Conheça o processo de negócios do Dinner Now.

- Entenda o design do sistema.

- Comunique-se com o Dinner Now sobre os requisitos do usuário novos ou atualizados.

- Atualizações de documentos para o sistema.

Os diagramas são integrados com o Team Foundation Server para que as equipes possam planejar, gerenciar e acompanhar seu trabalho com mais facilidade. Por exemplo, eles usam modelos para identificar casos de teste e tarefas de desenvolvimento e estimar seu trabalho. Lucerne vincula itens de trabalho da Team Foundation Server a elementos modelados para que eles possam monitorar o progresso e garantir que o sistema atenda aos requisitos dos usuários. Por exemplo, eles vinculam casos de uso para testar itens de trabalho de caso para que eles possam ver que os casos de uso são cumpridos quando todos os testes passam.

Antes que as equipes verifiquem suas alterações, elas validam o código em relação aos testes e ao design executando compilações que incluem validação de dependência e testes automatizados. Isso ajuda a garantir que o código atualizado não entre em conflito com o design e quebre a funcionalidade de funcionamento anteriormente.

### <a name="identify-changes-to-the-existing-system"></a>Identificar alterações no sistema existente

Jantar Agora deve estimar o custo de cumprir a nova exigência. Isso depende, em parte, do quanto essa mudança afetará outras partes do sistema. Para ajudá-los a entender isso, um dos desenvolvedores do Dinner Now cria esses mapas e diagramas a partir do código existente:

|**Mapa ou diagrama**|**programas**|
|-|-|
|*Mapa de código*<br /><br /> Consulte:<br /><br /> - [Mapear dependências através de suas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />- [Navegue e reorganize mapas de código](../modeling/browse-and-rearrange-code-maps.md)<br />- [Personalize mapas de código editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Dependências e outras relações em código.<br /><br /> Por exemplo, o Dinner Now pode começar revisando mapas de código de montagem para uma visão geral das assembléias e suas dependências. Eles podem perfurar os mapas para explorar os namespaces e classes nessas assembléias.<br /><br /> Jantar Agora também pode criar mapas para explorar determinadas áreas e outros tipos de relacionamentos no código. Eles usam o Solution Explorer para encontrar e selecionar as áreas e relacionamentos que lhes interessam.|
|*Diagrama de classe baseado em código*<br /><br /> Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Classes existentes em código|

 Por exemplo, o desenvolvedor cria um mapa de código. Ela ajusta seu escopo para focar nas áreas que serão afetadas pelo novo cenário. Essas áreas são selecionadas e destacadas no mapa:

 ![Gráfico de dependência de namespace](../modeling/media/namespace_reviewsystem.png)

 **Mapa de código de namespace**

 O desenvolvedor expande os namespaces selecionados para ver suas classes, métodos e relacionamentos:

 ![Gráfico expandido de dependência de namespace](../modeling/media/dep_reviewsystem.png)

 **Mapa de código de namespace expandido com links de grupo cruzado visíveis**

 O desenvolvedor examina o código para encontrar as classes e métodos afetados. Para ver os efeitos de cada alteração à medida que você os faz, regenere mapas de código após cada alteração. Consulte [Visualize code](../modeling/visualize-code.md).

 Para descrever alterações em outras partes do sistema, como componentes ou interações, a equipe pode desenhar esses elementos em quadros brancos. Eles também podem desenhar os seguintes diagramas no Visual Studio para que os detalhes possam ser capturados, gerenciados e compreendidos por ambas as equipes:

|**Diagramas**|**Descreve**|
|-|-|
|*Diagrama de classe baseado em código*<br /><br /> Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Classes existentes em código.|

### <a name="keep-code-consistent-with-the-design"></a><a name="ValidatingCode"></a>Manter código consistente com o design
 Jantar Agora deve certificar-se de que o código atualizado permanece consistente com o design. Eles criam diagramas de dependência que descrevem as camadas de funcionalidade no sistema, especificam as dependências permitidas entre eles e associam artefatos de solução a essas camadas.

|**Diagrama**|**Descreve**|
|-|-|
|*Diagrama de dependência*<br /><br /> Consulte:<br /><br /> - [Crie diagramas de dependência a partir do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramas de dependência: Referência](../modeling/layer-diagrams-reference.md)<br />- [Diagramas de dependência: Diretrizes](../modeling/layer-diagrams-guidelines.md)<br />- [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)|A arquitetura lógica do código.<br /><br /> Um diagrama de dependência organiza e mapeia os artefatos em uma solução do Visual Studio para grupos abstratos chamados *camadas*. Essas camadas identificam as funções, tarefas ou funções que esses artefatos executam no sistema.<br /><br /> Diagramas de dependência são úteis para descrever o design pretendido do sistema e validar o código em evolução em relação a esse projeto.<br /><br /> Para criar camadas, arraste itens do Solution Explorer, mapas de código, exibição de classe e navegador de objetos. Para desenhar novas camadas, use a caixa de ferramentas ou clique com o botão direito do mouse na superfície do diagrama.<br /><br /> Para visualizar as dependências existentes, clique com o botão direito do mouse na superfície do diagrama de dependência e clique **em Gerar dependências**. Para especificar as dependências pretendidas, desenhe novas dependências.|

Por exemplo, o seguinte diagrama de dependência descreve dependências entre camadas e o número de artefatos que estão associados a cada camada:

![Diagrama de dependência do sistema de pagamento integrado](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagrama de dependência**

Para garantir que os conflitos com o design não ocorram durante o desenvolvimento de código, as equipes usam validação de dependência em compilações que são executadas no Azure DevOps. Eles também criam uma tarefa msbuild personalizada para exigir validação de dependência em suas operações de check-in. Eles usam relatórios de compilação para coletar erros de validação.

Consulte:

- [Use o designer visual](/azure/devops/pipelines/get-started-designer)

- [Check-in fechado TFVC](/azure/devops/pipelines/build/triggers)

- [Construir e liberar tarefas](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Dicas gerais para criar e usar modelos

- A maioria dos diagramas consiste em nós conectados por linhas. Para cada tipo de diagrama, a caixa de ferramentas fornece diferentes tipos de nós e linhas.

   Para abrir a caixa de ferramentas, no menu **Exibir,** clique em **Caixa de ferramentas**.

- Para criar um nó, arraste-o da caixa de ferramentas para o diagrama. Certos tipos de nódulos devem ser arrastados para os nódulos existentes. Por exemplo, em um diagrama de componente, uma nova porta deve ser adicionada a um componente existente.

- Para criar uma linha ou uma conexão, clique na ferramenta apropriada na caixa de ferramentas, clique no nó de origem e clique no nó de destino. Algumas linhas podem ser criadas apenas entre certos tipos de nós. Quando você move o ponteiro sobre uma possível fonte ou alvo, o ponteiro indica se você pode criar uma conexão.

### <a name="plan-and-track-work"></a>Planejar e acompanhar o trabalho

Os diagramas de modelagem do Visual Studio são integrados com o Team Foundation Server para que você possa planejar, gerenciar e acompanhar o trabalho com mais facilidade. Ambas as equipes usam modelos para identificar casos de teste e tarefas de desenvolvimento e estimar seu trabalho. A Lucerne cria e vincula itens de trabalho do Team Foundation Server a elementos de modelo, como casos de uso ou componentes. Isso os ajuda a monitorar seu progresso e rastrear seu trabalho de volta às necessidades dos usuários. Isso os ajuda a garantir que suas mudanças continuem a atender a esses requisitos.

À medida que seu trabalho progride, as equipes atualizam seus itens de trabalho para refletir o tempo que gastaram em suas tarefas. Eles também monitoram e relatam o status de seu trabalho usando os seguintes recursos do Team Foundation Server:

- Relatórios *diários* de queima que mostram se eles vão completar o trabalho planejado no tempo esperado. Eles geram outros relatórios semelhantes do Team Foundation Server para acompanhar o progresso dos bugs.

- Uma *planilha de iteração* que usa o Microsoft Excel para ajudar a equipe a monitorar e equilibrar a carga de trabalho entre seus membros. Esta planilha é vinculada ao Team Foundation Server e fornece foco para discussão durante suas reuniões de progresso regular.

- Um *painel de desenvolvimento* que usa o Office Project para manter a equipe informada sobre informações importantes do projeto.

Consulte:

- [Sobre ferramentas ágeis e gerenciamento de projetos Ágeis](/azure/devops/boards/backlogs/backlogs-overview?view=vsts)

- [Gráficos, dashboards e widgets (Azure DevOps Services)](/azure/devops/report/dashboards/overview?view=vsts)

- [Criar sua lista de pendências e tarefas usando o Project](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="test-validate-and-check-in-code"></a><a name="TestValidateCheckInCode"></a>Teste, valide e verifique em código

À medida que as equipes completam cada tarefa, eles verificam seu código no controle de origem e recebem lembretes do Team Foundation Server, se esquecerem. Antes que o Team Foundation Server aceite seus check-ins, as equipes executam testes de unidade e validação de dependência para verificar o código em relação aos seus casos de teste e ao design. Eles usam o Team Foundation Server para executar builds, testes automatizados de unidades e validação de dependência regularmente. Isso ajuda a garantir que o código atenda aos seguintes critérios:

- E funciona.

- Ele não quebra o código de trabalho anteriormente.

- Não conflita com o projeto.

Dinner Now tem uma grande coleção de testes automatizados, que Lucerna pode reutilizar porque quase todos ainda se aplicam. Lucerna também pode construir sobre esses testes e adicionar novos para cobrir novas funcionalidades. Ambos também usam o Visual Studio para executar testes manuais.

Para garantir que o código esteja em conformidade com o design, as equipes configuram suas compilações no Azure DevOps para incluir validação de dependência. Se ocorrer algum conflito, um relatório é gerado com os detalhes.

Consulte:

- [Testando o aplicativo](/azure/devops/test/overview?view=vsts)

- [Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)

- [Usar controle de versão](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)

## <a name="update-the-system-using-visualization-and-modeling"></a>Atualize o sistema usando visualização e modelagem

Lucerna e Dinner Now devem integrar seus sistemas de pagamento. As seções a seguir mostram os diagramas de modelagem no Visual Studio para ajudá-los a executar essa tarefa:

- [Visualize o código existente: Mapas de código](#VisualizeCode)

- [Definir um Glossário de Tipos: Diagramas de Classe](#DefineClasses)

- [Descreva a arquitetura lógica: diagramas de dependência](#DescribeLayers)

Consulte:

- [Visualizar código](../modeling/visualize-code.md)

- [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)

- [Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>Visualize o código existente: Mapas de código

Mapas de código mostram a organização atual e as relações no código. Os itens são representados por nós no mapa, e as relações são *representadas* por *links*. Mapas de código podem ajudá-lo a executar os seguintes tipos de tarefas:

- Explorar códigos desconhecidos.

- Entenda onde e como uma mudança proposta pode afetar o código existente.

- Encontre áreas de complexidade, dependências naturais ou padrões, ou outras áreas que possam se beneficiar da melhoria.

Por exemplo, o Dinner Now deve estimar o custo de atualização do componente PaymentProcessing. Isso depende, em parte, do quanto essa mudança afetará outras partes do sistema. Para ajudá-los a entender isso, um dos desenvolvedores do Dinner Now gera mapas de código a partir do código e ajusta o foco de escopo nas áreas que podem ser afetadas pela mudança.

O mapa a seguir mostra as dependências entre a classe PaymentProcessing e outras partes do sistema Dinner Now, que aparecem selecionadas:

![Gráfico de dependência para o sistema de pagamento Dinner Now](../modeling/media/dep_dnpayment.png)

**Mapa de código para o sistema de pagamento Dinner Now**

O desenvolvedor explora o mapa expandindo a classe PaymentProcessing e selecionando seus membros para ver as áreas potencialmente afetadas:

![Métodos dentro de PagamentosProcessamento e dependências](../modeling/media/depgraph_expandeddn.png)

**Métodos dentro da classe PaymentProcessing e suas dependências**

Eles geram o seguinte mapa para o Sistema de Pagamento Lucerna para inspecionar suas classes, métodos e dependências. A equipe vê que o sistema lucerna também pode exigir trabalho para interagir com as outras partes do Dinner Now:

![Gráfico de dependência para o sistema de pagamento lucerna](../modeling/media/depgraph_lucernepay.png)

**Mapa de código para o Sistema de Pagamento lucerna**

Ambas as equipes trabalham juntas para determinar as mudanças necessárias para integrar os dois sistemas. Eles decidem refatorar parte do código para que seja mais fácil de atualizar. A classe PaymentApprover será mudança para o namespace DinnerNow.Business e exigirá alguns novos métodos. As classes Dinner Now que lidam com transações terão seu próprio espaço de nome. As equipes criam e usam itens de trabalho para planejar, organizar e acompanhar seu trabalho. Eles ligam os itens de trabalho a elementos modelados onde ele é útil.

Após a reorganização do código, as equipes geram um novo mapa de código para ver a estrutura e relacionamentos atualizados:

![Gráfico de dependência com código reorganizado](../modeling/media/depgraph_integrated.png)

**Mapa de código com código reorganizado**

Este mapa mostra que a classe PaymentApprover está agora no namespace DinnerNow.Business e tem alguns novos métodos. As classes de transação Dinner Now agora têm seu próprio namespace paymentsystem, o que torna mais fácil lidar com esse código mais tarde.

#### <a name="creating-a-code-map"></a>Criando um mapa de código

- Para obter uma visão geral rápida do código-fonte, siga estas etapas para gerar um mapa de código:

     No menu **Arquitetura,** clique em **Gerar mapa de código para solução**.

     Para uma visão geral rápida do código compilado, crie um mapa de código em branco e arraste arquivos de montagem ou arquivos binários para a superfície do mapa.

- Para explorar itens específicos de código ou solução, use o Solution Explorer para selecionar itens e relacionamentos que você deseja visualizar. Em seguida, você pode gerar um novo mapa ou adicionar itens selecionados a um mapa existente. Consulte [as dependências do mapa em suas soluções](../modeling/map-dependencies-across-your-solutions.md).

- Para ajudá-lo a explorar o mapa, reorganize o layout para que ele se adapte aos tipos de tarefas que você deseja executar.

     Por exemplo, para visualizar camadas no código, selecione um layout de árvore. Consulte [Procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Resumo: Pontos fortes dos mapas de código
 Mapas de código ajudam você:

- Saiba mais sobre a organização e relacionamentos no código existente.

- Identificar áreas que podem ser afetadas por uma mudança proposta.

- Encontre áreas de complexidade, padrões, camadas ou outras áreas que você possa melhorar para tornar o código mais fácil de manter, alterar e reutilizar.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descreve**|
|-|-|
|Diagrama de dependência|A arquitetura lógica do sistema. Use validação de dependência para garantir que o código permaneça consistente com o design.<br /><br /> Para ajudá-lo a identificar as dependências existentes ou as dependências pretendidas, crie um mapa de código e itens relacionados ao grupo. Para criar um diagrama de dependência, consulte:<br /><br /> - [Crie diagramas de dependência a partir do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramas de dependência: Diretrizes](../modeling/layer-diagrams-guidelines.md)|
|Diagrama de classe (baseado em código)|Classes existentes em código para um projeto específico.<br /><br /> Para visualizar e modificar uma classe existente em código, use Class Designer.<br /><br /> Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a>Definir um Glossário de Tipos: Diagramas de Classe
 Os diagramas de classe definem as entidades, termos ou conceitos que participam do sistema e suas relações entre si. Por exemplo, você pode usar esses diagramas durante o desenvolvimento para descrever os atributos e operações de cada classe, independentemente de sua linguagem de implementação ou estilo.

 Para ajudar Lucerna a descrever e discutir as entidades que participam do caso de uso do Pagamento de Processo, eles desenham o seguinte diagrama de classe:

 ![Entidades de pagamento de processos no diagrama da classe](../modeling/media/uml_payentities.png)

 **Entidades de pagamento de processos em um diagrama de classe**

 Este diagrama mostra que um Cliente pode ter muitos pedidos e diferentes maneiras de pagar por pedidos. Conta bancária e cartão de crédito herdam do Pagamento.

 Durante o desenvolvimento, Lucerna usa o seguinte diagrama de classe para descrever e discutir os detalhes de cada classe:

 ![Detalhes da entidade process payment em um diagrama de classe](../modeling/media/uml_payment.png)

 **Detalhes do pagamento do processo no diagrama da classe**

#### <a name="drawing-a-class-diagram"></a>Desenho de um diagrama de classe

Um diagrama de classe tem as seguintes características principais:

- Tipos como classes, interfaces e enumerações:

  - Uma *classe* é a definição de objetos que compartilham características estruturais ou comportamentais específicas.

  - Uma *interface* define uma parte do comportamento externamente visível de um objeto.

  - Uma *enumeração* é um classificador que contém uma lista de valores literais.

- *Atributos* são valores de um determinado tipo que descrevem cada instância de um *classificador*. Um classificador é um nome geral para tipos, componentes, casos de uso e até atores.

- *As operações* são métodos ou funções que as instâncias de um classificador podem executar.

- Uma *associação* indica algum tipo de relação entre dois classificadores.

  - Uma *agregação* é uma associação que indica uma propriedade compartilhada entre classificadores.

  - Uma *composição* é uma associação que indica uma relação de parte inteira entre os classificadores.

    Para mostrar agregações ou composições, coloque a propriedade **Agregação** em uma associação. **Mostra shared** agregações e **composto** mostra composições.

- Uma *dependência* indica que alterar a definição de um classificador pode alterar a definição de outro classificador.

- Uma *generalização* indica que um classificador específico herda parte de sua definição a partir de um classificador geral. Uma *realização* indica que uma classe implementa as operações e atributos oferecidos por uma interface.

     Para criar essas relações, use a ferramenta **Herança.** Alternativamente, uma realização pode ser representada como um *pirulito.*

- *Os pacotes* são grupos de classificadores, associações, linhas de vida, componentes e outros pacotes. *As* relações de importação indicam que um pacote inclui todas as definições de outro pacote.

Como ponto de partida para explorar e discutir classes existentes, você pode usar o Class Designer para criar diagramas de classe a partir do código.

- [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Resumo: Pontos fortes dos diagramas de classe
 Diagramas de classe ajudam a definir:

- Um glossário comum de termos a serem usados ao discutir as necessidades dos usuários e as entidades que participam do sistema. Consulte [os requisitos do usuário do modelo](../modeling/model-user-requirements.md).

- Tipos que são utilizados por partes do sistema, como componentes, independentemente de sua implementação. Consulte [Modelar a arquitetura do seu aplicativo](../modeling/model-your-app-s-architecture.md).

- Relações, como dependências, entre tipos. Por exemplo, você pode mostrar que um tipo pode ser associado a várias instâncias de outro tipo.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrição**|
|-|-|
|Diagrama de dependência|Defina a arquitetura lógica do sistema no que se refere às classes.<br /><br /> Use validação de dependência para garantir que o código permaneça consistente com o design.<br /><br /> Consulte:<br /><br /> - [Crie diagramas de dependência a partir do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramas de dependência: Referência](../modeling/layer-diagrams-reference.md)<br />- [Diagramas de dependência: Diretrizes](../modeling/layer-diagrams-guidelines.md)<br />- [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)|
|Mapa de código|Visualize a organização e as relações no código existente.<br /><br /> Para identificar classes, seus relacionamentos e seus métodos, crie um mapa de código que mostre esses elementos.<br /><br /> Consulte:<br /><br /> - [Mapear dependências através de suas soluções](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-dependency-diagrams"></a><a name="DescribeLayers"></a>Descreva a arquitetura lógica: diagramas de dependência
 Diagramas de dependência descrevem a arquitetura lógica de um sistema organizando os artefatos em sua solução em grupos abstratos ou *camadas*. Artefatos podem ser muitas coisas, como espaços de nome, projetos, classes, métodos, e assim por diante. As camadas representam e descrevem as funções ou tarefas que os artefatos executam no sistema. Você também pode incluir validação de camadas em suas operações de compilação e check-in para garantir que o código permaneça consistente com seu design.

 Para manter o código consistente com o design, Dinner Now e Lucerna use o seguinte diagrama de dependência para validar seu código à medida que ele evolui:

 ![Diagrama de dependência do sistema de pagamento integrado](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagrama de dependência para jantar agora integrado com Lucerna**

 As camadas deste diagrama se ligam aos artefatos correspondentes da solução Dinner Now e Lucerna. Por exemplo, a camada De negócios é ligada ao namespace DinnerNow.Business e seus membros, que agora incluem a classe PaymentApprover. A camada de acesso a recursos é ligada ao namespace DinnerNow.Data. As setas, ou *dependências,* especificam que apenas a camada Empresa pode usar a funcionalidade na camada Acesso a recursos. À medida que as equipes atualizam seu código, a validação de camadas é realizada regularmente para capturar conflitos à medida que ocorrem e para ajudar as equipes a resolvê-los prontamente.

 As equipes trabalham juntas para integrar e testar gradualmente os dois sistemas. Primeiro, eles garantem que o PaymentApprover e o resto do Dinner Now trabalhem um com o outro com sucesso antes de lidarem com o PaymentProcessing.

 O mapa de código a seguir mostra as novas chamadas entre o Dinner Now e o PaymentApprover:

 ![Gráfico de dependência atualizado com sistema integrado](../modeling/media/depgraph_intsystem.png)

 **Mapa de código com chamadas de método atualizadas**

 Depois que eles confirmam que o sistema funciona como esperado, o Dinner Now comenta o código PaymentProcessing. Os relatórios de validação de camadas estão limpos e o mapa de código resultante mostra que não existem mais dependências do PaymentProcessing:

 ![Gráfico de dependência sem pagamentoprocessamento](../modeling/media/depgraph_nomore.png)

 **Mapa de código sem pagamentoprocessamento**

#### <a name="drawing-a-dependency-diagram"></a>Desenho de um diagrama de dependência

Um diagrama de dependência tem as seguintes características principais:

- *Camadas* descrevem grupos lógicos de artefatos.

- Um *link* é uma associação entre uma camada e um artefato.

     Para criar camadas a partir de artefatos, arraste itens do Solution Explorer, mapas de código, Visualização de Classe ou Navegador de Objetos. Para desenhar novas camadas e, em seguida, vinculá-las a artefatos, use a caixa de ferramentas ou clique com o botão direito do mouse na superfície do diagrama para criar as camadas e arraste os itens para essas camadas.

     O número em uma camada mostra o número de artefatos que estão ligados à camada. Esses artefatos podem ser namespaces, projetos, classes, métodos, e assim por diante. Ao interpretar o número de artefatos em uma camada, lembre-se do seguinte:

  - Se uma camada estiver vinculada a um artefato que contenha outros artefatos, mas não estiver vinculada diretamente a outros artefatos, o número incluirá apenas o artefato vinculado. No entanto, os outros artefatos estão incluídos para análise durante a validação da camada.

       Por exemplo, se uma camada estiver vinculada a um único namespace, o número de artefatos vinculados será 1, mesmo se o namespace contiver classes. Se a camada também tiver links para cada classe no namespace, o número incluirá as classes vinculadas.

  - Se uma camada contiver outras camadas vinculadas a artefatos, a camada de contêiner também estará vinculada a esses artefatos, mesmo que o número na camada de contêiner não inclua esses artefatos.

    Para ver os artefatos vinculados a uma camada, clique com o botão direito do mouse na dependência e clique **em Exibir Links** para abrir o Layer **Explorer**.

- Uma *dependência* indica que uma camada pode usar a funcionalidade em outra camada, mas não vice-versa. Uma *dependência bidirecional* indica que uma camada pode usar a funcionalidade em outra camada, e vice-versa.

     Para exibir as dependências existentes no diagrama de dependência, clique com o botão direito do mouse na superfície do diagrama e clique **em Gerar dependências**. Para descrever as dependências pretendidas, desenhe novas.

Consulte:

- [Criar diagramas de dependência do código](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)

- [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)

- [Validar o código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Resumo: Pontos fortes dos diagramas de dependência

Diagramas de dependência ajudam você:

- Descreva a arquitetura lógica de um sistema de acordo com a funcionalidade de seus artefatos.

- Certifique-se de que o código em desenvolvimento esteja em conformidade com o projeto especificado.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrição**|
|-|-|
|Mapa de código|Visualize a organização e as relações no código existente.<br /><br /> Para criar camadas, gere um mapa de código e, em seguida, agrupe itens no mapa como camadas potenciais. Arraste os grupos do mapa para o diagrama de dependência.<br /><br /> Consulte:<br /><br /> - [Mapear dependências através de suas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />- [Navegue e reorganize mapas de código](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoria**|**Links**|
|-|-|
|**Fóruns**|- [Visual Studio Visualização & Ferramentas de Modelagem](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Visualização & Modelagem SDK (Ferramentas DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Confira também

- [Visualizar código](../modeling/visualize-code.md)
- [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)
- [Use modelos em desenvolvimento ágil](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)
- [Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)
