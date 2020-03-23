---
title: 'Cenário: Mude seu design usando visualização e modelagem | Microsoft Docs'
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
ms.openlocfilehash: 70cc3c81c426ec55d0afb36360155786ec97d937
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302311"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Cenário: alterar o design usando visualização e modelagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Certifique-se de que seu sistema de software atenda às necessidades dos usuários usando as ferramentas de visualização e modelagem no Visual Studio. Use ferramentas como diagramas de Linguagem de Modelagem Unificada (UML), mapas de código, diagramas de camada e diagramas de classe para:

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

- [Criar modelos para o aplicativo](../modeling/create-models-for-your-app.md)

## <a name="scenario-overview"></a><a name="ScenarioOverview"></a>Visão geral do cenário
 Este cenário descreve episódios dos ciclos de vida do desenvolvimento de software de duas empresas fictícias: Dinner Now e Lucerne Publishing. O Dinner Now oferece um serviço de entrega de refeições baseado na Web em Seattle. Os clientes podem pedir refeições e pagá-las no site do Dinner Now. Os pedidos são então enviados para o restaurante local apropriado para entrega. A Lucerne Publishing, uma empresa em Nova York, administra vários negócios fora e na Internet. Por exemplo, eles executam um site onde os clientes podem postar avaliações de restaurantes.

 Lucerna adquiriu recentemente o Dinner Now e quer fazer as seguintes mudanças:

- Integre seus sites adicionando recursos de revisão de restaurantes ao Dinner Now.

- Substitua o sistema de pagamento do Dinner Now pelo sistema da Lucerna.

- Expanda o serviço Dinner Now em toda a região.

  Jantar Agora usa PROGRAMAÇÃO SCRUM e eXtreme. Eles têm uma cobertura de teste muito alta e muito pouco código sem suporte. Eles minimizam os riscos criando versões pequenas, mas funcionando de um sistema e, em seguida, adicionando funcionalidade incrementalmente. Eles desenvolvem seu código sobre iterações curtas e freqüentes. Isso permite que eles abracem a mudança com confiança, refatorem o código com freqüência e evitem "grande design na frente".

  Lucerna mantém uma coleção muito maior e complexa de sistemas, alguns dos quais têm mais de 40 anos. Eles são muito cautelosos em fazer mudanças devido à complexidade e escopo do código legado. Eles seguem um processo de desenvolvimento mais rigoroso, preferindo projetar soluções detalhadas e documentar o design e as mudanças que ocorrem durante o desenvolvimento.

  Ambas as equipes usam diagramas de modelagem no Visual Studio para ajudá-los a desenvolver sistemas que atendam às necessidades dos usuários. Eles usam o Team Foundation Server juntamente com outras ferramentas para ajudá-los a planejar, organizar e gerenciar seu trabalho.

  Para obter mais informações sobre o Team Foundation Server, consulte:

- [Trabalho de planejamento e acompanhamento](#PlanningTracking)

- [Testando, validando e verificando em código atualizado](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a>Funções de Arquitetura e Diagramas de Modelagem no Desenvolvimento de Software
 A tabela a seguir descreve funções que essas ferramentas podem desempenhar durante vários e vários estágios do ciclo de vida do desenvolvimento de software:

||**Modelagem de requisitos do usuário**|**Modelagem de processos de negócios**|**Arquitetura de sistema & Design**|**Visualização de códigos & Exploração**|**Verificação**|
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|
|Use o diagrama de caso (UML)|√|√|||√|
|Diagrama de atividade (UML)|√|√|√||√|
|Diagrama de classe (UML)|√|√|√||√|
|Diagrama de componente (UML)|√|√|√||√|
|Diagrama de seqüência (UML)|√|√|√||√|
|Diagrama dsl (Domain-Specific Language, linguagem específica de domínio)|√|√|√|||
|Diagrama de camada, validação de camadas|||√|√|√|
|Mapa de código|||√|√|√|
|Class Designer (baseado em código)||||√||

 Para desenhar diagramas uml e diagramas de camada, você deve criar um projeto de modelagem como parte de uma solução existente ou uma nova. Esses diagramas devem ser criados no projeto de modelagem. Os itens nos diagramas uml são parte de um modelo comum, e os diagramas UML são pontos de vista desse modelo. Os itens nos diagramas de camada estão localizados no projeto de modelagem, mas não são armazenados no modelo comum. Mapas de código e diagramas de classe .NET criados a partir do código existem fora do projeto de modelagem.

 Consulte:

- [Criar projetos e diagramas de modelagem UML](../modeling/create-uml-modeling-projects-and-diagrams.md)

- [Criar diagramas de camada por meio de código](../modeling/create-layer-diagrams-from-your-code.md)

- [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)

- [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [SDK de Modelagem para Visual Studio - linguagens específicas ao domínio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

  Para mostrar visões alternativas da arquitetura, você pode reutilizar certos elementos do mesmo modelo em diagramas múltiplos ou diferentes. Por exemplo, você pode arrastar um componente para outro diagrama de componente ou para um diagrama de seqüência para que ele possa funcionar como um ator. Consulte [Editar modelos e diagramas uml](../modeling/edit-uml-models-and-diagrams.md).

  Ambas as equipes também usam validação de camadas para garantir que o código em desenvolvimento permaneça consistente com o design.

  Consulte:

- [Mantendo código consistente com o design](#ValidatingCode)

- [Descreva a arquitetura lógica: diagramas de camada](#DescribeLayers)

- [Validar o código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)

  > [!NOTE]
  > Algumas versões do Visual Studio suportam validação de camadas e versões somente leitura de mapas de código e diagramas UML para visualização e modelagem. Para ver quais versões do Visual Studio suportam esse recurso, consulte [o suporte à versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understanding-and-communicating-information-about-the-system"></a><a name="UnderstandingCommunicating"></a>Compreensão e Comunicação de Informações sobre o Sistema
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

  Antes que as equipes verifiquem suas alterações, elas validam o código em relação aos testes e ao design executando compilações que incluem validação de camadas e testes automatizados. Isso ajuda a garantir que o código atualizado não entre em conflito com o design e quebre a funcionalidade de funcionamento anteriormente.

  Consulte:

- [Entendendo o papel do sistema no processo de negócios](#UnderstandingBPMandSystemDesign)

- [Descrevendo os requisitos do usuário novos ou atualizados](#DescribingURM)

- [Criação de testes a partir de modelos](#CreatingTests)

- [Identificação de alterações no sistema existente](#DeterminingChanges)

- [Mantendo o código consistente com o design](#ValidatingCode)

- [Dicas gerais para criar e usar modelos](#GeneralTips)

- [Trabalho de planejamento e acompanhamento](#PlanningTracking)

- [Testando, validando e verificando em código atualizado](#TestValidateCheckInCode)

### <a name="understanding-the-role-of-the-system-in-the-business-process"></a><a name="UnderstandingBPMandSystemDesign"></a>Entendendo o papel do Sistema no Processo de Negócios
 Lucerna quer saber mais sobre o processo de negócios do Dinner Now. Eles criam os seguintes diagramas para esclarecer seu entendimento com o Dinner Now mais facilmente:

|**Diagrama**|**Descreve**|
|-----------------|-------------------|
|*Use o diagrama de caso (UML)*<br /><br /> Consulte:<br /><br /> -   [Diagramas de caso de uso uml: referência](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramas de casos de uso de UML: Diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)|- As atividades que o sistema Dinner Now suporta<br />- As pessoas e sistemas externos que realizam as atividades<br />- Os principais componentes do sistema que suportam cada atividade<br />- As partes do processo de negócios que estão fora do escopo do sistema atual, por exemplo, a entrega de alimentos|
|*Diagrama de atividade (UML)*<br /><br /> Consulte:<br /><br /> -   [Diagramas de atividade uml: referência](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramas de atividade uml: diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|O fluxo de etapas que ocorrem quando um cliente cria um pedido|
|*Diagrama de classe (UML)*<br /><br /> Consulte:<br /><br /> -   [Diagramas de classe UML: Referência](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de classe UML: Diretrizes](../modeling/uml-class-diagrams-guidelines.md)|As entidades empresariais e termos utilizados na discussão e as relações entre essas entidades. Por exemplo, o Item de Ordem e Menu faz parte do vocabulário neste cenário.|

 Por exemplo, Lucerna cria o seguinte diagrama de caso de uso para entender as tarefas que são executadas no site do Dinner Now e quem as executa:

 ![Diagrama de Casos de Uso UML](../modeling/media/uml-usecase.png "UML_UseCase")

 **Diagrama de Casos de Uso UML**

 O diagrama de atividade a seguir descreve o fluxo de etapas quando um cliente cria um pedido no site do Dinner Now. Nesta versão, os elementos de comentário identificam os papéis, e as linhas criam *raias,* que organizam os passos por papel:

 ![Diagrama de Atividade UML](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")

 **Diagrama de Atividade UML**

 O diagrama de classe a seguir descreve as entidades que participam do processo de ordem:

 ![Diagrama de Classe UML](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")

 **Diagrama de Classe UML**

### <a name="describing-new-or-updated-user-requirements"></a><a name="DescribingURM"></a>Descrevendo requisitos de usuários novos ou atualizados
 Lucerne quer adicionar funcionalidade ao sistema Dinner Now para que os clientes possam ler e contribuir com avaliações de restaurantes. Eles atualizam os seguintes diagramas para que possam descrever e discutir este novo requisito com o Dinner Now:

|**Diagrama**|**Descreve**|
|-----------------|-------------------|
|*Use o diagrama de caso (UML)*<br /><br /> Consulte:<br /><br /> -   [Diagramas de caso de uso uml: referência](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramas de casos de uso de UML: Diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)|Um novo caso de uso para "Escrever uma revisão de restaurante"|
|*Diagrama de atividade (UML)*<br /><br /> Consulte:<br /><br /> -   [Diagramas de atividade uml: referência](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramas de atividade uml: diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|Os passos que ocorrem quando um cliente quer escrever uma revisão de restaurante|
|*Diagrama de classe (UML)*<br /><br /> Consulte:<br /><br /> -   [Diagramas de classe UML: Referência](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de classe UML: Diretrizes](../modeling/uml-class-diagrams-guidelines.md)|Os dados necessários para armazenar uma revisão|

 Por exemplo, o diagrama de caso de uso a seguir inclui um novo caso de uso "Write Review" para representar o novo requisito. É destacado em laranja no diagrama para facilitar a identificação:

 ![Diagrama de Casos de Uso UML](../modeling/media/uml-writerev.png "UML_WriteRev")

 **Diagrama de caso de uso de UML**

 O diagrama de atividade a seguir inclui novos elementos em laranja para descrever o fluxo de etapas no novo caso de uso:

 ![Diagrama de Atividade UML](../modeling/media/uml-writereview.png "UML_WriteReview")

 **Diagrama de atividade uml**

 O diagrama de classe a seguir inclui uma nova classe de revisão e suas relações com outras classes para que as equipes possam discutir seus detalhes. Observe que um cliente e um restaurante podem ter várias avaliações:

 ![Diagrama de Classe UML](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")

 **Diagrama de classe UML**

### <a name="creating-tests-from-models"></a><a name="CreatingTests"></a>Criando testes a partir de modelos
 Ambas as equipes concordam que precisam de um conjunto completo de testes para o sistema e seus componentes antes de fazer qualquer alteração. Lucerna possui uma equipe especializada que realiza testes de sistema e nível de componentes. Eles reutilizam os testes criados pelo Dinner Now e estruturam esses testes usando os diagramas uml:

- Cada caso de uso é representado por um ou vários testes. Os elementos no link do diagrama do caso de uso para itens de trabalho do Caso de Teste no Servidor de Fundação da Equipe.

- Cada fluxo em um diagrama de atividade ou diagrama de seqüência de nível de sistema está ligado a um teste no mínimo. A equipe de teste garante sistematicamente que eles testam todos os caminhos possíveis através do diagrama de atividade.

- Os termos usados para descrever os testes são baseados nos termos definidos pelos diagramas de caso de uso, classe e atividade.

  À medida que os requisitos mudam e os diagramas são atualizados para refletir essas alterações, os testes também são atualizados. Um requisito é considerado cumprido somente quando os testes passam. Quando possível ou prático, os testes são definidos e baseados em diagramas UML antes do início da implementação.

  Consulte:

- [Desenvolver testes por meio de um modelo](../modeling/develop-tests-from-a-model.md)

- [Validar o modelo UML](../modeling/validate-your-uml-model.md)

### <a name="identifying-changes-to-the-existing-system"></a><a name="DeterminingChanges"></a>Identificação de alterações no sistema existente
 Jantar Agora deve estimar o custo de cumprir a nova exigência. Isso depende, em parte, do quanto essa mudança afetará outras partes do sistema. Para ajudá-los a entender isso, um dos desenvolvedores do Dinner Now cria esses mapas e diagramas a partir do código existente:

|**Mapa ou diagrama**|**programas**|
|------------------------|---------------|
|*Mapa de código*<br /><br /> Consulte:<br /><br /> -   [Mapear dependências através de suas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Navegue e reorganize mapas de código](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Personalize mapas de código editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Dependências e outras relações em código.<br /><br /> Por exemplo, o Dinner Now pode começar revisando mapas de código de montagem para uma visão geral das assembléias e suas dependências. Eles podem perfurar os mapas para explorar os namespaces e classes nessas assembléias.<br /><br /> Jantar Agora também pode criar mapas para explorar determinadas áreas e outros tipos de relacionamentos no código. Eles usam o Solution Explorer para encontrar e selecionar as áreas e relacionamentos que lhes interessam.|
|*Diagrama de classe baseado em código*<br /><br /> Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Classes existentes em código|

 Por exemplo, o desenvolvedor cria um mapa de código. Ela ajusta seu escopo para focar nas áreas que serão afetadas pelo novo cenário. Essas áreas são selecionadas e destacadas no mapa:

 ![Gráfico de dependência de namespace](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")

 **Mapa de código de namespace**

 O desenvolvedor expande os namespaces selecionados para ver suas classes, métodos e relacionamentos:

 ![Gráfico expandido de dependência de namespace](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")

 **Mapa de código de namespace expandido com links de grupo cruzado visíveis**

 O desenvolvedor examina o código para encontrar as classes e métodos afetados. Para ver os efeitos de cada alteração à medida que você os faz, regenere mapas de código após cada alteração. Consulte [Visualize code](../modeling/visualize-code.md).

 Para descrever alterações em outras partes do sistema, como componentes ou interações, a equipe pode desenhar esses elementos em quadros brancos. Eles também podem desenhar os seguintes diagramas no Visual Studio para que os detalhes possam ser capturados, gerenciados e compreendidos por ambas as equipes:

|**Diagramas**|**Descreve**|
|------------------|-------------------|
|*Diagrama de atividade (UML)*<br /><br /> Consulte:<br /><br /> -   [Diagramas de atividade uml: referência](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramas de atividade uml: diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|O fluxo de etapas que ocorrem quando o sistema percebe que um cliente faz um pedido de um restaurante novamente, levando o cliente a escrever uma revisão.|
|*Diagrama de classe (UML)*<br /><br /> Consulte:<br /><br /> -   [Diagramas de classe UML: Referência](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de classe UML: Diretrizes](../modeling/uml-class-diagrams-guidelines.md)|Classes lógicas e seus relacionamentos. Por exemplo, uma nova classe é adicionada para descrever uma **Revisão** e suas relações com outras entidades, como **Restaurante,** **Menu**e **Cliente.**<br /><br /> Para associar avaliações com um cliente, o sistema deve armazenar os detalhes do cliente. Um diagrama de classe UML pode ajudar a esclarecer esses detalhes.|
|*Diagrama de classe baseado em código*<br /><br /> Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Classes existentes em código.|
|*Diagrama de componente (UML)*<br /><br /> Consulte:<br /><br /> -   [Diagramas de componentes UML: Referência](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramas de componentes UML: Diretrizes](../modeling/uml-component-diagrams-guidelines.md)|As partes de alto nível do sistema, como o site do Dinner Now, e suas interfaces. Essas interfaces definem como os componentes interagem entre si através dos métodos ou serviços que fornecem e consomem.|
|*Diagrama de seqüência (UML)*<br /><br /> Consulte:<br /><br /> -   [Diagramas de seqüência UML: Referência](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramas de seqüência UML: Diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)|A seqüência de interações entre instâncias.|

 Por exemplo, o diagrama do componente a seguir mostra o novo componente, que faz parte do componente Dinner Now Web Site. O componente ReviewProcessing lida com a funcionalidade de criar avaliações e aparece destacado em laranja:

 ![Diagrama de Componente UML](../modeling/media/uml-internal.png "UML_Internal")

 **Diagrama de componente UML**

 O diagrama de seqüência a seguir mostra a seqüência de interações que ocorrem quando o Site do Dinner Now verifica se o cliente já pediu em um restaurante antes. Se isso for verdade, então ele pede ao cliente para criar uma revisão, que é enviada para o restaurante e publicada pelo site:

 ![Diagrama de Sequência UML](../modeling/media/uml-revsystem.png "UML_RevSystem")

 **Diagrama de seqüência UML**

### <a name="keeping-code-consistent-with-the-design"></a><a name="ValidatingCode"></a>Mantendo código consistente com o design
 Jantar Agora deve certificar-se de que o código atualizado permanece consistente com o design. Eles criam diagramas de camadas que descrevem as camadas de funcionalidade no sistema, especificam as dependências permitidas entre eles e associam artefatos de solução a essas camadas.

|**Diagrama**|**Descreve**|
|-----------------|-------------------|
|*Diagrama de camada*<br /><br /> Consulte:<br /><br /> -   [Crie diagramas de camada a partir do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de camada: Referência](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de camada: Diretrizes](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)|A arquitetura lógica do código.<br /><br /> Um diagrama de camada organiza e [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mapeia os artefatos em uma solução para grupos abstratos chamados *camadas*. Essas camadas identificam as funções, tarefas ou funções que esses artefatos executam no sistema.<br /><br /> Diagramas de camada são úteis para descrever o design pretendido do sistema e validar o código em evolução em relação a esse projeto.<br /><br /> Para criar camadas, arraste itens do Solution Explorer, mapas de código, exibição de classe e navegador de objetos. Para desenhar novas camadas, use a caixa de ferramentas ou clique com o botão direito do mouse na superfície do diagrama.<br /><br /> Para visualizar as dependências existentes, clique com o botão direito do mouse na superfície do diagrama de camada e clique **em Gerar dependências**. Para especificar as dependências pretendidas, desenhe novas dependências.|

 Por exemplo, o diagrama de camada a seguir descreve dependências entre camadas e o número de artefatos associados a cada camada:

 ![Diagrama de camada do sistema de pagamento integrado](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Diagrama de camada**

 Para garantir que os conflitos com o projeto não ocorram durante o desenvolvimento do código, as equipes usam validação de camadas em compilações que são executadas no Team Foundation Build. Eles também criam uma tarefa msbuild personalizada para exigir validação de camadas em suas operações de check-in. Eles usam relatórios de compilação para coletar erros de validação.

 Consulte:

- [Definir o processo de compilação](https://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)

- [Usar um processo de compilação de check-in restrito para validar alterações](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)

- [Personalizar seu modelo de processo de compilação](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

### <a name="general-tips-for-creating-and-using-models"></a><a name="GeneralTips"></a>Dicas gerais para criar e usar modelos

- A maioria dos diagramas consiste em nós conectados por linhas. Para cada tipo de diagrama, a caixa de ferramentas fornece diferentes tipos de nós e linhas.

   Para abrir a caixa de ferramentas, no menu **Exibir,** clique em **Caixa de ferramentas**.

- Para criar um nó, arraste-o da caixa de ferramentas para o diagrama. Certos tipos de nódulos devem ser arrastados para os nódulos existentes. Por exemplo, em um diagrama de componente, uma nova porta deve ser adicionada a um componente existente.

- Para criar uma linha ou uma conexão, clique na ferramenta apropriada na caixa de ferramentas, clique no nó de origem e clique no nó de destino. Algumas linhas podem ser criadas apenas entre certos tipos de nós. Quando você move o ponteiro sobre uma possível fonte ou alvo, o ponteiro indica se você pode criar uma conexão.

- Quando você cria itens em diagramas UML, você também os adiciona a um modelo comum. Os diagramas UML em um projeto de modelagem são pontos de vista desse modelo. Os itens em um diagrama de camada fazem parte do projeto de modelagem, embora não sejam armazenados no modelo comum.

   Para ver o modelo, no menu **Arquitetura,** aponte para **o Windows**e clique **em UML Model Explorer**.

- Em alguns casos, você pode arrastar certos itens do **UML Model Explorer** para um diagrama UML. Alguns elementos dentro do mesmo modelo podem ser usados em diagramas múltiplos ou diferentes para mostrar visões alternativas da arquitetura. Por exemplo, você pode arrastar um componente para outro diagrama de componente ou para um diagrama de seqüência para usar como ator.

- O Visual Studio suporta UML 2.1.2. Esta visão geral descreve apenas as principais características dos diagramas UML nesta versão, mas há muitos livros que discutem uml e seu uso em detalhes.

  Consulte [Criar modelos para o seu aplicativo](../modeling/create-models-for-your-app.md).

### <a name="planning-and-tracking-work"></a><a name="PlanningTracking"></a>Trabalho de planejamento e rastreamento
 Os diagramas de modelagem do Visual Studio são integrados com o Team Foundation Server para que você possa planejar, gerenciar e acompanhar o trabalho com mais facilidade. Ambas as equipes usam modelos para identificar casos de teste e tarefas de desenvolvimento e estimar seu trabalho. A Lucerne cria e vincula itens de trabalho do Team Foundation Server a elementos de modelo, como casos de uso ou componentes. Isso os ajuda a monitorar seu progresso e rastrear seu trabalho de volta às necessidades dos usuários. Isso os ajuda a garantir que suas mudanças continuem a atender a esses requisitos.

 À medida que seu trabalho progride, as equipes atualizam seus itens de trabalho para refletir o tempo que gastaram em suas tarefas. Eles também monitoram e relatam o status de seu trabalho usando os seguintes recursos do Team Foundation Server:

- Relatórios diários de *burndown* mostram se eles vão completar o trabalho planejado no tempo esperado. Eles geram outros relatórios semelhantes do Team Foundation Server para acompanhar o progresso dos bugs.

- Uma *planilha de iteração* que usa o Microsoft Excel para ajudar a equipe a monitorar e equilibrar a carga de trabalho entre seus membros. Esta planilha é vinculada ao Team Foundation Server e fornece foco para discussão durante suas reuniões de progresso regular.

- Um *painel de desenvolvimento* que usa o Office Project para manter a equipe informada sobre informações importantes do projeto.

  Consulte:

- [Acompanhe o trabalho usando o Visual Studio Team Services ou o Team Foundation Server](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)

- [Vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md)

- [Gráficos, painéis e relatórios para o Visual Studio ALM](https://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)

- [Criar sua lista de pendências e tarefas usando o Project](https://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)

### <a name="testing-validating-and-checking-in-code"></a><a name="TestValidateCheckInCode"></a>Testando, validando e verificando código
 À medida que as equipes completam cada tarefa, eles verificam seu código no controle de versão da Team Foundation e recebem lembretes do Team Foundation Server, se esquecerem. Antes que o Team Foundation Server aceite seus check-ins, as equipes executam testes de unidade e validação de camadas para verificar o código em relação aos seus casos de teste e ao design. Eles usam o Team Foundation Server para executar compilações, testes automatizados de unidades e validação de camadas regularmente. Isso ajuda a garantir que o código atenda aos seguintes critérios:

- E funciona.

- Ele não quebra o código de trabalho anteriormente.

- Não conflita com o projeto.

  Dinner Now tem uma grande coleção de testes automatizados, que Lucerna pode reutilizar porque quase todos ainda se aplicam. Lucerna também pode construir sobre esses testes e adicionar novos para cobrir novas funcionalidades. Ambos também usam o Visual Studio para executar testes manuais.

  Para garantir que o código esteja em conformidade com o design, as equipes configuram suas compilações no Team Foundation Build para incluir validação de camadas. Se ocorrer algum conflito, um relatório é gerado com os detalhes.

  Consulte:

- [Testando o aplicativo](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)

- [Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)

- [Usar controle de versão](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Construa o aplicativo](/azure/devops/pipelines/index)

## <a name="updating-the-system-using-visualization-and-modeling"></a><a name="UpdatingSystem"></a>Atualização do sistema usando visualização e modelagem
 Lucerna e Dinner Now devem integrar seus sistemas de pagamento. As seções a seguir mostram os diagramas de modelagem no Visual Studio para ajudá-los a executar essa tarefa:

- [Entenda os requisitos do usuário: Use diagramas de casos](#UnderstandUseCases)

- [Entenda o processo de negócios: Diagramas de atividade](#UnderstandActivities)

- [Descreva a estrutura do sistema: Diagramas de componentes](#DescribeComponents)

- [Descreva as interações: Diagramas de seqüência](#DescribeSequence)

- [Visualize o código existente: Mapas de código](#VisualizeCode)

- [Definir um Glossário de Tipos: Diagramas de Classe](#DefineClasses)

- [Descreva a arquitetura lógica: diagramas de camada](#DescribeLayers)

  Consulte:

- [Criar modelos para o aplicativo](../modeling/create-models-for-your-app.md)

- [Visualizar código](../modeling/visualize-code.md)

- [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)

- [Requisitos de usuário do modelo](../modeling/model-user-requirements.md)

- [Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)

### <a name="understand-the-user-requirements-use-case-diagrams"></a><a name="UnderstandUseCases"></a>Entenda os requisitos do usuário: Use diagramas de casos
 Os diagramas de caso resumem as atividades que um sistema suporta e quem realiza essas atividades. Lucerna usa um diagrama de caso de uso para aprender o seguinte sobre o sistema Dinner Now:

- Os clientes criam pedidos.

- Restaurantes recebem pedidos.

- O Gateway do processador de pagamento externo, que o Sistema de Pagamento Dinner Now usa para validar pagamentos, está fora de escopo para o site da Web.

  O diagrama também mostra como alguns dos principais casos de uso se dividem em casos de uso menores. Lucerna quer usar seu próprio sistema de pagamento. Eles destacam o caso de uso do pagamento de processo em uma cor diferente para indicar que ele requer alterações:

  ![Destacando o pagamento do processo em um diagrama de caso de uso](../modeling/media/uml-processpay.png "UML_ProcessPay")

  **Destacando o pagamento do processo no diagrama do caso de uso**

  Se o tempo de desenvolvimento fosse curto, a equipe poderia discutir se eles querem deixar os clientes pagar em restaurantes diretamente. Para mostrar isso, eles substituiriam o caso de uso do pagamento de processo por um que está fora do limite do sistema Dinner Now. Eles então ligariam o Cliente diretamente ao Restaurante, indicando que o Dinner Now só processaria pedidos:

  ![Restaurante Rescoping Pay no diagrama do caso de uso](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")

  **Restaurante Rescoping Pay no diagrama do caso de uso**

  Consulte:

- [Diagramas de caso de uso UML: referência](../modeling/uml-use-case-diagrams-reference.md)

- [Diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="drawing-a-use-case-diagram"></a>Desenho de um diagrama de caso de uso
 Um diagrama de caso de uso tem as seguintes características principais:

- *Os atores* representam papéis desempenhados por pessoas, organizações, máquinas ou sistemas de software. Por exemplo, Cliente, Restaurante e o Sistema de Pagamento Dinner Now são atores.

- *Os casos de uso* representam interações entre atores e o sistema em desenvolvimento.  Eles podem representar qualquer escala de interação de um único clique ou mensagem para uma transação estendida por muitos dias.

- *Associações* ligam atores para usar casos.

- Um caso de uso maior pode *incluir* os menores, por exemplo, Create Order inclui Select Restaurant. Você pode *estender* um caso de uso, que adiciona metas e etapas ao caso de uso estendido, para indicar que o caso de uso ocorre apenas determinadas condições. Casos de uso também podem herdar um do outro.

- Um *subsistema* representa o sistema de software que está em desenvolvimento ou um de seus componentes. É uma caixa grande que contém casos de uso. Um diagrama de caso de uso esclarece o que está dentro ou fora do limite do subsistema. Para indicar que o usuário deve cumprir determinadas metas de outras formas, desenhe esses casos de uso fora do limite do subsistema.

- Artefatos ligam *elementos* no diagrama a outros diagramas ou documentos.

  Consulte:

- [Diagramas de caso de uso UML: referência](../modeling/uml-use-case-diagrams-reference.md)

- [Diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="summary-strengths-of-use-case-diagrams"></a>Resumo: Pontos fortes do caso de uso diagramas
 Use diagramas de caso para ajudá-lo a visualizar:

- As atividades que um sistema suporta ou não suporta

- As pessoas e sistemas externos que realizam essas atividades

- Os principais componentes do sistema que suportam cada atividade, que você pode representar como subsistemas aninhados dentro do sistema pai

- Como um caso de uso pode se dividir em menores ou variações

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descreve**|
|-----------------|-------------------|
|Diagrama de atividade|O fluxo de etapas em um caso de uso e aqueles que executam essas etapas nesse caso de uso.<br /><br /> Os nomes dos casos de uso refletem frequentemente as etapas em um diagrama de atividade. Os diagramas de atividade suportam elementos como decisões, mesclagens, entradas e saídas, fluxos simultâneos e assim por diante.<br /><br /> Consulte:<br /><br /> -   [Diagramas de atividade uml: referência](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramas de atividade uml: diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|
|Diagrama de sequência|A seqüência de interações entre os participantes em um caso de uso.<br /><br /> Consulte:<br /><br /> -   [Diagramas de seqüência UML: Referência](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramas de seqüência UML: Diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)|
|Diagrama de classe (UML)|As entidades ou tipos que participam do caso de uso.<br /><br /> Consulte:<br /><br /> -   [Diagramas de classe UML: Referência](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de classe UML: Diretrizes](../modeling/uml-class-diagrams-guidelines.md)|

### <a name="understand-the-business-process-activity-diagrams"></a><a name="UnderstandActivities"></a>Entenda o processo de negócios: Diagramas de atividade
 Os diagramas de atividade descrevem o fluxo de etapas em um processo de negócios e fornecem uma maneira simples de comunicar o fluxo de trabalho. Um projeto de desenvolvimento pode ter vários diagramas de atividade. Normalmente, uma atividade abrange todas as ações que resultam de uma ação externa, como pedir uma refeição, atualizar um cardápio ou adicionar um novo restaurante ao negócio. Uma atividade também pode descrever os detalhes de uma ação complexa.

 Lucerna atualiza o seguinte diagrama de atividade para mostrar que Lucerna processa o pagamento e paga o restaurante. Eles substituem o Sistema de Pagamento Dinner Now pelo Sistema de Pagamento Lucerna, como destacado:

 ![Sistema de pagamento lucerna no diagrama de atividade](../modeling/media/uml-lucerne.png "UML_Lucerne")

 **Substituindo o sistema de pagamento Dinner Now no diagrama de atividades**

 O diagrama atualizado ajuda lucerna e jantar agora visualizar onde o Sistema de Pagamento Lucerna se encaixa no processo de negócios. Nesta versão, os comentários são usados para identificar as funções que executam as etapas. As linhas são usadas para criar *raias,* que organizam os passos por papel.

 As equipes também podem considerar discutir uma história alternativa onde o cliente paga o restaurante em vez disso depois que o pedido é entregue. Isso criaria diferentes requisitos para o sistema de software.

 Anteriormente, o Dinner Now desenhou esses diagramas em um quadro branco ou no PowerPoint. Eles agora também usam o Visual Studio para desenhar esses diagramas para que ambas as equipes possam capturar, entender e gerenciar os detalhes.

 Consulte:

- [Diagramas de atividade UML: referência](../modeling/uml-activity-diagrams-reference.md)

- [Diagramas de atividade UML: diretrizes](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="drawing-an-activity-diagram"></a>Desenho de um diagrama de atividade
 Um diagrama de atividade saem das seguintes características principais:

- Um *nó inicial* que indica a primeira ação da atividade.

   O diagrama deve sempre ter um desses nós.

- *Ações* que descrevem etapas onde o usuário ou software executa uma tarefa.

- *Controle de fluxos* que mostram o fluxo entre as ações.

- *Os nódulos de decisão* que representam ramos condicionais no fluxo.

- *Nódulos de garfo* que dividem fluxos únicos em fluxos simultâneos.

- *Nó final da atividade* que mostra o fim da atividade.

   Embora esses nós sejam opcionais, é útil incluí-los no diagrama para mostrar onde a atividade termina.

  Consulte:

- [Diagramas de atividade UML: referência](../modeling/uml-activity-diagrams-reference.md)

- [Diagramas de atividade UML: diretrizes](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="summary-strengths-of-activity-diagrams"></a>Resumo: Pontos fortes dos diagramas de atividade
 Diagramas de atividade ajudam a visualizar e descrever o fluxo de controle e informações entre as ações de um negócio, sistema ou programa. Esta é uma maneira simples e útil de descrever o fluxo de trabalho ao se comunicar com outras pessoas.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrição**|
|-----------------|---------------------|
|Diagrama de caso de uso|Resumir as atividades que cada ator realiza.<br /><br /> Consulte:<br /><br /> -   [Diagramas de caso de uso uml: referência](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramas de casos de uso de UML: Diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)|
|Diagrama de componente|Visualize o sistema como uma coleção de peças reutilizáveis que fornecem ou consomem comportamento através de um conjunto bem definido de interfaces.<br /><br /> Consulte:<br /><br /> -   [Diagramas de componentes UML: Referência](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramas de componentes UML: Diretrizes](../modeling/uml-component-diagrams-guidelines.md)|

### <a name="describe-the-system-structure-component-diagrams"></a><a name="DescribeComponents"></a>Descreva a estrutura do sistema: Diagramas de componentes
 Diagramas de componentes descrevem um sistema como uma coleção de peças separáveis que fornecem ou consomem comportamento através de um conjunto bem definido de interfaces. As peças podem estar em qualquer escala e podem se conectar de qualquer maneira.

 Para ajudar Lucerna e Dinner Now a visualizar e discutir os componentes do sistema e suas interfaces, eles criam os seguintes diagramas de componentes:

 ![Componentes externos no sistema de pagamento](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")

 **Componentes do sistema de pagamento Dinner Now**

 Este diagrama mostra diferentes tipos de componentes e suas *dependências*. Por exemplo, tanto o Site do Dinner Now quanto o Sistema de Pagamento Lucerna exigem que o Gateway do processador de pagamento externo valide pagamentos. As setas entre os componentes representam as dependências que indicam quais componentes requerem a funcionalidade de outros componentes.

 Para usar o Sistema de Pagamento Lucerna, o site do Dinner Now deve ser atualizado para usar as interfaces de Aprovação de Pagamento e Deserção a Pagar no Sistema de Pagamento Lucerna.

 O diagrama a seguir mostra uma configuração específica de componentes para o site do Dinner Now. Esta configuração indica que qualquer instância do site consiste em quatro *partes:*

- Processamento de clientes

- Processamento de pedidos

- RevisãoProcessamento

- Paymentprocessing

  Essas partes são instâncias dos tipos de componentes especificados e estão conectadas da seguinte forma:

  ![Componentes dentro do site do Dinner Now](../modeling/media/uml-dinnernow.png "UML_DinnerNow")

  **Componentes dentro do site do Dinner Now**

  O site Dinner Now delega seu comportamento a essas partes, que lidam com as funções do site. As setas entre o componente-pai e seus componentes membros mostram *delegações* que indicam quais partes lidam com as mensagens que o pai recebe ou envia através de suas interfaces.

  Nesta configuração, o componente PaymentProcessing processa os pagamentos dos clientes. Portanto, deve ser atualizado para integrar-se ao sistema de pagamento da Lucerna. Em outros cenários, várias instâncias de um tipo de componente podem existir no mesmo componente pai.

  Consulte:

- [Diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)

- [Diagramas de componente UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="drawing-a-component-diagram"></a>Desenho de um diagrama de componente
 Um diagrama de componente saem das seguintes características principais:

- *Componentes* que representam peças separáveis da funcionalidade do sistema.

- *Portas de interface fornecidas* que representam grupos de mensagens ou chamadas quais componentes implementam e são usadas por outros componentes ou sistemas externos.

- *Portas de interface necessárias* que representam grupos de mensagens ou chamadas que os componentes enviam para outros componentes ou sistemas externos. Este tipo de porta descreve as operações que um componente pelo menos espera de outros componentes ou sistemas externos.

- *As peças* são membros de componentes e são tipicamente instâncias de outros componentes. Uma peça é uma parte do design interno do componente pai.

- *Dependências* que indicam componentes requerem a funcionalidade de outros componentes.

- *As delegações* que indicam partes de um componente lidam com as mensagens enviadas ou recebidas pelo componente pai.

  Consulte:

- [Diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)

- [Diagramas de componente UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="summary-strengths-of-component-diagrams"></a>Resumo: Pontos fortes dos diagramas de componentes
 Diagramas de componentes ajudam a visualizar:

- O sistema como uma coleção de partes separáveis, independentemente de sua linguagem de implementação ou estilo.

- Componentes com interfaces bem definidas, tornando o design mais fácil de entender e atualizar quando os requisitos mudam.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrição**|
|-----------------|---------------------|
|Mapa de código|Visualize a organização e as relações no código existente.<br /><br /> Para identificar candidatos a componentes, crie um mapa de código e itens de grupo por sua função no sistema.<br /><br /> Consulte:<br /><br /> -   [Mapear dependências através de suas soluções](../modeling/map-dependencies-across-your-solutions.md)|
|Diagrama de sequência|Visualize a seqüência de interações entre componentes ou as partes dentro de um componente.<br /><br /> Para criar uma linha de vida em um diagrama de seqüência a partir de um componente, clique com o botão direito do mouse no componente e clique em **Criar linha de vida**.<br /><br /> Consulte:<br /><br /> -   [Diagramas de seqüência UML: Referência](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramas de seqüência UML: Diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)|
|Diagrama de classe (UML)|Defina as interfaces nas portas fornecidas ou necessárias e as classes que implementam a funcionalidade dos componentes.<br /><br /> Consulte:<br /><br /> -   [Diagramas de classe UML: Referência](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de classe UML: Diretrizes](../modeling/uml-class-diagrams-guidelines.md)|
|Diagrama de camada|Descreva a arquitetura lógica do sistema como ele se relaciona com os componentes. Use a validação da camada para garantir que o código permaneça consistente com o design.<br /><br /> Consulte:<br /><br /> -   [Crie diagramas de camada a partir do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de camada: Referência](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de camada: Diretrizes](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)|
|Diagrama de atividade|Visualize o processamento interno que os componentes realizam em resposta às mensagens recebidas.<br /><br /> Consulte:<br /><br /> -   [Diagramas de atividade uml: referência](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramas de atividade uml: diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>Visualize o código existente: Mapas de código
 Mapas de código mostram a organização atual e as relações no código. Os itens são representados por nós no mapa, e as relações são *representadas* por *links*. Mapas de código podem ajudá-lo a executar os seguintes tipos de tarefas:

- Explorar códigos desconhecidos.

- Entenda onde e como uma mudança proposta pode afetar o código existente.

- Encontre áreas de complexidade, camadas naturais ou padrões, ou outras áreas que possam se beneficiar da melhoria.

  Por exemplo, o Dinner Now deve estimar o custo de atualização do componente PaymentProcessing. Isso depende, em parte, do quanto essa mudança afetará outras partes do sistema. Para ajudá-los a entender isso, um dos desenvolvedores do Dinner Now gera mapas de código a partir do código e ajusta o foco de escopo nas áreas que podem ser afetadas pela mudança.

  O mapa a seguir mostra as dependências entre a classe PaymentProcessing e outras partes do sistema Dinner Now, que aparecem selecionadas:

  ![Gráfico de dependência para o sistema de pagamento Dinner Now](../modeling/media/dep-dnpayment.png "Dep_DNPayment")

  **Mapa de código para o sistema de pagamento Dinner Now**

  O desenvolvedor explora o mapa expandindo a classe PaymentProcessing e selecionando seus membros para ver as áreas potencialmente afetadas:

  ![Métodos dentro de PagamentosProcessamento e dependências](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")

  **Métodos dentro da classe PaymentProcessing e suas dependências**

  Eles geram o seguinte mapa para o Sistema de Pagamento Lucerna para inspecionar suas classes, métodos e dependências. A equipe vê que o sistema lucerna também pode exigir trabalho para interagir com as outras partes do Dinner Now:

  ![Gráfico de dependência para o sistema de pagamento lucerna](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")

  **Mapa de código para o Sistema de Pagamento lucerna**

  Ambas as equipes trabalham juntas para determinar as mudanças necessárias para integrar os dois sistemas. Eles decidem refatorar parte do código para que seja mais fácil de atualizar. A classe PaymentApprover será mudança para o namespace DinnerNow.Business e exigirá alguns novos métodos. As classes Dinner Now que lidam com transações terão seu próprio espaço de nome. As equipes criam e usam itens de trabalho para planejar, organizar e acompanhar seu trabalho. Eles ligam os itens de trabalho a elementos modelados onde ele é útil.

  Após a reorganização do código, as equipes geram um novo mapa de código para ver a estrutura e relacionamentos atualizados:

  ![Gráfico de dependência com código reorganizado](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")

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
|-----------------|-------------------|
|Diagrama de camada|A arquitetura lógica do sistema. Use a validação da camada para garantir que o código permaneça consistente com o design.<br /><br /> Para ajudá-lo a identificar camadas ou camadas pretendidas, crie um mapa de código e itens relacionados ao grupo. Para criar um diagrama de camada, consulte:<br /><br /> -   [Crie diagramas de camada a partir do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de camada: Diretrizes](../modeling/layer-diagrams-guidelines.md)|
|Diagrama de componente|Componentes, suas interfaces e seus relacionamentos.<br /><br /> Para ajudá-lo a identificar componentes, crie um mapa de código e grupos de itens por sua função no sistema.<br /><br /> Consulte:<br /><br /> -   [Diagramas de componentes UML: Referência](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramas de componentes UML: Diretrizes](../modeling/uml-component-diagrams-guidelines.md)|
|Diagrama de classe (UML)|Aulas, seus atributos e operações, e seus relacionamentos.<br /><br /> Para ajudá-lo a identificar esses elementos, crie um diagrama de classe UML que mostre esses elementos.<br /><br /> Consulte:<br /><br /> -   [Diagramas de classe UML: Referência](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de classe UML: Diretrizes](../modeling/uml-class-diagrams-guidelines.md)|
|Diagrama de classe (baseado em código)|Classes existentes em código para um projeto específico.<br /><br /> Para visualizar e modificar uma classe existente em código, use Class Designer.<br /><br /> Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|

### <a name="describe-the-interactions-sequence-diagrams"></a><a name="DescribeSequence"></a>Descreva as interações: Diagramas de seqüência
 Diagramas de seqüência descrevem uma série de interações entre partes de um sistema. As peças podem ser de qualquer escala. Por exemplo, eles podem variar de objetos individuais em um programa a grandes subsistemas ou atores externos. As interações podem ser de qualquer escala e tipo. Por exemplo, eles podem variar de mensagens individuais a transações estendidas e podem ser chamadas de função ou mensagens de serviço da Web.

 Para ajudar Lucerna e Jantar Agora descrevem e discutem as etapas no caso de uso do pagamento do processo, eles criam o seguinte diagrama de seqüência a partir do diagrama do componente. As linhas de vida refletem o componente Dinner Now e suas partes. As mensagens que aparecem entre as linhas de vida seguem as conexões nos diagramas do componente:

 ![Diagrama de seqüência para o caso de uso do pagamento do processo](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")

 **Diagrama de seqüência para o caso de uso do pagamento do processo**

 O diagrama de seqüência mostra que quando o cliente cria um pedido, o site do Dinner Now chama ProcessOrder em uma instância de OrderProcessing. Em seguida, o OrderProcessing chama ProcessPayment on PaymentProcessing. Isso continua até que o Gateway do processador de pagamento externo valide o pagamento. Só então o controle retorna ao site do Dinner Now.

 Lucerna deve estimar o custo de atualização de seu sistema de pagamento para se integrar ao sistema Dinner Now. Para ajudá-los a entender isso, eles também podem criar mapas de código para visualizar o código afetado.

 Consulte:

- [Diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md)

- [Diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)

- [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)

#### <a name="drawing-a-sequence-diagram"></a>Desenho de um diagrama de seqüência
 Um diagrama de seqüência tem as seguintes características principais:

- Linhas *de vida verticais* representam atores ou instâncias de objetos de software.

   Para adicionar um símbolo de ator, que indica que um participante está fora do sistema em desenvolvimento, clique na linha de vida. Na janela **Propriedades,** definir **Ator** como **True**. Se a janela **Propriedades** não estiver aberta, pressione **F4**.

- As *mensagens horizontais* representam chamadas de método, mensagens de serviço da Web ou alguma outra comunicação. *As ocorrências de execução* são retângulos verticais sombreados que aparecem nas linhas de vida e representam os períodos durante os quais os objetos recebidos processam chamadas.

- Durante uma mensagem *síncrona,* o objeto \<remetente aguarda o controle para <retornar>> como em uma chamada de função regular. Durante uma mensagem *assíncrona,* o remetente pode continuar imediatamente.

- Use \<<criar mensagens>> para indicar a construção de objetos por outros objetos. Deve ser a primeira mensagem enviada ao objeto.

  Consulte:

- [Diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md)

- [Diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)

#### <a name="summary-strengths-of-sequence-diagrams"></a>Resumo: Pontos fortes dos diagramas de seqüência
 Diagramas de seqüência ajudam a visualizar:

- O fluxo de controle que se transfere entre atores ou objetos durante a execução de um caso de uso.

- A implementação de uma chamada ou mensagem de método.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrição**|
|-----------------|---------------------|
|Diagrama de classe (UML)|Defina as classes que as linhas de vida representam e os parâmetros e valores de retorno que são usados nas mensagens enviadas entre linhas de vida.<br /><br /> Para criar uma classe a partir de uma linha de vida, clique com o botão direito do mouse na linha de vida e clique em **Criar classe** ou **criar interface**. Para criar uma linha de vida a partir de um tipo em um diagrama de classe, clique com o botão direito do mouse no tipo e clique em **Criar linha de vida**.<br /><br /> Consulte:<br /><br /> -   [Diagramas de classe UML: Referência](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramas de classe UML: Diretrizes](../modeling/uml-class-diagrams-guidelines.md)|
|Diagrama de componente|Descreva os componentes que as linhas de vida representam e as interfaces que fornecem e consomem o comportamento representado pelas mensagens.<br /><br /> Para criar uma linha de vida a partir de um diagrama de componente, clique com o botão direito do mouse no componente e clique em **Criar linha de vida**.<br /><br /> Consulte:<br /><br /> -   [Diagramas de componentes UML: Referência](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramas de componentes UML: Diretrizes](../modeling/uml-component-diagrams-guidelines.md)|
|Diagrama de caso de uso|Resumir as interações entre usuários e componentes em um diagrama de seqüência como um caso de uso, que representa o objetivo de um usuário.<br /><br /> Consulte:<br /><br /> -   [Diagramas de caso de uso uml: referência](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramas de casos de uso de UML: Diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a>Definir um Glossário de Tipos: Diagramas de Classe
 Os diagramas de classe definem as entidades, termos ou conceitos que participam do sistema e suas relações entre si. Por exemplo, você pode usar esses diagramas durante o desenvolvimento para descrever os atributos e operações de cada classe, independentemente de sua linguagem de implementação ou estilo.

 Para ajudar Lucerna a descrever e discutir as entidades que participam do caso de uso do Pagamento de Processo, eles desenham o seguinte diagrama de classe:

 ![Entidades de pagamento de processos no diagrama da classe](../modeling/media/uml-payentities.png "UML_PayEntities")

 **Entidades de pagamento de processos em um diagrama de classe**

 Este diagrama mostra que um Cliente pode ter muitos pedidos e diferentes maneiras de pagar por pedidos. Conta bancária e cartão de crédito herdam do Pagamento.

 Durante o desenvolvimento, Lucerna usa o seguinte diagrama de classe para descrever e discutir os detalhes de cada classe:

 ![Detalhes da entidade process payment em um diagrama de classe](../modeling/media/uml-payment.png "UML_Payment")

 **Detalhes do pagamento do processo no diagrama da classe**

 Consulte:

- [Diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)

- [Diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)

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

  Consulte:

- [Diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)

- [Diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)

- [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Resumo: Pontos fortes dos diagramas de classe
 Diagramas de classe ajudam a definir:

- Um glossário comum de termos a serem usados ao discutir as necessidades dos usuários e as entidades que participam do sistema. Consulte [os requisitos do usuário do modelo](../modeling/model-user-requirements.md).

- Tipos que são utilizados por partes do sistema, como componentes, independentemente de sua implementação. Consulte [Modelar a arquitetura do seu aplicativo](../modeling/model-your-app-s-architecture.md).

- Relações, como dependências, entre tipos. Por exemplo, você pode mostrar que um tipo pode ser associado a várias instâncias de outro tipo.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrição**|
|-----------------|---------------------|
|Diagrama de caso de uso|Defina os tipos utilizados para descrever metas e etapas em casos de uso.<br /><br /> Consulte:<br /><br /> -   [Diagramas de caso de uso uml: referência](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramas de casos de uso de UML: Diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)|
|Diagrama de atividade|Defina os tipos de dados que passam por nódulos de objeto, pinos de entrada, pinos de saída e nós de parâmetro de atividade.<br /><br /> Consulte:<br /><br /> -   [Diagramas de atividade uml: referência](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramas de atividade uml: diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|
|Diagrama de componente|Descreva componentes, suas interfaces e seus relacionamentos. Uma classe também pode descrever um componente completo.<br /><br /> Consulte:<br /><br /> -   [Diagramas de componentes UML: Referência](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramas de componentes UML: Diretrizes](../modeling/uml-component-diagrams-guidelines.md)|
|Diagrama de camada|Defina a arquitetura lógica do sistema no que se refere às classes.<br /><br /> Use a validação da camada para garantir que o código permaneça consistente com o design.<br /><br /> Consulte:<br /><br /> -   [Crie diagramas de camada a partir do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de camada: Referência](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de camada: Diretrizes](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)|
|Diagrama de sequência|Defina os tipos de linhas de vida e as operações, parâmetros e valores de retorno para todas as mensagens que a linha de vida pode receber.<br /><br /> Para criar uma linha de vida a partir de um tipo em um diagrama de classe, clique com o botão direito do mouse no tipo e clique em **Criar linha de vida**.<br /><br /> Consulte:<br /><br /> -   [Diagramas de seqüência UML: Referência](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramas de seqüência UML: Diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)|
|Mapa de código|Visualize a organização e as relações no código existente.<br /><br /> Para identificar classes, seus relacionamentos e seus métodos, crie um mapa de código que mostre esses elementos.<br /><br /> Consulte:<br /><br /> -   [Mapear dependências através de suas soluções](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-layer-diagrams"></a><a name="DescribeLayers"></a>Descreva a arquitetura lógica: diagramas de camada
 Diagramas de camada descrevem a arquitetura lógica de um sistema organizando os artefatos em sua solução em grupos abstratos ou *camadas*. Artefatos podem ser muitas coisas, como espaços de nome, projetos, classes, métodos, e assim por diante. As camadas representam e descrevem as funções ou tarefas que os artefatos executam no sistema. Você também pode incluir validação de camadas em suas operações de compilação e check-in para garantir que o código permaneça consistente com seu design.

 Para manter o código consistente com o design, Dinner Now e Lucerna use o seguinte diagrama de camada para validar seu código à medida que ele evolui:

 ![Diagrama de camada do sistema de pagamento integrado](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Diagrama de camada para jantar agora integrado com Lucerna**

 As camadas deste diagrama se ligam aos artefatos correspondentes da solução Dinner Now e Lucerna. Por exemplo, a camada De negócios é ligada ao namespace DinnerNow.Business e seus membros, que agora incluem a classe PaymentApprover. A camada de acesso a recursos é ligada ao namespace DinnerNow.Data. As setas, ou *dependências,* especificam que apenas a camada Empresa pode usar a funcionalidade na camada Acesso a recursos. À medida que as equipes atualizam seu código, a validação de camadas é realizada regularmente para capturar conflitos à medida que ocorrem e para ajudar as equipes a resolvê-los prontamente.

 As equipes trabalham juntas para integrar e testar gradualmente os dois sistemas. Primeiro, eles garantem que o PaymentApprover e o resto do Dinner Now trabalhem um com o outro com sucesso antes de lidarem com o PaymentProcessing.

 O mapa de código a seguir mostra as novas chamadas entre o Dinner Now e o PaymentApprover:

 ![Gráfico de dependência atualizado com sistema integrado](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")

 **Mapa de código com chamadas de método atualizadas**

 Depois que eles confirmam que o sistema funciona como esperado, o Dinner Now comenta o código PaymentProcessing. Os relatórios de validação de camadas estão limpos e o mapa de código resultante mostra que não existem mais dependências do PaymentProcessing:

 ![Gráfico de dependência sem pagamentoprocessamento](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")

 **Mapa de código sem pagamentoprocessamento**

#### <a name="drawing-a-layer-diagram"></a>Desenho de um diagrama de camada
 Um diagrama de camada tem as seguintes características principais:

- *Camadas* descrevem grupos lógicos de artefatos.

- Um *link* é uma associação entre uma camada e um artefato.

   Para criar camadas a partir de artefatos, arraste itens do Solution Explorer, mapas de código, Visualização de Classe ou Navegador de Objetos. Para desenhar novas camadas e, em seguida, vinculá-las a artefatos, use a caixa de ferramentas ou clique com o botão direito do mouse na superfície do diagrama para criar as camadas e arraste os itens para essas camadas.

   O número em uma camada mostra o número de artefatos que estão ligados à camada. Esses artefatos podem ser namespaces, projetos, classes, métodos, e assim por diante. Ao interpretar o número de artefatos em uma camada, lembre-se do seguinte:

  - Se uma camada estiver vinculada a um artefato que contenha outros artefatos, mas não estiver vinculada diretamente a outros artefatos, o número incluirá apenas o artefato vinculado. No entanto, os outros artefatos estão incluídos para análise durante a validação da camada.

     Por exemplo, se uma camada estiver vinculada a um único namespace, o número de artefatos vinculados será 1, mesmo se o namespace contiver classes. Se a camada também tiver links para cada classe no namespace, o número incluirá as classes vinculadas.

  - Se uma camada contiver outras camadas vinculadas a artefatos, a camada de contêiner também estará vinculada a esses artefatos, mesmo que o número na camada de contêiner não inclua esses artefatos.

    Para ver os artefatos vinculados a uma camada, clique com o botão direito do mouse na camada e clique **em Exibir Links** para abrir o Layer **Explorer**.

- Uma *dependência* indica que uma camada pode usar a funcionalidade em outra camada, mas não vice-versa. Uma *dependência bidirecional* indica que uma camada pode usar a funcionalidade em outra camada, e vice-versa.

   Para exibir as dependências existentes no diagrama de camada, clique com o botão direito do mouse na superfície do diagrama e clique **em Gerar dependências**. Para descrever as dependências pretendidas, desenhe novas.

  Consulte:

- [Criar diagramas de camada por meio de código](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramas de camada: referência](../modeling/layer-diagrams-reference.md)

- [Diagramas de camada: diretrizes](../modeling/layer-diagrams-guidelines.md)

- [Validar o código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-layer-diagrams"></a>Resumo: Pontos fortes dos diagramas de camada
 Diagramas de camada ajudam você:

- Descreva a arquitetura lógica de um sistema de acordo com a funcionalidade de seus artefatos.

- Certifique-se de que o código em desenvolvimento esteja em conformidade com o projeto especificado.

#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas

|**Diagrama**|**Descrição**|
|-----------------|---------------------|
|Mapa de código|Visualize a organização e as relações no código existente.<br /><br /> Para criar camadas, gere um mapa de código e, em seguida, agrupe itens no mapa como camadas potenciais. Arraste os grupos do mapa para o diagrama de camadas.<br /><br /> Consulte:<br /><br /> -   [Mapear dependências através de suas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Navegue e reorganize mapas de código](../modeling/browse-and-rearrange-code-maps.md)|
|Diagrama de componente|Descreva componentes, suas interfaces e seus relacionamentos.<br /><br /> Para visualizar camadas, crie um diagrama de componentes que descreva a funcionalidade de diferentes componentes no sistema.<br /><br /> Consulte:<br /><br /> -   [Diagramas de componentes UML: Referência](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramas de componentes UML: Diretrizes](../modeling/uml-component-diagrams-guidelines.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoria**|**Links**|
|------------------|---------------|
|**Fóruns**|-   [Visual Studio Visualização & Ferramentas de Modelagem](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualização & Modelagem SDK (Ferramentas DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Consulte Também
 [Visualize código](../modeling/visualize-code.md) [Criar modelos para o seu aplicativo](../modeling/create-models-for-your-app.md) Use [modelos em seu processo de desenvolvimento](../modeling/use-models-in-your-development-process.md) Use [modelos em desenvolvimento ágil](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) [Valide seu sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md) [Amplie modelos e diagramas uml](../modeling/extend-uml-models-and-diagrams.md)
