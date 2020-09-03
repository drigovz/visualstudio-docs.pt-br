---
title: Desenvolver testes a partir de um modelo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- tests and requirements
ms.assetid: 40f87192-ba85-4552-8804-314a678261ae
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2b9fec6954706fcecb1281650a8db3d85f08fbd0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669783"
---
# <a name="develop-tests-from-a-model"></a>Desenvolver testes por meio de um modelo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar requisitos e modelos arquitetônicos para ajudá-lo a organizar os testes do seu sistema e seus componentes. Essa prática ajuda a garantir que você teste os requisitos que são importantes para os usuários e outros participantes e ajuda a atualizar os testes rapidamente quando os requisitos mudam. Se você usar [!INCLUDE[TCMext](../includes/tcmext-md.md)] o, também poderá manter links entre os modelos e os testes.

 Para ver quais versões do Visual Studio oferecem suporte a esses recursos, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="system-and-subsystem-testing"></a>Teste do sistema e do subsistema
 O *teste do sistema,* também conhecido como *teste de aceitação*, significa testar se as necessidades dos usuários estão sendo atendidas. Esses testes se preocupam com o comportamento visível externamente do sistema em vez do design interno.

 Os testes do sistema são muito valiosos ao estender ou recriar um sistema. Eles ajudam a evitar a introdução de bugs quando você altera o código.

 Ao planejar qualquer alteração ou extensão em um sistema, é útil começar com um conjunto de testes do sistema que são executados no sistema existente. Em seguida, você pode estender ou ajustar os testes para testar os novos requisitos, fazer as alterações no código e executar novamente o conjunto completo de testes.

 Ao desenvolver um novo sistema, você pode começar a criar testes assim que o desenvolvimento começar. Ao definir testes antes de desenvolver cada recurso, você pode capturar as discussões de requisitos de uma maneira muito específica.

 Os testes de subsistema aplicam os mesmos princípios aos principais componentes de um sistema. Cada componente é testado separadamente de outros componentes. Os testes de subsistema se concentram no comportamento visível nas interfaces de usuário ou API do componente.

 Para obter mais informações sobre como executar testes, consulte [testando o aplicativo](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac).

## <a name="deriving-system-tests-from-a-requirements-model"></a>Derivando testes do sistema de um modelo de requisitos
 Você pode criar e manter uma relação entre os testes do sistema e um modelo de requisitos. Para estabelecer essa relação, você escreve testes que correspondem aos elementos principais do modelo de requisitos. O Visual Studio ajuda a manter essa relação, permitindo que você crie links entre os testes e partes do modelo. Para obter mais informações sobre modelos de requisitos, consulte [requisitos de usuário de modelo](../modeling/model-user-requirements.md).

### <a name="write-tests-for-each-use-case"></a>Gravar testes para cada caso de uso
 Se você usar [!INCLUDE[TCMext](../includes/tcmext-md.md)] o, poderá criar um grupo de testes para cada caso de uso definido em seu modelo de requisitos. Por exemplo, se você tiver uma ordem de uso, faça uma refeição, que inclui criar pedido e Adicionar item ao pedido, você pode criar testes para o geral e mais detalhados desses casos de uso. Para obter mais informações sobre casos de uso, consulte [diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md).

 Essas diretrizes podem ser úteis:

- Cada caso de uso deve ter vários testes, para caminhos principais e resultados excepcionais.

- Quando você descreve um caso de uso no modelo de requisitos, é mais importante definir sua condição, ou seja, a meta que é obtida, do que descrever em detalhes os procedimentos que o usuário segue para atingir o objetivo. Por exemplo, a condição de pedido de uma refeição pode ser que um restaurante esteja preparando uma refeição para um cliente e que o cliente tenha pago. A pré-condição é o critério que os testes devem verificar.

- Basear testes separados nas cláusulas separadas da pré-condição. Por exemplo, crie testes separados para notificar o restaurante do pedido e para receber o pagamento do cliente. Essa separação tem estas vantagens:

  - As alterações em diferentes aspectos dos requisitos geralmente ocorrem de forma independente. Ao separar os testes em diferentes aspectos dessa maneira, você torna mais fácil atualizar os testes quando os requisitos mudam.

  - Se o plano de desenvolvimento implementar um aspecto do caso de uso antes de outro, você poderá habilitar os testes separadamente conforme o desenvolvimento progride.

