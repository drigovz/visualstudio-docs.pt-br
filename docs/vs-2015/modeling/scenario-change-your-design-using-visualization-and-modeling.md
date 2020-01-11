---
title: 'Cenário: alterar o design usando a visualização e a modelagem | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0954a38a2667331c537487a706d1d2d13a07f6c4
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850906"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Cenário: alterar o design usando visualização e modelagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verifique se o sistema de software atende às necessidades dos usuários usando as ferramentas de visualização e modelagem no Visual Studio. Use ferramentas como diagramas de Unified Modeling Language (UML), mapas de código, diagramas de camadas e diagramas de classe para:

 Para ver quais versões do Visual Studio oferecem suporte a cada ferramenta, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Esclareça os requisitos dos usuários e os processos de negócios.

- Visualize e explore o código existente.

- Descreva as alterações em um sistema existente.

- Verifique se o sistema atende aos seus requisitos.

- Mantenha o código consistente com o design.

  Este passo a passos:

- Descreve como essas ferramentas podem beneficiar seu projeto de software.

- Mostra como você pode usar essas ferramentas, independentemente de sua abordagem de desenvolvimento, com um cenário de exemplo.

  Para saber mais sobre essas ferramentas e os cenários que eles dão suporte, consulte:

- [Análise e modelagem de arquitetura](../modeling/analyze-and-model-your-architecture.md)

- [Visualizar código](../modeling/visualize-code.md)

- [Criar modelos para o aplicativo](../modeling/create-models-for-your-app.md)

## <a name="ScenarioOverview"></a>Visão geral do cenário
 Este cenário descreve os episódios dos ciclos de vida de desenvolvimento de software de duas empresas fictícias: jantar agora e editora Zuzu. O jantar agora fornece um serviço de entrega de refeição baseado na Web em Seattle. Os clientes podem pedir refeições e pagar por eles no site do jantar agora. Em seguida, os pedidos são enviados para o restaurante local apropriado para entrega. A editora Zuzu, uma empresa em Nova York, executa várias empresas e na Web. Por exemplo, eles executam um site da Web onde os clientes podem postar revisões de restaurante.

 A editora recentemente adquiriu o jantar agora e deseja fazer as seguintes alterações:

- Integre seus sites adicionando recursos de revisão de restaurante ao jantar agora.

- Substitua o sistema de pagamento do jantar agora pelo sistema da Lucerne.

- Expanda o serviço de jantar agora na região.

  O jantar agora usa o SCRUM e a programação extrema. Eles têm cobertura de teste muito alta e muito pouco código sem suporte. Eles minimizam riscos criando versões pequenas, mas em funcionamento, de um sistema e, em seguida, adicionando funcionalidade incrementalmente. Eles desenvolvem seu código em iterações curtas e frequentes. Isso permite que eles adotem alterações com confiança, com frequência o código de refatoração e evite "Big design up inicial".

  A Lucerne mantém uma coleção imensamente maior e complexa de sistemas, alguns dos quais têm mais de 40 anos de idade. Eles têm muito cuidado ao fazer alterações devido à complexidade e ao escopo do código herdado. Eles seguem um processo de desenvolvimento mais rigoroso, preferindo criar soluções detalhadas e documentar o design e as alterações que ocorrem durante o desenvolvimento.

  Ambas as equipes usam diagramas de modelagem no Visual Studio para ajudá-los a desenvolver sistemas que atendam às necessidades dos usuários. Eles usam Team Foundation Server junto com outras ferramentas para ajudá-los a planejar, organizar e gerenciar seu trabalho.

  Para obter mais informações sobre Team Foundation Server, consulte:

- [Planejamento e acompanhamento de trabalho](#PlanningTracking)

- [Testando, validando e verificando o código atualizado](#TestValidateCheckInCode)

## <a name="ModelingDiagramsTools"></a>Funções de diagramas de arquitetura e modelagem no desenvolvimento de software
 A tabela a seguir descreve as funções que essas ferramentas podem reproduzir durante vários e vários estágios do ciclo de vida do desenvolvimento de software:

||**Modelagem de requisitos de usuário**|**Modelagem de processos de negócios**|**Arquitetura do sistema & Design**|**Visualização de código & exploração**|**Verificação**|
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|
|Diagrama de caso de uso (UML)|√|√|||√|
|Diagrama de atividade (UML)|√|√|√||√|
|Diagrama de classe (UML)|√|√|√||√|
|Diagrama de componente (UML)|√|√|√||√|
|Diagrama de sequência (UML)|√|√|√||√|
|Diagrama de DSL (linguagem específica do domínio)|√|√|√|||
|Diagrama de camadas, validação de camada|||√|√|√|
|Mapa de códigos|||√|√|√|
|Designer de Classe (baseado em código)||||√||

 Para desenhar diagramas UML e diagramas de camada, você deve criar um projeto de modelagem como parte de uma solução existente ou um novo. Esses diagramas devem ser criados no projeto de modelagem. Os itens em diagramas UML fazem parte de um modelo comum, e os diagramas UML são exibições desse modelo. Os itens em diagramas de camada estão localizados no projeto de modelagem, mas não são armazenados no modelo comum. Mapas de código e diagramas de classe .NET criados a partir do código existem fora do projeto de modelagem.

 Consulte:

- [Criar projetos e diagramas de modelagem UML](../modeling/create-uml-modeling-projects-and-diagrams.md)

- [Criar diagramas de camada por meio de código](../modeling/create-layer-diagrams-from-your-code.md)

- [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)

- [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [SDK de Modelagem para Visual Studio – linguagens específicas de domínio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

  Para mostrar modos de exibição alternativos da arquitetura, você pode reutilizar determinados elementos do mesmo modelo em vários ou em diagramas diferentes. Por exemplo, você pode arrastar um componente para outro diagrama de componente ou para um diagrama de sequência para que ele possa funcionar como um ator. Consulte [editar modelos e diagramas UML](../modeling/edit-uml-models-and-diagrams.md).

  Ambas as equipes também usam a validação de camada para garantir que o código em desenvolvimento permaneça consistente com o design.

  Consulte:

- [Mantendo o código consistente com o design](#ValidatingCode)

- [Descrever a arquitetura lógica: diagramas de camada](#DescribeLayers)

- [Validar o código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)

  > [!NOTE]
  > Algumas versões do Visual Studio dão suporte à validação de camada e versões somente leitura de mapas de código e diagramas UML para visualização e modelagem. Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="UnderstandingCommunicating"></a>Compreendendo e comunicando informações sobre o sistema
 Não há nenhuma ordem recomendada para usar os diagramas de modelagem do Visual Studio, para que você possa usá-los conforme eles se ajustarem às suas necessidades ou abordagem. Normalmente, as equipes revisitam seus modelos iterativamente e frequentemente em um projeto. Cada diagrama oferece forças específicas para ajudá-lo a entender, descrever e comunicar diferentes aspectos do sistema em desenvolvimento.

 O jantar agora e a Zulu se comunicam entre si e com os participantes do projeto usando diagramas como linguagem comum. Por exemplo, o jantar agora usa diagramas para executar estas tarefas:

- Visualizar o código existente.

- Comunique-se com a Lucerne sobre histórias de usuários novas ou atualizadas.

- Identifique as alterações necessárias para dar suporte a histórias de usuário novas ou atualizadas.

  A Lucerne usa diagramas para executar estas tarefas:

- Saiba mais sobre o processo de negócios do jantar agora.

- Entenda o design do sistema.

- Comunique-se com o jantar agora sobre os requisitos de usuário novos ou atualizados.

- Documentar atualizações no sistema.

  Os diagramas são integrados com o Team Foundation Server para que as equipes possam planejar, gerenciar e controlar seu trabalho com mais facilidade. Por exemplo, eles usam modelos para identificar casos de teste e tarefas de desenvolvimento e para estimar seu trabalho. A Lucerne links Team Foundation Server itens de trabalho a elementos de modelo para que eles possam monitorar o progresso e garantir que o sistema atenda aos requisitos dos usuários. Por exemplo, eles vinculam casos de uso a itens de trabalho de caso de teste para que possam ver se os casos de uso são atendidos quando todos os testes são aprovados.

  Antes que as equipes verifiquem suas alterações, elas validam o código em relação aos testes e ao design executando compilações que incluem validação de camada e testes automatizados. Isso ajuda a garantir que o código atualizado não entre em conflito com o design e interromper a funcionalidade de trabalho anterior.

  Consulte:

- [Compreendendo a função do sistema no processo de negócios](#UnderstandingBPMandSystemDesign)

- [Descrevendo os requisitos de usuário novos ou atualizados](#DescribingURM)

- [Criando testes de modelos](#CreatingTests)

- [Identificando alterações no sistema existente](#DeterminingChanges)

- [Mantendo o código consistente com o design](#ValidatingCode)

- [Dicas gerais para criar e usar modelos](#GeneralTips)

- [Planejamento e acompanhamento de trabalho](#PlanningTracking)

- [Testando, validando e verificando o código atualizado](#TestValidateCheckInCode)

### <a name="UnderstandingBPMandSystemDesign"></a>Compreendendo a função do sistema no processo de negócios
 A Lucerne quer saber mais sobre o processo de negócios do jantar agora. Eles criam os diagramas a seguir para esclarecer sua compreensão com o jantar agora com mais facilidade:

|**Diagrama**|**Descrita**|
|-----------------|-------------------|
|*Diagrama de caso de uso (UML)*<br /><br /> Consulte:<br /><br /> [diagramas de caso de uso de UML -   : referência](../modeling/uml-use-case-diagrams-reference.md)<br />[diagramas de caso de uso de UML -   : diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)|-As atividades que o jantar agora suporta<br />-As pessoas e os sistemas externos que executam as atividades<br />-Os principais componentes do sistema que oferecem suporte a cada atividade<br />-As partes do processo comercial que estão fora do escopo do sistema atual, por exemplo, entrega de alimentos|
|*Diagrama de atividade (UML)*<br /><br /> Consulte:<br /><br /> [diagramas de atividade de UML -   : referência](../modeling/uml-activity-diagrams-reference.md)<br />[diagramas de atividade de UML -   : diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|O fluxo de etapas que ocorrem quando um cliente cria um pedido|
|*Diagrama de classe (UML)*<br /><br /> Consulte:<br /><br /> -   [diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)<br />-   [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)|As entidades de negócios e os termos usados em discussão e as relações entre essas entidades. Por exemplo, o item de ordem e de menu fazem parte do vocabulário nesse cenário.|

 Por exemplo, a Lucerne cria o diagrama de caso de uso a seguir para entender as tarefas que são executadas no site do jantar agora e quem as executa:

 ![Diagrama de Casos de Uso UML](../modeling/media/uml-usecase.png "UML_UseCase")

 **Diagrama de Casos de Uso UML**

 O diagrama de atividade a seguir descreve o fluxo de etapas quando um cliente cria um pedido no site do jantar agora. Nesta versão, os elementos de comentário identificam as funções e as linhas criam *raias*, que organizam as etapas por função:

 ![Diagrama de Atividade UML](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")

 **Diagrama de Atividade UML**

 O diagrama de classe a seguir descreve as entidades que participam do processo de pedido:

 ![Diagrama de Classe UML](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")

 **Diagrama de Classe UML**

### <a name="DescribingURM"></a>Descrevendo os requisitos de usuário novos ou atualizados
 A Lucerne deseja adicionar funcionalidade ao sistema de jantar agora para que os clientes possam ler e contribuir com revisões de restaurantes. Eles atualizam os diagramas a seguir para que eles possam descrever e discutir esse novo requisito com o jantar agora:

|**Diagrama**|**Descrita**|
|-----------------|-------------------|
|*Diagrama de caso de uso (UML)*<br /><br /> Consulte:<br /><br /> [diagramas de caso de uso de UML -   : referência](../modeling/uml-use-case-diagrams-reference.md)<br />[diagramas de caso de uso de UML -   : diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)|Um novo caso de uso para "escrever uma revisão de restaurante"|
|*Diagrama de atividade (UML)*<br /><br /> Consulte:<br /><br /> [diagramas de atividade de UML -   : referência](../modeling/uml-activity-diagrams-reference.md)<br />[diagramas de atividade de UML -   : diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|As etapas que ocorrem quando um cliente deseja escrever uma revisão de restaurante|
|*Diagrama de classe (UML)*<br /><br /> Consulte:<br /><br /> -   [diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)<br />-   [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)|Os dados necessários para armazenar uma revisão|

 Por exemplo, o diagrama de caso de uso a seguir inclui um novo caso de uso de "análise de gravação" para representar o novo requisito. Ele é realçado em laranja no diagrama para facilitar a identificação:

 ![Diagrama de Casos de Uso UML](../modeling/media/uml-writerev.png "UML_WriteRev")

 **Diagrama de caso de uso UML**

 O diagrama de atividade a seguir inclui novos elementos em laranja para descrever o fluxo de etapas no novo caso de uso:

 ![Diagrama de Atividade UML](../modeling/media/uml-writereview.png "UML_WriteReview")

 **Diagrama de atividade UML**

 O diagrama de classe a seguir inclui uma nova classe de revisão e suas relações com outras classes para que as equipes possam discutir seus detalhes. Observe que um cliente e um restaurante podem ter várias revisões:

 ![Diagrama de Classe UML](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")

 **Diagrama de classes UML**

### <a name="CreatingTests"></a>Criando testes de modelos
 Ambas as equipes concordam que precisam de um conjunto completo de testes para o sistema e seus componentes antes de fazer qualquer alteração. A Lucerne tem uma equipe especializada que executa testes no nível do sistema e do componente. Eles reutilizam os testes criados pelo jantar agora e estruturam esses testes usando os diagramas UML:

- Cada caso de uso é representado por um ou vários testes. Os elementos no diagrama de caso de uso do link para itens de trabalho de caso de teste no Team Foundation Server.

- Cada fluxo em um diagrama de atividade ou diagrama de sequência no nível do sistema é vinculado a um único teste no mínimo. A equipe de teste garante sistematicamente que eles testam todos os caminhos possíveis por meio do diagrama de atividade.

- Os termos usados para descrever os testes são baseados nos termos definidos pelos diagramas de caso de uso, de classe e de atividade.

  Conforme os requisitos mudam e os diagramas são atualizados para refletir essas alterações, os testes também são atualizados. Um requisito é considerado atendido somente quando os testes são aprovados. Quando possível ou práticos, os testes são definidos e baseados em diagramas UML antes do início da implementação.

  Consulte:

- [Desenvolver testes por meio de um modelo](../modeling/develop-tests-from-a-model.md)

- [Validar o modelo UML](../modeling/validate-your-uml-model.md)

### <a name="DeterminingChanges"></a>Identificando alterações no sistema existente
 Agora, o jantar deve estimar o custo da reunião do novo requisito. Isso depende, em parte, de quanto essa alteração afetará outras partes do sistema. Para ajudá-los a entender isso, um dos jantares, agora, os desenvolvedores criam esses mapas e diagramas a partir do código existente:

|**Mapa ou diagrama**|**programas**|
|------------------------|---------------|
|*Mapa de códigos*<br /><br /> Consulte:<br /><br /> -   [mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />-   [procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Personalizar mapas de código editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Dependências e outras relações no código.<br /><br /> Por exemplo, o jantar agora pode começar examinando mapas de código assembly para obter uma visão geral dos assemblies e suas dependências. Eles podem analisar os mapas para explorar os namespaces e as classes nesses assemblies.<br /><br /> Agora, o jantar também pode criar mapas para explorar áreas específicas e outros tipos de relações no código. Eles usam Gerenciador de Soluções para localizar e selecionar as áreas e relações que os interessam.|
|*Diagrama de classe baseado em código*<br /><br /> Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Classes existentes no código|

 Por exemplo, o desenvolvedor cria um mapa de código. Ela ajusta seu escopo para se concentrar nas áreas que serão afetadas pelo novo cenário. Essas áreas são selecionadas e realçadas no mapa:

 ![Grafo de dependência de namespace](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")

 **Mapa de código do namespace**

 O desenvolvedor expande os namespaces selecionados para ver suas classes, métodos e relações:

 ![Grafo de dependência de namespace expandido](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")

 **Mapa de código de namespace expandido com links entre grupos visíveis**

 O desenvolvedor examina o código para localizar as classes e os métodos afetados. Para ver os efeitos de cada alteração ao fazê-las, gere novamente os mapas de código após cada alteração. Consulte [Visualizar código](../modeling/visualize-code.md).

 Para descrever as alterações em outras partes do sistema, como componentes ou interações, a equipe pode desenhar esses elementos em quadros de comunicações. Eles também podem desenhar os seguintes diagramas no Visual Studio para que os detalhes possam ser capturados, gerenciados e compreendidos por ambas as equipes:

|**Diagrama**|**Descrita**|
|------------------|-------------------|
|*Diagrama de atividade (UML)*<br /><br /> Consulte:<br /><br /> [diagramas de atividade de UML -   : referência](../modeling/uml-activity-diagrams-reference.md)<br />[diagramas de atividade de UML -   : diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|O fluxo de etapas que ocorrem quando o sistema observa que um cliente faz um pedido de um restaurante novamente, solicitando que o cliente escreva uma revisão.|
|*Diagrama de classe (UML)*<br /><br /> Consulte:<br /><br /> -   [diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)<br />-   [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)|Classes lógicas e suas relações. Por exemplo, uma nova classe é adicionada para descrever uma **revisão** e suas relações com outras entidades, como **restaurante**, **menu**e **cliente**.<br /><br /> Para associar as revisões a um cliente, o sistema deve armazenar os detalhes do cliente. Um diagrama de classes UML pode ajudar a esclarecer esses detalhes.|
|*Diagrama de classe baseado em código*<br /><br /> Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Classes existentes no código.|
|*Diagrama de componente (UML)*<br /><br /> Consulte:<br /><br /> -   [diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)<br />-   [diagramas de componentes UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md)|As partes de alto nível do sistema, como o site do jantar agora e suas interfaces. Essas interfaces definem como os componentes interagem entre si por meio dos métodos ou serviços que eles fornecem e consomem.|
|*Diagrama de sequência (UML)*<br /><br /> Consulte:<br /><br /> -   [diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md)<br />-   [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)|A sequência de interações entre instâncias.|

 Por exemplo, o diagrama de componente a seguir mostra o novo componente, que é parte do componente de site do jantar agora. O componente ReviewProcessing manipula a funcionalidade de criação de revisões e aparece realçado em laranja:

 ![Diagrama de Componente UML](../modeling/media/uml-internal.png "UML_Internal")

 **Diagrama de componente UML**

 O diagrama de sequência a seguir mostra a sequência de interações que ocorrem quando o site do jantar agora verifica se o cliente foi solicitado de um restaurante antes. Se isso for verdadeiro, ele solicitará que o cliente crie uma revisão, que é enviada para o restaurante e publicada pelo site:

 ![Diagrama de sequência UML](../modeling/media/uml-revsystem.png "UML_RevSystem")

 **Diagrama de sequência UML**

### <a name="ValidatingCode"></a>Mantendo o código consistente com o design
 Agora, o jantar deve garantir que o código atualizado permaneça consistente com o design. Eles criam diagramas de camada que descrevem as camadas de funcionalidade no sistema, especificam as dependências permitidas entre elas e associam os artefatos de solução a essas camadas.

|**Diagrama**|**Descrita**|
|-----------------|-------------------|
|*Diagrama de camada*<br /><br /> Consulte:<br /><br /> -   [criar diagramas de camada do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />[diagramas de camada de -   : referência](../modeling/layer-diagrams-reference.md)<br />[diagramas de camada de -   : diretrizes](../modeling/layer-diagrams-guidelines.md)<br />-   [validar o código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)|A arquitetura lógica do código.<br /><br /> Um diagrama de camada organiza e mapeia os artefatos em uma solução de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para grupos abstratos chamados *camadas*. Essas camadas identificam as funções, as tarefas ou as funções que esses artefatos executam no sistema.<br /><br /> Os diagramas de camada são úteis para descrever o design pretendido do sistema e validar o código em evolução nesse design.<br /><br /> Para criar camadas, arraste itens de Gerenciador de Soluções, mapas de código, Modo de Exibição de Classe e pesquisador de objetos. Para desenhar novas camadas, use a caixa de ferramentas ou clique com o botão direito do mouse na superfície do diagrama.<br /><br /> Para exibir as dependências existentes, clique com o botão direito do mouse na superfície do diagrama de camadas e clique em **gerar dependências**. Para especificar as dependências pretendidas, desenhe novas dependências.|

 Por exemplo, o diagrama de camada a seguir descreve as dependências entre as camadas e o número de artefatos associados a cada camada:

 ![Diagrama de camada do sistema de pagamento integrado](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Diagrama de Camada**

 Para garantir que conflitos com o design não ocorram durante o desenvolvimento de código, as equipes usam a validação de camada em compilações que são executadas no Team Foundation Build. Eles também criam uma tarefa personalizada do MSBuild para exigir a validação de camada em suas operações de check-in. Eles usam relatórios de compilação para coletar erros de validação.

 Consulte:

- [Definir o processo de compilação](https://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)

- [Usar um processo de compilação de check-in restringido para validar as alterações](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)

- [Personalizar o modelo de processo de compilação](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

### <a name="GeneralTips"></a>Dicas gerais para criar e usar modelos

- A maioria dos diagramas consiste em nós que estão conectados por linhas. Para cada tipo de diagrama, a caixa de ferramentas fornece diferentes tipos de nós e linhas.

   Para abrir a caixa de ferramentas, no menu **Exibir** , clique em **caixa de ferramentas**.

- Para criar um nó, arraste-o da caixa de ferramentas para o diagrama. Determinados tipos de nós devem ser arrastados para nós existentes. Por exemplo, em um diagrama de componente, uma nova porta deve ser adicionada a um componente existente.

- Para criar uma linha ou uma conexão, clique na ferramenta apropriada na caixa de ferramentas, clique no nó de origem e, em seguida, clique no nó de destino. Algumas linhas podem ser criadas somente entre determinados tipos de nós. Quando você move o ponteiro sobre uma possível origem ou destino, o ponteiro indica se você pode criar uma conexão.

- Ao criar itens em diagramas UML, você também os adiciona a um modelo comum. Os diagramas UML em um projeto de modelagem são exibições desse modelo. Os itens em um diagrama de camada fazem parte do projeto de modelagem, mesmo que não sejam armazenados no modelo comum.

   Para ver o modelo, no menu **arquitetura** , aponte para **Windows**e clique em Gerenciador de **modelos UML**.

- Em alguns casos, você pode arrastar determinados itens do **Gerenciador de modelos UML** para um diagrama UML. Alguns elementos dentro do mesmo modelo podem ser usados em vários ou em diagramas diferentes para mostrar modos de exibição alternativos da arquitetura. Por exemplo, você pode arrastar um componente para outro diagrama de componente ou para um diagrama de sequência para usar como um ator.

- O Visual Studio dá suporte a 2.1.2 UML. Esta visão geral descreve apenas os principais recursos dos diagramas UML nesta versão, mas há muitos livros que discutem o UML e seu uso em detalhes.

  Consulte [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md).

### <a name="PlanningTracking"></a>Planejamento e acompanhamento de trabalho
 Os diagramas de modelagem do Visual Studio são integrados com Team Foundation Server para que você possa planejar, gerenciar e acompanhar o trabalho com mais facilidade. As duas equipes usam modelos para identificar casos de teste e tarefas de desenvolvimento e para estimar seu trabalho. A Lucerne cria e vincula Team Foundation Server itens de trabalho a elementos de modelo, como casos de uso ou componentes. Isso ajuda a monitorar seu progresso e rastrear seu trabalho de volta aos requisitos dos usuários. Isso ajuda a garantir que suas alterações continuem a atender a esses requisitos.

 À medida que seu trabalho progride, as equipes atualizam seus itens de trabalho para refletir o tempo gasto em suas tarefas. Eles também monitoram e relatam o status em seu trabalho usando os seguintes recursos de Team Foundation Server:

- *Relatórios de Burndown* diários que mostram se eles vão concluir o trabalho planejado no tempo esperado. Eles geram outros relatórios semelhantes de Team Foundation Server para acompanhar o progresso dos bugs.

- Uma *planilha de iteração* que usa o Microsoft Excel para ajudar a equipe a monitorar e balancear a carga de trabalho entre seus membros. Esta planilha está vinculada a Team Foundation Server e fornece o foco para discussão durante suas reuniões de progresso regulares.

- Um *painel de desenvolvimento* que usa o Office Project para manter a equipe informada sobre informações importantes do projeto.

  Consulte:

- [Acompanhar o trabalho usando Visual Studio Team Services ou Team Foundation Server](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)

- [Vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md)

- [Gráficos, painéis e relatórios para o Visual Studio ALM](https://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)

- [Criar sua pendência e tarefas usando o projeto](https://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)

### <a name="TestValidateCheckInCode"></a>Testando, validando e verificando o código
 Conforme as equipes concluem cada tarefa, elas verificam seu código no controle de versão do Team Foundation e recebem lembretes de Team Foundation Server, caso se esqueçam. Antes que Team Foundation Server aceite seus check-ins, as equipes executam testes de unidade e a validação de camada para verificar o código em relação aos casos de teste e ao design. Eles usam Team Foundation Server para executar compilações, testes de unidade automatizados e validação de camada regularmente. Isso ajuda a garantir que o código atenda aos seguintes critérios:

- Funciona.

- Ele não interrompe o código que estava funcionando anteriormente.

- Ele não entra em conflito com o design.

  Agora, o jantar tem uma grande coleção de testes automatizados, que a Lucerne pode reutilizar porque quase todos ainda se aplicam. A Lucerne também pode criar esses testes e adicionar novos para abranger novas funcionalidades. Ambos também usam o Visual Studio para executar testes manuais.

  Para garantir que o código esteja de acordo com o design, as equipes configuram suas compilações no Team Foundation Build para incluir a validação de camada. Se ocorrer algum conflito, um relatório será gerado com os detalhes.

  Consulte:

- [Testando o aplicativo](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)

- [Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)

- [Usar o controle de versão](https://docs.microsoft.com/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Compilar o aplicativo](/azure/devops/pipelines/index)

## <a name="UpdatingSystem"></a>Atualizando o sistema usando visualização e modelagem
 A Lucerne e o jantar agora devem integrar seus sistemas de pagamento. As seções a seguir mostram os diagramas de modelagem no Visual Studio que os ajudam a executar esta tarefa:

- [Entender os requisitos do usuário: diagramas de caso de uso](#UnderstandUseCases)

- [Entenda o processo comercial: diagramas de atividade](#UnderstandActivities)

- [Descrever a estrutura do sistema: diagramas de componentes](#DescribeComponents)

- [Descrever as interações: diagramas de sequência](#DescribeSequence)

- [Visualizar código existente: mapas de código](#VisualizeCode)

- [Definir um glossário de tipos: diagramas de classe](#DefineClasses)

- [Descrever a arquitetura lógica: diagramas de camada](#DescribeLayers)

  Consulte:

- [Criar modelos para o aplicativo](../modeling/create-models-for-your-app.md)

- [Visualizar código](../modeling/visualize-code.md)

- [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)

- [Requisitos de usuário do modelo](../modeling/model-user-requirements.md)

- [Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)

### <a name="UnderstandUseCases"></a>Entender os requisitos do usuário: diagramas de caso de uso
 Diagramas de caso de uso resumem as atividades que um sistema suporta e quem executa essas atividades. A Lucerne usa um diagrama de caso de uso para aprender o seguinte sobre o sistema do jantar agora:

- Os clientes criam pedidos.

- Pedidos de recebimento de restaurantes.

- O gateway do processador de pagamento externo, que o sistema de pagamento do jantar agora usa para validar pagamentos, está fora do escopo do site.

  O diagrama também mostra como alguns dos principais casos de uso dividem-se em casos de uso menores. A Lucerne quer usar seu próprio sistema de pagamento. Eles destacam o caso de uso de pagamento de processo em uma cor diferente para indicar que ele requer alterações:

  ![Realçando o pagamento do processo em um diagrama de caso de uso](../modeling/media/uml-processpay.png "UML_ProcessPay")

  **Realçando o pagamento do processo no diagrama de caso de uso**

  Se o tempo de desenvolvimento for curto, a equipe poderá discutir se desejam permitir que os clientes paguem restaurantes diretamente. Para mostrar isso, eles substituirão o caso de uso do pagamento do processo por um que esteja fora do jantar agora no limite do sistema. Em seguida, eles vinculariam o cliente diretamente ao restaurante, indicando que o jantar agora só processaria pedidos:

  ![Reescopor o restaurante no diagrama de caso de uso](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")

  **Reescopor o restaurante no diagrama de caso de uso**

  Consulte:

- [Diagramas de caso de uso UML: referência](../modeling/uml-use-case-diagrams-reference.md)

- [Diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="drawing-a-use-case-diagram"></a>Desenho de um diagrama de caso de uso
 Um diagrama de caso de uso tem os seguintes recursos principais:

- Os *atores* representam funções desempenhadas por pessoas, organizações, computadores ou sistemas de software. Por exemplo, cliente, restaurante e o sistema de pagamento do jantar agora são atores.

- *Casos de uso* representam interações entre atores e o sistema em desenvolvimento.  Eles podem representar qualquer escala de interação de um único clique do mouse ou mensagem para uma transação estendida por vários dias.

- *Associações* vinculam atores a casos de uso.

- Um caso de uso maior pode *incluir* menores, por exemplo, criar pedido inclui selecionar restaurante. Você pode *estender* um caso de uso, que adiciona metas e etapas ao caso de uso estendido, para indicar que o caso de uso ocorre somente sob determinadas condições. Os casos de uso também podem ser herdados uns dos outros.

- Um *subsistema* representa o sistema de software que está em desenvolvimento ou um de seus componentes. É uma caixa grande que contém casos de uso. Um diagrama de caso de uso esclarece o que está dentro ou fora do limite do subsistema. Para indicar que o usuário deve realizar determinadas metas de outras maneiras, desenhe os casos de uso fora do limite do subsistema.

- Os *artefatos* vinculam elementos no diagrama a outros diagramas ou documentos.

  Consulte:

- [Diagramas de caso de uso UML: referência](../modeling/uml-use-case-diagrams-reference.md)

- [Diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="summary-strengths-of-use-case-diagrams"></a>Resumo: pontos fortes de diagramas de caso de uso
 Os diagramas de caso de uso ajudam você a Visualizar:

- As atividades às quais um sistema dá suporte ou não oferece suporte

- As pessoas e os sistemas externos que executam essas atividades

- Os principais componentes do sistema que oferecem suporte a cada atividade, que você pode representar como subsistemas aninhados dentro do sistema pai

- Como um caso de uso pode ser dividido em pequenas partes ou variações

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrita**|
|-----------------|-------------------|
|Diagrama de atividade|O fluxo de etapas em um caso de uso e aqueles que executam essas etapas nesse caso de uso.<br /><br /> Os nomes dos casos de uso freqüentemente espelham as etapas em um diagrama de atividade. Os diagramas de atividade dão suporte a elementos como decisões, mesclagens, entradas e saídas, fluxos simultâneos e assim por diante.<br /><br /> Consulte:<br /><br /> [diagramas de atividade de UML -   : referência](../modeling/uml-activity-diagrams-reference.md)<br />[diagramas de atividade de UML -   : diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|
|Diagrama de sequência|A sequência de interações entre os participantes em um caso de uso.<br /><br /> Consulte:<br /><br /> -   [diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md)<br />-   [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)|
|Diagrama de classe (UML)|As entidades ou os tipos que participam do caso de uso.<br /><br /> Consulte:<br /><br /> -   [diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)<br />-   [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)|

### <a name="UnderstandActivities"></a>Entenda o processo comercial: diagramas de atividade
 Os diagramas de atividade descrevem o fluxo de etapas em um processo de negócios e fornecem uma maneira simples de comunicar o fluxo de trabalho. Um projeto de desenvolvimento pode ter vários diagramas de atividade. Normalmente, uma atividade abrange todas as ações resultantes de uma ação externa, como ordenar uma refeição, atualizar um menu ou adicionar um novo restaurante à empresa. Uma atividade também pode descrever os detalhes de uma ação complexa.

 A Lucerne atualiza o diagrama de atividade a seguir para mostrar que a Lucerne processa o pagamento e paga o restaurante. Eles substituem o sistema de pagamento do jantar agora pelo sistema de pagamento Zulu como realçado:

 ![Sistema de pagamento Zulu no diagrama de atividade](../modeling/media/uml-lucerne.png "UML_Lucerne")

 **Substituindo o sistema de pagamento do jantar agora no diagrama de atividade**

 O diagrama atualizado ajuda a Lucerne e o jantar agora a visualizar onde o sistema de pagamento da Lucerne se encaixa no processo de negócios. Nesta versão, os comentários são usados para identificar as funções que executam as etapas. As linhas são usadas para criar *raias*, que organizam as etapas por função.

 As equipes também podem considerar a discussão de uma história alternativa em que o cliente paga o restaurante, em vez de ser entregue. Isso criaria requisitos diferentes para o sistema de software.

 Anteriormente, o jantar agora desenhava esses diagramas em um quadro de comunicações ou no PowerPoint. Agora, eles também usam o Visual Studio para desenhar esses diagramas para que ambas as equipes possam capturar, compreender e gerenciar os detalhes.

 Consulte:

- [Diagramas de atividade UML: referência](../modeling/uml-activity-diagrams-reference.md)

- [Diagramas de atividade UML: diretrizes](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="drawing-an-activity-diagram"></a>Desenhando um diagrama de atividade
 Um diagrama de atividade tem os seguintes recursos principais:

- Um *nó inicial* que indica a primeira ação da atividade.

   O diagrama sempre deve ter um desses nós.

- *Ações* que descrevem as etapas em que o usuário ou o software executa uma tarefa.

- *Fluxos de controle* que mostram o fluxo entre as ações.

- *Nós de decisão* que representam ramificações condicionais no fluxo.

- *Nós de bifurcação* que dividem fluxos únicos em fluxos simultâneos.

- *Nós finais da atividade* que mostra as extremidades da atividade.

   Embora esses nós sejam opcionais, é útil incluí-los no diagrama para mostrar onde a atividade termina.

  Consulte:

- [Diagramas de atividade UML: referência](../modeling/uml-activity-diagrams-reference.md)

- [Diagramas de atividade UML: diretrizes](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="summary-strengths-of-activity-diagrams"></a>Resumo: pontos fortes dos diagramas de atividade
 Os diagramas de atividade ajudam você a visualizar e descrever o fluxo de controle e as informações entre as ações de um negócio, sistema ou programa. Essa é uma maneira simples e útil de descrever o fluxo de trabalho ao se comunicar com outras pessoas.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrição**|
|-----------------|---------------------|
|Diagrama de caso de uso|Resuma as atividades que cada ator executa.<br /><br /> Consulte:<br /><br /> [diagramas de caso de uso de UML -   : referência](../modeling/uml-use-case-diagrams-reference.md)<br />[diagramas de caso de uso de UML -   : diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)|
|Diagrama de componente|Visualize o sistema como uma coleção de partes reutilizáveis que fornecem ou consomem o comportamento por meio de um conjunto bem definido de interfaces.<br /><br /> Consulte:<br /><br /> -   [diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)<br />-   [diagramas de componentes UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md)|

### <a name="DescribeComponents"></a>Descrever a estrutura do sistema: diagramas de componentes
 Os diagramas de componente descrevem um sistema como uma coleção de partes separáveis que fornecem ou consomem o comportamento por meio de um conjunto bem definido de interfaces. As partes podem estar em qualquer escala e podem se conectar de qualquer maneira.

 Para ajudar a Lucerne e o jantar agora Visualizar e discutir os componentes do sistema e suas interfaces, eles criam os seguintes diagramas de componente:

 ![Componentes externos no sistema de pagamento](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")

 **Componentes do jantar agora sistema de pagamento**

 Este diagrama mostra diferentes tipos de componentes e suas *dependências*. Por exemplo, o site do jantar agora e o sistema de pagamento da Lucerne exigem que o gateway do processador de pagamento externo valide pagamentos. As setas entre os componentes representam as dependências que indicam quais componentes exigem a funcionalidade de outros componentes.

 Para usar o sistema de pagamento da Lucerne, o site do jantar agora deve ser atualizado para usar as interfaces PaymentApproval e PayableInsertion no sistema de pagamento da Lucerne.

 O diagrama a seguir mostra uma configuração específica de componentes para o site do jantar agora. Essa configuração indica que qualquer instância do site consiste em quatro *partes*:

- CustomerProcessing

- OrderProcessing

- ReviewProcessing

- PaymentProcessing

  Essas partes são instâncias dos tipos de componentes especificados e são conectadas da seguinte maneira:

  ![Componentes no site do jantar agora](../modeling/media/uml-dinnernow.png "UML_DinnerNow")

  **Componentes no site do jantar agora**

  O site do jantar agora delega seu comportamento a essas partes, que lidam com as funções do site. As setas entre o componente pai e seus componentes Membros mostram as *delegações* que indicam quais partes manipulam as mensagens que o pai recebe ou envia por meio de suas interfaces.

  Nessa configuração, o componente PaymentProcessing processa pagamentos de clientes. Portanto, ele deve ser atualizado para integrar-se ao sistema de pagamento da Lucerne. Em outros cenários, podem existir várias instâncias de um tipo de componente no mesmo componente pai.

  Consulte:

- [Diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)

- [Diagramas de componente UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="drawing-a-component-diagram"></a>Desenhando um diagrama de componente
 Um diagrama de componente tem os seguintes recursos principais:

- *Componentes* que representam partes separáveis da funcionalidade do sistema.

- *Portas de interface fornecidas* que representam grupos de mensagens ou chamadas que componentes implementam e são usados por outros componentes ou sistemas externos.

- *As portas de interface necessárias* que representam grupos de mensagens ou chamadas que os componentes enviam a outros componentes ou sistemas externos. Esse tipo de porta descreve as operações que um componente pelo menos espera de outros componentes ou sistemas externos.

- As *partes* são membros de componentes e normalmente são instâncias de outros componentes. Uma parte é uma parte do design interno do componente pai.

- As *dependências* que indicam componentes exigem a funcionalidade de outros componentes.

- As *delegações* que indicam partes de um componente manipulam as mensagens enviadas ou recebidas pelo componente pai.

  Consulte:

- [Diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)

- [Diagramas de componente UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="summary-strengths-of-component-diagrams"></a>Resumo: pontos fortes dos diagramas de componente
 Os diagramas de componente ajudam a Visualizar:

- O sistema como uma coleção de partes separáveis, independentemente de seu idioma ou estilo de implementação.

- Componentes com interfaces bem definidas, tornando o design mais fácil de entender e atualizar quando os requisitos mudam.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrição**|
|-----------------|---------------------|
|Mapa de códigos|Visualize a organização e as relações no código existente.<br /><br /> Para identificar os candidatos aos componentes, crie um mapa de código e agrupe os itens por sua função no sistema.<br /><br /> Consulte:<br /><br /> -   [mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md)|
|Diagrama de sequência|Visualize a sequência de interações entre componentes ou as partes dentro de um componente.<br /><br /> Para criar uma linha de vida em um diagrama de sequência de um componente, clique com o botão direito do mouse no componente e clique em **Criar linha de vida**.<br /><br /> Consulte:<br /><br /> -   [diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md)<br />-   [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)|
|Diagrama de classe (UML)|Defina as interfaces nas portas fornecidas ou necessárias e as classes que implementam a funcionalidade dos componentes.<br /><br /> Consulte:<br /><br /> -   [diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)<br />-   [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)|
|Diagrama de camada|Descreva a arquitetura lógica do sistema à medida que ele se relaciona com os componentes do. Use a validação de camada para garantir que o código permaneça consistente com o design.<br /><br /> Consulte:<br /><br /> -   [criar diagramas de camada do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />[diagramas de camada de -   : referência](../modeling/layer-diagrams-reference.md)<br />[diagramas de camada de -   : diretrizes](../modeling/layer-diagrams-guidelines.md)<br />-   [validar o código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)|
|Diagrama de atividade|Visualize o processamento interno que os componentes executam em resposta a mensagens de entrada.<br /><br /> Consulte:<br /><br /> [diagramas de atividade de UML -   : referência](../modeling/uml-activity-diagrams-reference.md)<br />[diagramas de atividade de UML -   : diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|

### <a name="VisualizeCode"></a>Visualizar código existente: mapas de código
 Os mapas de código mostram a organização atual e as relações no código. Os itens são representados por *nós* no mapa e as relações são representadas por *links*. Os mapas de código podem ajudá-lo a executar os seguintes tipos de tarefas:

- Explore um código desconhecido.

- Entenda onde e como uma alteração proposta pode afetar o código existente.

- Encontre áreas de complexidade, camadas ou padrões naturais ou outras áreas que podem se beneficiar do aprimoramento.

  Por exemplo, o jantar agora deve estimar o custo da atualização do componente PaymentProcessing. Isso depende, em parte, de quanto essa alteração afetará outras partes do sistema. Para ajudá-los a entender isso, um dos jantares, agora, os desenvolvedores geram mapas de código do código e ajusta o foco do escopo nas áreas que podem ser afetadas pela alteração.

  O mapa a seguir mostra as dependências entre a classe PaymentProcessing e outras partes do sistema do jantar agora, que aparecem selecionadas:

  ![Grafo de dependência para o sistema de pagamento do jantar agora](../modeling/media/dep-dnpayment.png "Dep_DNPayment")

  **Mapa de códigos para o sistema de pagamento do jantar agora**

  O desenvolvedor explora o mapa expandindo a classe PaymentProcessing e selecionando seus membros para ver as áreas potencialmente afetadas:

  ![Métodos dentro de PaymentProcessing e dependências](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")

  **Métodos dentro da classe PaymentProcessing e suas dependências**

  Eles geram o mapa a seguir para o sistema de pagamento Zulu para inspecionar suas classes, métodos e dependências. A equipe vê que o sistema da Lucerne também pode exigir trabalho para interagir com as outras partes do jantar agora:

  ![Grafo de dependência para o sistema de pagamento Zulu](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")

  **Mapa de códigos para o sistema de pagamento da Lucerne**

  Ambas as equipes trabalham juntas para determinar as alterações necessárias para integrar os dois sistemas. Eles decidem refatorar parte do código para que seja mais fácil de atualizar. A classe PaymentApprover será movida para o namespace DinnerNow. Business e exigirá alguns novos métodos. As classes do jantar agora que lidam com as transações terão seu próprio namespace. As equipes criam e usam itens de trabalho para planejar, organizar e acompanhar seu trabalho. Eles vinculam os itens de trabalho a elementos de modelo onde são úteis.

  Depois de reorganizar o código, as equipes geram um novo mapa de código para ver a estrutura e as relações atualizadas:

  ![Grafo de dependência com código reorganizado](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")

  **Mapa de código com código reorganizado**

  Esse mapa mostra que a classe PaymentApprover agora está no namespace DinnerNow. Business e tem alguns métodos novos. Agora, as classes Transaction do jantar agora têm seu próprio namespace PaymentSystem, o que torna mais fácil lidar com esse código posteriormente.

#### <a name="creating-a-code-map"></a>Criando um mapa de código

- Para obter uma visão geral rápida do código-fonte, siga estas etapas para gerar um mapa de código:

     No menu **arquitetura** , clique em **gerar mapa de código para solução**.

     Para obter uma visão geral rápida do código compilado, crie um mapa de código em branco e arraste arquivos de assembly ou arquivos binários para a superfície do mapa.

- Para explorar um código específico ou itens de solução, use Gerenciador de Soluções para selecionar itens e relações que você deseja visualizar. Em seguida, você pode gerar um novo mapa ou adicionar itens selecionados a um mapa existente. Consulte [mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md).

- Para ajudá-lo a explorar o mapa, reorganize o layout para que ele se adapte aos tipos de tarefas que você deseja executar.

     Por exemplo, para visualizar a disposição em camadas no código, selecione um layout de árvore. Consulte [procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Resumo: pontos fortes dos mapas de código
 Os mapas de código ajudam você a:

- Saiba mais sobre a organização e as relações no código existente.

- Identifique áreas que podem ser afetadas por uma alteração proposta.

- Encontre áreas de complexidade, padrões, camadas ou outras áreas que você pode melhorar para tornar o código mais fácil de manter, alterar e reutilizar.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrita**|
|-----------------|-------------------|
|Diagrama de camada|A arquitetura lógica do sistema. Use a validação de camada para garantir que o código permaneça consistente com o design.<br /><br /> Para ajudá-lo a identificar camadas existentes ou camadas pretendidas, crie um mapa de código e itens relacionados ao grupo. Para criar um diagrama de camada, consulte:<br /><br /> -   [criar diagramas de camada do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />[diagramas de camada de -   : diretrizes](../modeling/layer-diagrams-guidelines.md)|
|Diagrama de componente|Componentes, suas interfaces e suas relações.<br /><br /> Para ajudá-lo a identificar componentes, crie um mapa de código e agrupe itens por sua função no sistema.<br /><br /> Consulte:<br /><br /> -   [diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)<br />-   [diagramas de componentes UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md)|
|Diagrama de classe (UML)|Classes, seus atributos e operações e suas relações.<br /><br /> Para ajudá-lo a identificar esses elementos, crie um diagrama de classe UML que mostre esses elementos.<br /><br /> Consulte:<br /><br /> -   [diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)<br />-   [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)|
|Diagrama de classe (baseado em código)|Classes existentes no código para um projeto específico.<br /><br /> Para visualizar e modificar uma classe existente no código, use Designer de Classe.<br /><br /> Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|

### <a name="DescribeSequence"></a>Descrever as interações: diagramas de sequência
 Os diagramas de sequência descrevem uma série de interações entre partes de um sistema. As partes podem ser de qualquer escala. Por exemplo, eles podem variar de objetos individuais em um programa para grandes subsistemas ou atores externos. As interações podem ser de qualquer escala e tipo. Por exemplo, eles podem variar de mensagens individuais para transações estendidas e podem ser chamadas de função ou mensagens de serviço Web.

 Para ajudar a Lucerne e o jantar agora descrevem e discutir as etapas no caso de uso de pagamento de processo, eles criam o diagrama de sequência a seguir do diagrama de componentes. As linhas de vida espelham o componente do site do jantar agora e suas partes. As mensagens que aparecem entre as linhas de vida seguem as conexões nos diagramas de componente:

 ![Diagrama de sequência para o caso de uso de pagamento de processo](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")

 **Diagrama de sequência para o caso de uso de pagamento do processo**

 O diagrama de sequência mostra que, quando o cliente cria um pedido, o site do jantar agora chama ProcessOrder em uma instância de OrderProcessing. Em seguida, OrderProcessing chama ProcessPayment no PaymentProcessing. Isso continuará até que o gateway do processador de pagamento externo valide o pagamento. Só então o controle retorna ao site do jantar agora.

 A Lucerne deve estimar o custo da atualização de seu sistema de pagamento para se integrar ao sistema do jantar agora. Para ajudá-los a entender isso, eles também podem criar mapas de código para visualizar o código afetado.

 Consulte:

- [Diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md)

- [Diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)

- [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)

#### <a name="drawing-a-sequence-diagram"></a>Desenhando um diagrama de sequência
 Um diagrama de sequência tem os seguintes recursos principais:

- As linhas de *vida* verticais representam atores ou instâncias de objetos de software.

   Para adicionar um símbolo de ator, que indica que um participante está fora do sistema em desenvolvimento, clique na linha da vida. Na janela **Propriedades** , defina **ator** como **verdadeiro**. Se a janela **Propriedades** não estiver aberta, pressione **F4**.

- *As mensagens* horizontais representam chamadas de método, mensagens de serviço Web ou alguma outra comunicação. As *ocorrências de execução* são retângulos sombreados verticais que aparecem nas linhas de vida e representam os períodos durante os quais os processos de recebimento de objetos são chamados.

- Durante uma mensagem *síncrona* , o objeto do remetente aguarda o controle para <\<retornar > > como em uma chamada de função regular. Durante uma mensagem *assíncrona* , o remetente pode continuar imediatamente.

- Use <\<criar > Mensagens > para indicar a construção de objetos por outros objetos. Deve ser a primeira mensagem enviada ao objeto.

  Consulte:

- [Diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md)

- [Diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)

#### <a name="summary-strengths-of-sequence-diagrams"></a>Resumo: pontos fortes de diagramas de sequência
 Os diagramas de sequência ajudam você a Visualizar:

- O fluxo de controle que transfere entre atores ou objetos durante a execução de um caso de uso.

- A implementação de uma chamada de método ou mensagem.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrição**|
|-----------------|---------------------|
|Diagrama de classe (UML)|Defina as classes que as linhas de vida representam e os parâmetros e valores de retorno que são usados em mensagens enviadas entre linhas de vida.<br /><br /> Para criar uma classe de uma linha de vida, clique com o botão direito do mouse na linha da vida e clique em **criar classe** ou **criar interface**. Para criar uma linha de vida de um tipo em um diagrama de classe, clique com o botão direito do mouse no tipo e clique em **Criar linha de vida**.<br /><br /> Consulte:<br /><br /> -   [diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)<br />-   [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)|
|Diagrama de componente|Descreva os componentes que as linhas de vida representam e as interfaces que fornecem e consomem o comportamento representado pelas mensagens.<br /><br /> Para criar uma linha de vida de um diagrama de componente, clique com o botão direito do mouse no componente e clique em **Criar linha de vida**.<br /><br /> Consulte:<br /><br /> -   [diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)<br />-   [diagramas de componentes UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md)|
|Diagrama de caso de uso|Resuma as interações entre usuários e componentes em um diagrama de sequência como um caso de uso, que representa a meta de um usuário.<br /><br /> Consulte:<br /><br /> [diagramas de caso de uso de UML -   : referência](../modeling/uml-use-case-diagrams-reference.md)<br />[diagramas de caso de uso de UML -   : diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)|

### <a name="DefineClasses"></a>Definir um glossário de tipos: diagramas de classe
 Os diagramas de classe definem as entidades, os termos ou os conceitos que participam do sistema e suas relações entre si. Por exemplo, você pode usar esses diagramas durante o desenvolvimento para descrever os atributos e as operações de cada classe, independentemente de seu idioma ou estilo de implementação.

 Para ajudar a Lucerne a descrever e discutir as entidades que participam do caso de uso de pagamento do processo, elas desenham o seguinte diagrama de classe:

 ![Processar entidades de pagamento no diagrama de classes](../modeling/media/uml-payentities.png "UML_PayEntities")

 **Processar entidades de pagamento em um diagrama de classe**

 Este diagrama mostra que um cliente pode ter muitos pedidos e diferentes maneiras de pagar por pedidos. O BankAccount e o CreditCard herdam de pagamento.

 Durante o desenvolvimento, a Lucerne usa o seguinte diagrama de classe para descrever e discutir os detalhes de cada classe:

 ![Processar detalhes da entidade de pagamento em um diagrama de classe](../modeling/media/uml-payment.png "UML_Payment")

 **Processar detalhes de pagamento no diagrama de classe**

 Consulte:

- [Diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)

- [Diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)

#### <a name="drawing-a-class-diagram"></a>Desenhando um diagrama de classe
 Um diagrama de classe tem os seguintes recursos principais:

- Tipos como classes, interfaces e enumerações:

  - Uma *classe* é a definição de objetos que compartilham características estruturais ou comportamentais específicas.

  - Uma *interface* define uma parte do comportamento visível externamente de um objeto.

  - Uma *Enumeração* é um classificador que contém uma lista de valores literais.

- *Atributos* são valores de um determinado tipo que descrevem cada instância de um *classificador*. Um classificador é um nome geral para tipos, componentes, casos de uso e até mesmo atores.

- *Operações* são métodos ou funções que as instâncias de um classificador podem executar.

- Uma *Associação* indica algum tipo de relação entre dois classificadores.

  - Uma *agregação* é uma associação que indica uma propriedade compartilhada entre classificadores.

  - Uma *composição* é uma associação que indica uma relação de parte inteira entre classificadores.

    Para mostrar agregações ou composições, defina a propriedade de **agregação** em uma associação. **Compartilhado** mostra as agregações **e as composições mostra** as composições.

- Uma *dependência* indica que a alteração da definição de um classificador pode alterar a definição de outro classificador.

- Uma *generalização* indica que um classificador específico herda parte de sua definição de um classificador geral. Uma *realização* indica que uma classe implementa as operações e os atributos oferecidos por uma interface.

   Para criar essas relações, use a ferramenta de **herança** . Como alternativa, uma realização pode ser representada como uma *pirulito*.

- Os *pacotes* são grupos de classificadores, associações, linhas de vida, componentes e outros pacotes. As relações de *importação* indicam que um pacote inclui todas as definições de outro pacote.

  Como ponto de partida para explorar e discutir as classes existentes, você pode usar Designer de Classe para criar diagramas de classe a partir do código.

  Consulte:

- [Diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)

- [Diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)

- [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Resumo: forças dos diagramas de classe
 Os diagramas de classe ajudam a definir:

- Um glossário comum de termos a serem usados ao discutir as necessidades dos usuários e as entidades que participam do sistema. Consulte [requisitos de usuário de modelo](../modeling/model-user-requirements.md).

- Tipos que são usados por partes do sistema, como componentes, independentemente de sua implementação. Consulte [modelar a arquitetura do seu aplicativo](../modeling/model-your-app-s-architecture.md).

- Relações, como dependências, entre tipos. Por exemplo, você pode mostrar que um tipo pode ser associado a várias instâncias de outro tipo.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrição**|
|-----------------|---------------------|
|Diagrama de caso de uso|Defina os tipos que são usados para descrever as metas e as etapas em casos de uso.<br /><br /> Consulte:<br /><br /> [diagramas de caso de uso de UML -   : referência](../modeling/uml-use-case-diagrams-reference.md)<br />[diagramas de caso de uso de UML -   : diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)|
|Diagrama de atividade|Defina os tipos de dados que passam nós de objeto, Pins de entrada, Pins de saída e nós de parâmetro de atividade.<br /><br /> Consulte:<br /><br /> [diagramas de atividade de UML -   : referência](../modeling/uml-activity-diagrams-reference.md)<br />[diagramas de atividade de UML -   : diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|
|Diagrama de componente|Descreva os componentes, suas interfaces e suas relações. Uma classe também pode descrever um componente completo.<br /><br /> Consulte:<br /><br /> -   [diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)<br />-   [diagramas de componentes UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md)|
|Diagrama de camada|Defina a arquitetura lógica do sistema como está relacionada às classes.<br /><br /> Use a validação de camada para garantir que o código permaneça consistente com o design.<br /><br /> Consulte:<br /><br /> -   [criar diagramas de camada do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />[diagramas de camada de -   : referência](../modeling/layer-diagrams-reference.md)<br />[diagramas de camada de -   : diretrizes](../modeling/layer-diagrams-guidelines.md)<br />-   [validar o código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)|
|Diagrama de sequência|Defina os tipos de linhas de vida e as operações, parâmetros e valores de retorno para todas as mensagens que a linha de vida pode receber.<br /><br /> Para criar uma linha de vida de um tipo em um diagrama de classe, clique com o botão direito do mouse no tipo e clique em **Criar linha de vida**.<br /><br /> Consulte:<br /><br /> -   [diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md)<br />-   [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)|
|Mapa de códigos|Visualize a organização e as relações no código existente.<br /><br /> Para identificar classes, suas relações e seus métodos, crie um mapa de código que mostre esses elementos.<br /><br /> Consulte:<br /><br /> -   [mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="DescribeLayers"></a>Descrever a arquitetura lógica: diagramas de camada
 Os diagramas de camada descrevem a arquitetura lógica de um sistema organizando os artefatos em sua solução em grupos abstratos ou *camadas*. Os artefatos podem ser muitas coisas, como namespaces, projetos, classes, métodos e assim por diante. As camadas representam e descrevem as funções ou tarefas que os artefatos executam no sistema. Você também pode incluir a validação de camada em suas operações de criação e check-in para garantir que o código permaneça consistente com seu design.

 Para manter o código consistente com o design, o jantar agora e a Lucerne usam o diagrama de camada a seguir para validar seu código à medida que ele evolui:

 ![Diagrama de camada do sistema de pagamento integrado](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Diagrama de camada para jantar agora integrado à Lucerne**

 As camadas neste diagrama vinculam-se ao jantar correspondente agora e aos artefatos da solução Zulu. Por exemplo, a camada de negócios vincula-se ao namespace DinnerNow. Business e a seus membros, que agora incluem a classe PaymentApprover. A camada de acesso a recursos vincula-se ao namespace DinnerNow. Data. As setas, ou *dependências*, especificam que apenas a camada de negócios pode usar a funcionalidade na camada de acesso ao recurso. À medida que as equipes atualizam seu código, a validação de camada é executada regularmente para detectar conflitos à medida que ocorrem e para ajudar as equipes a solucioná-los imediatamente.

 As equipes trabalham em conjunto para integrar e testar incrementalmente os dois sistemas. Primeiro, eles garantem que o PaymentApprover e o restante do jantar agora trabalhem com os outros com êxito antes de lidarem com o PaymentProcessing.

 O mapa de código a seguir mostra as novas chamadas entre o jantar agora e PaymentApprover:

 ![Grafo de dependência atualizado com sistema integrado](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")

 **Mapa de código com chamadas de método atualizadas**

 Depois de confirmar que o sistema funciona conforme o esperado, o jantar agora comenta o código PaymentProcessing. Os relatórios de validação de camada são limpos e o mapa de código resultante mostra que não existem mais dependências de PaymentProcessing:

 ![Grafo de dependência sem PaymentProcessing](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")

 **Mapa de código sem PaymentProcessing**

#### <a name="drawing-a-layer-diagram"></a>Desenhando um diagrama de camada
 Um diagrama de camada tem os seguintes recursos principais:

- *Camadas* descrevem grupos lógicos de artefatos.

- Um *link* é uma associação entre uma camada e um artefato.

   Para criar camadas de artefatos, arraste itens de Gerenciador de Soluções, mapas de código, Modo de Exibição de Classe ou pesquisador de objetos. Para desenhar novas camadas e vinculá-las a artefatos, use a caixa de ferramentas ou clique com o botão direito do mouse na superfície do diagrama para criar as camadas e, em seguida, arraste os itens para essas camadas.

   O número em uma camada mostra o número de artefatos vinculados à camada. Esses artefatos podem ser namespaces, projetos, classes, métodos e assim por diante. Ao interpretar o número de artefatos em uma camada, lembre-se do seguinte:

  - Se uma camada estiver vinculada a um artefato que contenha outros artefatos, mas não estiver vinculada diretamente a outros artefatos, o número incluirá apenas o artefato vinculado. No entanto, os outros artefatos estão incluídos para análise durante a validação da camada.

     Por exemplo, se uma camada estiver vinculada a um único namespace, o número de artefatos vinculados será 1, mesmo se o namespace contiver classes. Se a camada também tiver links para cada classe no namespace, o número incluirá as classes vinculadas.

  - Se uma camada contiver outras camadas vinculadas a artefatos, a camada de contêiner também estará vinculada a esses artefatos, mesmo que o número na camada de contêiner não inclua esses artefatos.

    Para ver os artefatos que estão vinculados a uma camada, clique com o botão direito do mouse na camada e clique em **exibir links** para abrir o **Gerenciador de camadas**.

- Uma *dependência* indica que uma camada pode usar a funcionalidade em outra camada, mas não vice-versa. Uma *dependência bidirecional* indica que uma camada pode usar a funcionalidade em outra camada, e vice-versa.

   Para exibir as dependências existentes no diagrama de camadas, clique com o botão direito do mouse na superfície do diagrama e clique em **gerar dependências**. Para descrever as dependências pretendidas, desenhe novas.

  Consulte:

- [Criar diagramas de camada por meio de código](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramas de camada: referência](../modeling/layer-diagrams-reference.md)

- [Diagramas de camada: diretrizes](../modeling/layer-diagrams-guidelines.md)

- [Validar o código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-layer-diagrams"></a>Resumo: pontos fortes de diagramas de camada
 Os diagramas de camada ajudam você a:

- Descreva a arquitetura lógica de um sistema de acordo com a funcionalidade de seus artefatos.

- Verifique se o código em desenvolvimento está em conformidade com o design especificado.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrição**|
|-----------------|---------------------|
|Mapa de códigos|Visualize a organização e as relações no código existente.<br /><br /> Para criar camadas, gere um mapa de código e agrupe itens no mapa como camadas potenciais. Arraste os grupos do mapa para o diagrama de camada.<br /><br /> Consulte:<br /><br /> -   [mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />-   [procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)|
|Diagrama de componente|Descreva os componentes, suas interfaces e suas relações.<br /><br /> Para visualizar camadas, crie um diagrama de componente que descreva a funcionalidade de diferentes componentes no sistema.<br /><br /> Consulte:<br /><br /> -   [diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)<br />-   [diagramas de componentes UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md)|

## <a name="external-resources"></a>Recursos Externos

|**Categoria**|**Links**|
|------------------|---------------|
|**Fóruns**|[ferramentas de modelagem & de visualização do Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch) -   <br />[SDK de modelagem do & de visualização do Visual Studio (ferramentas DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx) -   |

## <a name="see-also"></a>Veja também
 [Visualize](../modeling/visualize-code.md) os [modelos de criação de código para seus](../modeling/create-models-for-your-app.md) [modelos de uso de aplicativo no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md) [usar modelos no desenvolvimento ágil](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) [validar seu sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md) [estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md)
