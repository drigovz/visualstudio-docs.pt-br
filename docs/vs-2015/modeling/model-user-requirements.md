---
title: Requisitos de usuário de modelo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a94a4bd479c3ad48efe44d3a92e91dc3a050efcd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918264"
---
# <a name="model-user-requirements"></a>Requisitos de usuário do modelo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Visual Studio ajuda você a entender, discutir e comunicar as necessidades dos usuários desenhando diagramas sobre suas atividades e a parte que seu sistema desempenha para ajudá-los a atingir suas metas. Um modelo de requisitos é um conjunto desses diagramas, cada um deles concentra-se em um aspecto diferente das necessidades dos usuários. Para ver uma demonstração em vídeo, consulte: [modelando o domínio de negócios](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain).

 Para ver quais versões do Visual Studio oferecem suporte a cada tipo de modelo, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Um modelo de requisitos ajuda você a:

- Concentre-se no comportamento externo do sistema, separadamente de seu design interno.

- Descreva as necessidades dos usuários e dos participantes com muito menos ambigüidade do que você pode em linguagem natural.

- Defina um glossário consistente de termos que podem ser usados por usuários, desenvolvedores e testadores.

- Reduza lacunas e inconsistências nos requisitos.

- Reduza o trabalho necessário para responder às alterações de requisitos.

- Planeje a ordem na qual os recursos serão desenvolvidos.