- Ao projetar os testes, separe a escolha dos dados de teste do código ou script que determina se a pré-condição foi alcançada. Por exemplo, um teste de uma função aritmética simples pode ser: entrada 4; Verifique se a saída é 2. Em vez disso, projete o script como: escolha uma entrada; Multiplique a saída por si mesma e verifique se o resultado é a entrada original. Esse estilo permite que você varie as entradas de teste sem alterar o corpo principal do teste.

#### <a name="linking-tests-to-use-cases"></a>Vinculando testes a casos de uso
 Se você estiver usando [!INCLUDE[TCMlong](../includes/tcmlong-md.md)] o para projetar e executar seus testes, poderá organizar seus testes em itens de trabalho de requisito, caso de uso ou de história de usuário. Você pode vincular esses itens de trabalho a casos de uso em seu modelo. Isso permite que você rastreie rapidamente as alterações de requisitos para os testes e ajuda a acompanhar o progresso de cada caso de uso.

###### <a name="to-link-tests-to-a-use-case"></a>Para vincular testes a um caso de uso

1. No [!INCLUDE[TCMlong](../includes/tcmlong-md.md)] , crie um requisito e baseie um conjunto de testes nele. Para saber como fazer isso, consulte [testando o aplicativo](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac).

    O requisito que você cria é um item de trabalho no [!INCLUDE[vstsTfsShort](../includes/vststfsshort-md.md)] . Pode ser uma história de usuário, um requisito ou um item de trabalho de caso de uso, dependendo do modelo de processo usado pelo seu projeto [!INCLUDE[esprfound](../includes/esprfound-md.md)] . Para obter mais informações, consulte [controlar o trabalho usando Visual Studio Team Services ou Team Foundation Server](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).

2. Vincule o item de trabalho de requisito a um ou mais casos de uso em seu modelo.

    Em um diagrama de caso de uso, clique com o botão direito do mouse em um caso de uso e clique em **vincular ao item de trabalho**. Para obter mais informações, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).

3. Adicione ao conjunto de testes, casos de teste que verificam os casos de uso.

   Normalmente, cada história de usuário ou item de trabalho de requisito será vinculado a vários casos de uso em seu modelo, e cada caso de uso será vinculado a várias histórias ou requisitos do usuário. Isso ocorre porque cada história ou requisito de usuário abrange um conjunto de tarefas que desenvolvem vários casos de uso. Por exemplo, em uma iteração inicial do seu projeto, você pode desenvolver a história de usuário básica na qual um cliente pode escolher itens de um catálogo e tê-los entregues. Em uma iteração posterior, a história pode ser que o usuário paga ao concluir o pedido, e o fornecedor recebe o dinheiro depois de enviar os bens.  Cada história adiciona uma cláusula à condição do caso de uso de mercadorias do pedido.

   Você pode criar links separados de requisitos para as cláusulas da iscondition escrevendo essas cláusulas em comentários separados no diagrama de caso de uso. Você pode vincular cada comentário a um item de trabalho de requisito e vincular o comentário ao caso de uso no diagrama.

### <a name="base-tests-on-the-requirements-types"></a>Testes básicos nos tipos de requisitos
 Os tipos, ou seja, as classes, as interfaces e as enumerações, de um modelo de requisitos descrevem os conceitos e as relações em termos de como os usuários acham e se comunicam sobre seus negócios. Ele exclui tipos preocupados apenas com o design interno do sistema.

 Projete seus testes em termos desses tipos de requisitos. Essa prática ajuda a garantir que quando as alterações nos requisitos forem discutidas, será fácil relacionar as alterações às alterações necessárias nos testes. Ele possibilita discutir os testes e seus resultados pretendidos diretamente com os usuários finais e outros participantes. Isso significa que as necessidades dos usuários podem ser mantidas fora do processo de desenvolvimento e evita o design inadvertido dos testes em relação a possíveis falhas no design.

 Para testes manuais, essa prática envolve a adesão ao vocabulário do modelo de requisitos nos scripts de teste. Para testes automatizados, essa prática envolve o uso de diagramas de classe de requisitos como base para seu código de teste e a criação de funções de acessador e de atualizador para vincular o modelo de requisito ao código.

 Por exemplo, um modelo de requisitos pode incluir o menu de tipos, o item de menu, a ordem e as associações entre eles. Esse modelo representa as informações armazenadas e lidas pelo sistema de pedidos de refeição, mas não representa as complexidades de sua implementação. No sistema de trabalho, pode haver várias realizações diferentes de cada tipo, em bancos de dados, em interfaces do usuário e em APIs. Em um sistema distribuído, pode haver várias variantes de cada instância armazenada em diferentes partes do sistema ao mesmo tempo.

 Para testar um caso de uso, como adicionar item ao pedido, um método de teste pode incluir um código semelhante a este:

```
Order order = … ; // set up an order
// Store prior state:
int countBefore = order.MenuItems.Count;
// Perform use case:
MenuItem chosenItem = …; // choose an item
AddItemToOrder (chosenItem, order);
// Verify part of postcondition:
int countAfter = order.MenuItems.Count;
Assert (countAfter == countBefore = 1);
```

 Observe que esse método de teste usa as classes do modelo de requisitos. As associações e os atributos são percebidos como propriedades do .NET.

 Para fazer isso funcionar, as propriedades das classes devem ser definidas como acessadores ou funções somente leitura, que acessam o sistema para recuperar informações sobre seu estado atual. Métodos que simulam casos de uso como AddItemToOrder devem orientar o sistema por meio de sua API ou por meio de uma camada abaixo de sua interface do usuário. Os construtores de objetos de teste como Order e MenuItem também devem orientar o sistema para criar itens correspondentes dentro do sistema.

 Muitos acessadores e atualizadores já estarão disponíveis por meio da API normal do aplicativo. Mas algumas funções adicionais podem precisar ser gravadas para habilitar os testes. Esses acessadores adicionais e atualizadores são, às vezes, conhecidos como "Instrumentação de teste". Como eles dependem do design interno do sistema, é responsabilidade dos desenvolvedores do sistema fornecê-los, enquanto os testadores gravam o código dos testes em termos do modelo de requisitos.

 Ao escrever testes automatizados, você pode usar testes genéricos para encapsular os acessadores e os atualizadores. Para obter mais informações, consulte [criando um teste automatizado que executa um executável usando testes genéricos](https://msdn.microsoft.com/library/b8dadaf4-4473-49c5-a0d9-46eca9e65d52).

### <a name="tests-for-business-rules"></a>Testes para regras de negócio
 Alguns requisitos não estão diretamente relacionados a um caso de uso. Por exemplo, o DinnerNow Business permite que os clientes escolham vários menus, mas requer que, em todos os pedidos, todos os itens escolhidos sejam de um único menu. Essa regra de negócio pode ser expressa como uma constante sobre as associações entre os pedidos, os menus e os itens no modelo de classe de requisitos.

 Uma regra invariável desse tipo controla não apenas todos os casos de uso atualmente definidos, mas também quaisquer outros casos de uso que serão definidos posteriormente. Portanto, é útil escrevê-lo separadamente de qualquer caso de uso e testá-lo separadamente dos casos de uso.

 Você pode escrever uma regra de negócio invariável como um comentário em um diagrama de classe. Para obter mais informações, consulte [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md).

 Você pode vincular testes a uma regra de negócio vinculando o comentário a um item de trabalho requisito ou de história de usuário, que pode ser vinculado a um conjunto de testes no [!INCLUDE[TCMlong](../includes/tcmlong-md.md)] . Para obter mais informações, consulte [anexando casos de teste a elementos de modelo](#Attaching).

 O desempenho e outros requisitos de qualidade de serviço podem ser observados em comentários em diagramas de caso de uso, atividade ou sequência. Você pode vinculá-los também aos itens de trabalho de requisitos e seus conjuntos de testes.

### <a name="sequence-and-activity-diagrams-for-tests"></a>Diagramas de sequência e atividade para testes
 Se seus requisitos ou modelos de arquitetura incluírem diagramas de sequência ou atividade, você poderá escrever testes que sigam os diagramas diretamente.

 Às vezes, é útil projetar testes que escolham dinamicamente caminhos diferentes por meio de branches e loops no diagrama.

 Tente verificar o estado do sistema após cada mensagem ou ação. Isso pode exigir instrumentação adicional.

## <a name="deriving-subsystem-tests-from-models"></a>Derivando testes de subsistema de modelos
 No design de alto nível de um sistema grande, você pode identificar componentes ou subsistemas. Elas representam partes que podem ser criadas separadamente ou que estão localizadas em computadores diferentes, ou são módulos reutilizáveis que podem ser recombinadas de várias maneiras. Para obter mais informações, consulte [diagramas de componentes UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md).

 Você pode aplicar a cada componente principal os mesmos princípios usados para o sistema completo. Em um projeto grande, cada componente pode ter seu próprio modelo de requisitos. Em projetos menores, um modelo de arquitetura ou design de alto nível pode ser criado para mostrar os principais componentes e suas interações. Para obter mais informações, consulte [modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md).

 Em ambos os casos, você pode estabelecer uma relação entre os elementos do modelo e os testes do subsistema da mesma maneira que faria entre o modelo de requisitos e os testes do sistema.

### <a name="isolate-components-with-provided-and-required-interfaces"></a>Isole componentes com as interfaces fornecidas e necessárias
 É útil identificar todas as dependências que um componente tem em outras partes do seu sistema ou serviços externos e representá-las como interfaces necessárias. Esse exercício geralmente leva a algum redesign que deixa o componente muito mais dissociado e facilmente separáveis do restante do seu design.

 Uma vantagem dessa desassociação é que o componente pode ser executado para teste, substituindo por objetos fictícios os serviços que ele geralmente usa. Esses são os componentes que são configurados para fins de teste. Um componente fictício fornece a interface que seu componente requer, respondendo a consultas com dados simulados. Os componentes fictícios formam parte de um conjunto completo de testes que você pode conectar a todas as interfaces do componente.

 Um benefício do teste de simulação é que você pode desenvolver seu componente, enquanto os outros componentes cujos serviços serão usados ainda estão em desenvolvimento.

## <a name="maintain-the-relationships-between-tests-and-model"></a>Manter as relações entre os testes e o modelo
 Em um projeto típico que executa uma iteração a cada poucas semanas, uma revisão de requisitos é mantida perto do início de cada iteração. A reunião discute os recursos que devem ser entregues na próxima iteração. Um modelo de requisitos pode ser usado para ajudar a discutir os conceitos, cenários e sequências de ações que serão desenvolvidos. Os participantes de negócios definem as prioridades, os desenvolvedores fazem estimativas e os testadores garantem que o comportamento esperado de cada recurso seja capturado corretamente.

 Escrever testes é a maneira mais eficiente de definir um requisito e também é uma maneira eficaz de garantir que uma pessoa tenha uma compreensão clara do que é necessário. No entanto, enquanto escrever testes leva muito tempo para ser feito durante um workshop de especificação, a criação de modelos pode ser feita muito mais rapidamente.

 Do ponto de vista dos testes, um modelo de requisitos pode ser visto como um atalho para os testes. Portanto, é importante manter a relação entre os testes e o modelo em todo o projeto.

## <a name="attaching-test-cases-to-model-elements"></a><a name="Attaching"></a> Anexando casos de teste a elementos de modelo
 Se o seu projeto usa [!INCLUDE[TCMlong](../includes/tcmlong-md.md)] , você pode vincular testes aos elementos em seu modelo. Isso permite que você encontre rapidamente os testes afetados por uma alteração nos requisitos e ajuda a acompanhar a extensão para a qual um requisito foi percebido.

 Você pode vincular testes a todos os tipos de elemento. Estes são alguns exemplos:

- Vincule um caso de uso aos testes que o exercitam.

- Escreva as cláusulas de uma subcondição de caso de uso ou meta, para comentários que estão vinculados ao caso de uso e, em seguida, vincule os testes a cada comentário.

- Escreva regras invariáveis em comentários em diagramas de classe ou diagramas de atividade e vincule-as a testes.

- Vincular testes a um diagrama de atividade ou a atividades individuais.

- Vincule um conjunto de testes ao componente ou ao subsistema que ele testa.

#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Para vincular testes a um elemento de modelo ou relação

1. No [!INCLUDE[TCMlong](../includes/tcmlong-md.md)] , crie um requisito e baseie um conjunto de testes nele. Para saber como fazer isso, consulte [testando o aplicativo](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac).

     O requisito que você cria é um item de trabalho no [!INCLUDE[vstsTfsShort](../includes/vststfsshort-md.md)] . Pode ser uma história de usuário, um requisito ou um item de trabalho de caso de uso, dependendo do modelo de processo usado pelo seu projeto [!INCLUDE[esprfound](../includes/esprfound-md.md)] . Para obter mais informações, consulte [controlar o trabalho usando Visual Studio Team Services ou Team Foundation Server](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).

2. Vincule o item de trabalho de requisito a um ou mais elementos em seu modelo.

     Em um diagrama de modelagem, clique com o botão direito do mouse em um elemento, comentário ou relação e clique em **vincular ao item de trabalho**. Para obter mais informações, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).

3. Adicione ao conjunto de testes, casos de teste que verificam o requisito expresso no elemento de modelo.

## <a name="see-also"></a>Consulte Também
 [Crie modelos para o modelo de](../modeling/create-models-for-your-app.md) [requisitos de usuário modelo](../modeling/model-user-requirements.md) [de aplicativo sua arquitetura de](../modeling/model-your-app-s-architecture.md) [análise e modelagem](../modeling/analyze-and-model-your-architecture.md) de aplicativos