- Use os modelos como base para testes do sistema, fazendo uma relação clara entre os testes e os requisitos. Quando os requisitos mudam, essa relação ajuda a atualizar os testes corretamente. Isso garante que o sistema atenda aos novos requisitos.

  Um modelo de requisitos fornece maior benefício se você usá-lo para enfocar discussões com os usuários ou seus representantes e revisitá-lo no início de cada iteração. Você não precisa concluí-lo detalhadamente antes de escrever código. Um aplicativo parcialmente funcional, mesmo que seja muito simplificado, geralmente forma a base mais stimulating para a discussão dos requisitos com os usuários. O modelo é uma maneira eficaz de resumir os resultados dessas discussões. Para obter mais informações, consulte [usar modelos em seu processo de desenvolvimento](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> Durante esses tópicos, "System" significa o sistema ou o aplicativo que você está desenvolvendo. Pode ser uma grande coleção de muitos componentes de software e hardware; ou um único aplicativo; ou um componente de software dentro de um sistema maior. Em todos os casos, o modelo de requisitos descreve o comportamento que é visível de fora do seu sistema, seja por meio de uma interface de usuário ou API.

## <a name="common-tasks"></a>Tarefas comuns
 Você pode criar várias exibições diferentes dos requisitos dos usuários.  Cada exibição fornece um tipo específico de informação.  Quando você cria essas exibições, é melhor movê-las com frequência de uma para outra. Você pode iniciar em qualquer modo de exibição.

|Diagrama ou documento|O que ele descreve em um modelo de requisitos|Seção|
|-------------------------|-----------------------------------------------|-------------|
|Diagrama de caso de uso|Quem usa o sistema e o que eles fazem com ele.|[Descrevendo como o sistema é usado](#UseCases)|
|Diagrama de classe conceitual|Glossário de tipos que são usados para descrever os requisitos; os tipos visíveis na interface do sistema.|[Definindo termos usados para descrever os requisitos](#RequirementsClasses)|
|Diagrama de atividade|Fluxo de trabalho e informações entre atividades executadas por usuários e pelo sistema ou por suas partes.|[Mostrando o fluxo de trabalho entre usuários e seu sistema](#Workflow)|
|Diagrama de sequência|Sequência de interações entre usuários e o sistema ou suas partes. Uma exibição alternativa para o diagrama de atividade.|[Mostrando interações entre usuários e seu sistema](#Sequences)|
|Documentos adicionais ou itens de trabalho|Critérios de desempenho, segurança, usabilidade e confiabilidade.|[Descrevendo os requisitos de qualidade de serviço](#QoSRequirements)|
|Documentos adicionais ou itens de trabalho|Restrições e regras não específicas de um caso de uso específico|[Mostrando regras de negócio](#BusinessRules)|

 Observe que a maioria dos tipos de diagramas pode ser usada para outras finalidades. Para obter uma visão geral dos tipos de diagrama, consulte [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md). Para obter informações básicas sobre diagramas de desenho, consulte [Editar diagramas e modelos UML](../modeling/edit-uml-models-and-diagrams.md).

## <a name="describing-how-your-system-is-used"></a><a name="UseCases"></a> Descrevendo como o sistema é usado
 Crie diagramas de caso de uso para descrever quem usa o sistema e para que eles o usam. Um caso de uso representa uma meta de um usuário do sistema e o procedimento que eles executam para atingir o objetivo.

 Por exemplo, um sistema de vendas online de refeições deve permitir que os clientes escolham itens de um menu e devem permitir que os restaurantes forneçam o menu. Você pode resumir isso em um diagrama de caso de uso:

 ![Casos de uso para cliente e restaurante](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")

 Você também pode mostrar como um caso de uso é composto de casos menores. Por exemplo, a ordenação de uma refeição faz parte da compra de uma refeição, que também inclui pagamento e entrega:

 ![O sistema participa do pagamento, mas não da entrega.](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")

 Você também pode mostrar quais casos de uso estão incluídos no escopo do sistema que você está desenvolvendo. Por exemplo, o sistema na ilustração não faz parte do caso de uso de entrega de refeição. Isso ajuda a definir o contexto para o trabalho de desenvolvimento. (Em um diagrama de caso de uso, os contêineres de subsistema podem ser usados para representar o sistema ou seus componentes.)

 Ele também ajuda sua equipe a discutir o que será incluído em versões sucessivas. Por exemplo, você pode discutir se, na versão inicial do sistema, pagar pela refeição está organizado diretamente entre o restaurante e o cliente, em vez de passar pelo sistema. Nesse caso, você pode mover o pagamento para a refeição fora do jantar agora do retângulo do sistema para a versão inicial.

 Um diagrama de caso de uso fornece apenas um resumo dos casos de uso. Para fornecer descrições mais detalhadas, você pode vincular os casos de uso no diagrama para separar documentos e para outros diagramas. Para saber como fazer isso, consulte [vincular um caso de uso a documentos e diagramas](../modeling/link-a-use-case-to-documents-and-diagrams.md).

 Desenhar um diagrama de caso de uso ajuda sua equipe:

- Concentre-se no que os usuários esperam fazer com o sistema, sem ser distraídosdo por detalhes da implementação.

- Discuta o escopo do sistema ou de versões específicas do sistema.

  Os tópicos a seguir fornecem mais informações:

|Para saber mais|Ler|
|--------------------|----------|
|Informações mais detalhadas sobre como criar casos de uso|[Diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md)|
|Elementos em um diagrama de caso de uso|[Diagramas de caso de uso UML: referência](../modeling/uml-use-case-diagrams-reference.md)|
|Como desenvolver código de casos de uso|[Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)|

## <a name="defining-terms-used-to-describe-requirements"></a><a name="RequirementsClasses"></a> Definindo termos usados para descrever os requisitos
 Você pode usar diagramas de classe UML para ajudá-lo a desenvolver um vocabulário consistente dos conceitos comerciais usados para as seguintes finalidades:

- Pelos próprios usuários para discutir a empresa em que o sistema funciona.

- Para descrever as necessidades dos usuários, por exemplo, nas descrições de casos de uso, regras de negócio e histórias de usuários.

- Os tipos de informações trocadas na API do sistema ou por meio da interface do usuário.

- Descrições dos testes de sistema ou de aceitação.

  Quando são usados para essa finalidade, o conteúdo de um diagrama de classe UML é chamado de diagrama de classe conceitual. (Ela também é conhecida como modelo de *domínio* ou *modelo de classe de análise*.)

  Em um diagrama de classe conceitual, você mostra apenas as classes necessárias nas descrições dos requisitos, sem mostrar qualquer detalhe do design interno do sistema. O diagrama não mostra nenhum detalhe do design interno do sistema. Normalmente, você não mostraria operações ou interfaces em classes conceituais.

  Por exemplo, você poderia desenhar essas classes conceituais no sistema do jantar agora:

  ![Menu classes, ordem, item de menu, item de pedido.](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")

  Um diagrama de classe conceitual fornece o vocabulário de termos que você usa em todo o modelo de requisitos. Por exemplo, na descrição detalhada do caso de uso, encomende uma refeição, você pode escrever:

  O cliente escolhe um *menu* do qual construir um *pedido*e, em seguida, cria *itens de pedido* na *ordem* selecionando *itens de menu* no *menu*.

  Observe como os termos usados nessa descrição são os nomes das classes no modelo. O diagrama remove as ambiguidades das relações entre essas classes. Por exemplo, ele mostra claramente que cada pedido está associado a apenas um menu.

  As noções básicas sobre os requisitos dos usuários podem ser rastreadas com muita compreensão sobre os significados detalhados de palavras. Por exemplo, a maioria dos restaurantes terá um entendimento compartilhado do menu e da ordem dos termos, mas a diferença entre um item em um pedido e um item em um menu é menos clara. Quando os requisitos estão sendo discutidos com os participantes comerciais, é importante expor essas diferenças. O diagrama de classes é uma ferramenta útil para ajudá-lo a esclarecer os termos e suas relações.

  O modelo de classe conceitual pode formar o vocabulário básico pelo qual a lógica de negócios do seu sistema pode ser descrita. Mas as classes no software normalmente serão muito mais complexas do que o modelo conceitual, pois sua implementação deve considerar problemas como desempenho, distribuição, flexibilidade e outros fatores. Várias implementações diferentes de uma classe conceitual são encontradas com frequência em um sistema.

  Por exemplo, pedidos podem ser representados em XML, SQL, HTML e C# em diferentes partes do sistema e em interfaces diferentes entre as partes. A associação entre uma ordem e um menu poderia ser representada de várias maneiras diferentes, como referências no código C#, relações em um banco de dados ou IDs de referência cruzada em XML. Mas, apesar dessas variações, o modelo conceitual fornece informações importantes que são verdadeiras em todas as partes do software. O diagrama de classe no exemplo nos informa que, em cada implementação, haverá apenas um menu associado a cada pedido.

  O desenho de um diagrama de classe de requisitos ajuda sua equipe:

- Defina e Padronize os termos básicos usados em discussões das necessidades dos usuários.

- Esclareça as relações entre esses termos.

  Os tópicos a seguir fornecem mais informações:

|Para saber mais|Ler|
|--------------------|----------|
|Informações mais detalhadas sobre como localizar classes de requisitos|[Diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)|
|Elementos em um diagrama de classe conceitual|[Diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)|
|Como desenvolver código de classes conceituais|[Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)|

 Em um diagrama de classe conceitual, normalmente não é útil posicionar as setas nas associações para representar a navegabilidade. Isso ocorre porque o diagrama não representa uma implementação. As associações representam relações entre objetos do mundo real.

## <a name="showing-business-rules"></a><a name="BusinessRules"></a> Mostrando regras de negócio
 Uma regra de negócio é um requisito que não está associado a um caso de uso específico e deve ser observado em todo o sistema.

 Muitas regras de negócio são restrições sobre as relações entre as classes conceituais. Você pode escrever essas *regras de negócio estáticos* como comentários associados às classes relevantes em um diagrama de classe conceitual. Por exemplo:

 ![Regra no comentário anexada à classe Order.](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")

 *As regras de negócio dinâmicas* restringem as sequências de eventos permitidas. Por exemplo, você usa um diagrama de sequência ou atividade para mostrar que um usuário deve fazer logon antes de executar outras operações em seu sistema.

 No entanto, muitas regras dinâmicas podem ser mais eficientes e genericamente declaradas substituindo-as por regras estáticas. Por exemplo, você pode adicionar um atributo booliano "conectado" a uma classe no modelo de classe conceitual. Você adicionaria logon como a pré-condição do caso de uso de log e a adicionaria como uma pré-condição da maioria dos outros casos de uso. Essa abordagem permite evitar a definição de todas as combinações possíveis de sequências de eventos. Também é mais flexível quando você precisa adicionar novos casos de uso ao modelo.

 Observe que a escolha aqui é sobre como você define os requisitos e que isso é independente de como você implementa os requisitos no código do programa.

 Os tópicos a seguir fornecem mais informações:

|Para saber mais|Ler|
|--------------------|----------|
|Informações mais detalhadas sobre como localizar e registrar regras de negócio estáticos|[Diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)|
|Elementos em um diagrama de classe conceitual|[Diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)|
|Como desenvolver código que siga as regras de negócio|[Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)|

## <a name="describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a> Descrevendo os requisitos de qualidade de serviço
 Há várias categorias de requisitos de qualidade de serviço. Eles incluem o seguinte:

- Desempenho

- Segurança

- Usabilidade

- Confiabilidade

- Robustez

  Você pode incluir alguns desses requisitos nas descrições de casos de uso específicos. Outros requisitos não são específicos para casos de uso e são escritos com mais eficiência em um documento separado. Quando possível, é útil aderir ao vocabulário definido pelo modelo de requisitos. No exemplo a seguir, observe que as palavras principais usadas no requisito são os títulos de atores, casos de uso e classes nas ilustrações anteriores:

  Se um restaurante excluir um item de menu enquanto um cliente estiver solicitando uma refeição, qualquer item de pedido que se refere a esse item de menu será exibido em vermelho.

  Os tópicos a seguir fornecem mais informações:

|Para saber mais|Ler|
|--------------------|----------|
|Anexando documentos adicionais a casos de uso|[Vincular um caso de uso a documentos e diagramas](../modeling/link-a-use-case-to-documents-and-diagrams.md)|
|Como desenvolver código que atenda aos requisitos de qualidade de serviço|[Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)|

## <a name="showing-work-flow-between-users-and-your-system"></a><a name="Workflow"></a> Mostrando o fluxo de trabalho entre usuários e seu sistema
 Você pode usar um diagrama de atividade para mostrar o fluxo de trabalho entre diferentes casos de uso. Geralmente, é útil iniciar um modelo de requisitos desenhando um diagrama de atividade mostrando as principais tarefas que os usuários executam, tanto com o sistema quanto fora dele.

 Por exemplo:

 ![Atividade com três ações e um loop.](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")

 Você pode desenhar diagramas de caso de uso e diagramas de atividade para mostrar diferentes exibições das mesmas informações.  O diagrama de caso de uso é mais eficaz na exibição do aninhamento das ações menores dentro da atividade maior, mas não mostra o fluxo de trabalho. Por exemplo:

 ![Casos de uso para ações anteriores](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")

 Observe que você também pode usar diagramas de atividade para representar algoritmos em seu software, mas ao usar os diagramas para o processo comercial, você se concentra nas ações visíveis fora do sistema.

 Os tópicos a seguir fornecem mais informações:

|Para saber mais|Ler|
|--------------------|----------|
|Mais informações sobre como definir fluxos de trabalho corporativos|[Diagramas de atividade UML: diretrizes](../modeling/uml-activity-diagrams-guidelines.md)|
|Elementos em um diagrama de atividade|[Diagramas de atividade UML: referência](../modeling/uml-activity-diagrams-reference.md)|
|Como desenvolver código de diagramas de atividade|[Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)|

## <a name="showing-interactions-between-users-and-your-system"></a><a name="Sequences"></a> Mostrando interações entre usuários e seu sistema
 Você pode usar um diagrama de sequência para mostrar o intercâmbio de mensagens entre o sistema e os atores externos, ou entre partes do seu sistema. Isso fornece uma exibição das etapas em um caso de uso que mostra claramente a sequência de interações. Os diagramas de sequência são especialmente úteis quando há várias partes de interação em um caso de uso e também onde o sistema tem uma API.

 Por exemplo:

 ![Diagrama de sequência com sistema e atores.](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")

 Uma vantagem dos diagramas de sequência é que é fácil ver quais mensagens são enviadas ao sistema que você está construindo. Para criar o sistema, você pode substituir a linha da vida do sistema único por uma linha de vida separada para cada um de seus componentes e, em seguida, mostrar as interações entre eles em resposta a cada mensagem de entrada.

 Os tópicos a seguir fornecem mais informações:

|Para saber mais|Ler|
|--------------------|----------|
|Mais informações sobre como definir interações|[Diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)|
|Elementos em um diagrama de sequência|[Diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md)|
|Como desenvolver código de diagramas de sequência|[Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)|

## <a name="using-a-model-to-reduce-inconsistencies"></a>Usando um modelo para reduzir inconsistências
 A criação de um modelo geralmente resulta em uma redução significativa em inconsistências e ambiguidades nos requisitos dos usuários. Participantes diferentes geralmente têm diferentes entendimentos do mundo de negócios em que o sistema funciona. Portanto, sua primeira tarefa é resolver essas diferenças entre seus clientes.

 Você descobrirá que muitas perguntas sobre o domínio de negócios surgem naturalmente durante a criação de um modelo. Ao colocar essas perguntas em seus usuários, você reduzirá a necessidade de alterações em um estágio posterior no projeto. Aqui estão algumas perguntas específicas que você pode perguntar a princípio e, em seguida, pergunte aos participantes da empresa se a resposta está nítida:

- Para cada classe no modelo de requisitos, pergunte "qual caso de uso cria instâncias desta classe?" Por exemplo, em um serviço de pedidos de refeições online, você pode perguntar: "qual caso de uso cria instâncias da classe de menu do restaurante?" Isso levaria a uma discussão de como um novo restaurante é inscrito no serviço e contribui com seu menu. Você pode fazer perguntas semelhantes sobre o que cria ou altera atributos e associações.

- Para cada caso de uso no modelo de requisitos, tente descrever o resultado, ou a condição, de cada caso de uso em palavras fornecidas pelos diagramas de classe. Geralmente, é útil mostrar o efeito de um caso de uso ao esboçar instâncias das classes antes e depois de uma ocorrência do caso de uso. Por exemplo, se a condição de caso de uso for "um item de menu é adicionado à ordem do cliente", as instâncias de esboço das classes de item de ordem e de menu. Mostrar os efeitos do caso de uso, como um novo link ou um novo objeto, em uma cor diferente ou em um novo desenho. Isso geralmente leva a discussões sobre quais informações são necessárias no modelo. Embora as classes de requisitos não estejam diretamente preocupados com a implementação, elas descrevem as informações que o sistema precisará armazenar e transmitir.

- Pergunte sobre as restrições de atributos e associações, especialmente restrições envolvendo mais de um atributo ou associação.

- Pergunte sobre sequências válidas e inválidas de casos de uso, desenho de sequência ou diagramas de atividade para ilustra-los.

  Ao examinar as relações entre as exibições que os diferentes diagramas fornecem, você pode entender rapidamente os principais conceitos com os quais os usuários trabalham e ajudá-los a entender o que precisam do sistema. Você também tem um melhor entendimento de quais requisitos os participantes são menos determinados. Você pode planejar desenvolver esses recursos, pelo menos em forma simplificada, em um estágio inicial do projeto, para permitir que os usuários experimentem com eles.

## <a name="see-also"></a>Consulte Também
 [Editar modelos UML e diagramas](../modeling/edit-uml-models-and-diagrams.md) [desenvolver testes de um modelo](../modeling/develop-tests-from-a-model.md) [use modelos em seu](../modeling/use-models-in-your-development-process.md) modelo de processo de desenvolvimento vídeo [de arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md) [: modelagem do domínio de negócios](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain)
