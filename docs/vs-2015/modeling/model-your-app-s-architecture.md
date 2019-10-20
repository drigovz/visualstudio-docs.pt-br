---
title: Modele a&#39;arquitetura do seu aplicativo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
ms.assetid: aedce746-9df5-49e1-9662-67eb1b83d313
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41dbb7b996c32af10010694935cbd3660b462f73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609645"
---
# <a name="model-your-app39s-architecture"></a>Modele a&#39;arquitetura do seu aplicativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para ajudar a garantir que o seu sistema de software ou aplicativo atenda às necessidades de seus usuários, você pode criar modelos no Visual Studio como parte da sua descrição da estrutura geral e do comportamento do seu aplicativo ou sistema de software. Usando modelos, você também pode descrever padrões que são usados em todo o design. Esses modelos ajudam você a entender a arquitetura existente, a discutir alterações e a comunicar suas intenções claramente.

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 A finalidade de um modelo é reduzir as ambiguidades que ocorrem nas descrições de idioma natural e ajudar você e seus colegas a visualizar o design e a discutir designs alternativos. Um modelo deve ser usado junto com outros documentos ou discussões. Por si só, um modelo não representa uma especificação completa da arquitetura.

> [!NOTE]
> Ao longo deste tópico, "System" significa o software que você está desenvolvendo. Pode ser uma grande coleção de muitos componentes de software e hardware, ou um único aplicativo ou uma parte de um aplicativo.

 A arquitetura de um sistema pode ser dividida em duas áreas:

- [Design de alto nível](#Structure). Isso descreve os principais componentes e como eles interagem entre si para atender a cada requisito. Se o sistema for grande, cada componente poderá ter seu próprio design de alto nível, que mostra como ele é composto por componentes menores.

- [Padrões de design](#Patterns) e convenções usadas em todos os designs dos componentes. Um padrão descreve uma abordagem específica para atingir uma meta de programação. Usando os mesmos padrões em um design, sua equipe pode reduzir o custo de fazer alterações e desenvolver novos softwares.

## <a name="Structure"></a>Design de alto nível
 Um design de alto nível descreve os principais componentes do seu sistema e como eles interagem entre si para atingir as metas do design. As atividades na lista a seguir estão envolvidas no desenvolvimento do design de alto nível, embora não necessariamente em uma sequência específica.

 Se você estiver atualizando o código existente, poderá começar descrevendo os principais componentes. Verifique se você entendeu as alterações nos requisitos do usuário e depois adicione ou modifique as interações entre os componentes. Se você estiver desenvolvendo um novo sistema, comece compreendendo os principais recursos das necessidades dos usuários. Você pode explorar sequências de interações para os principais casos de uso e, em seguida, consolidar as sequências em um design de componente.

 Em todos os casos, é útil desenvolver as diferentes atividades em paralelo e desenvolver código e testes em um estágio inicial. Evite tentar concluir um desses aspectos antes de iniciar outro. Normalmente, os requisitos e sua compreensão da melhor maneira de criar o sistema serão alterados enquanto você estiver escrevendo e testando o código. Portanto, você deve começar compreendendo e codificando os principais recursos dos requisitos e do seu design. Preencha os detalhes em iterações posteriores do projeto.

- [Noções básicas sobre os requisitos](#Requirements). O ponto de partida de qualquer design é uma compreensão clara das necessidades dos usuários.

- [Padrões de arquitetura](#BigDecisions). As escolhas feitas sobre as principais tecnologias e os elementos arquitetônicos do sistema.

- [Componentes e suas interfaces](#Components). Você pode desenhar diagramas de componentes para mostrar as partes principais do sistema e mostrar as interfaces por meio das quais eles interagem entre si. As interfaces de cada componente incluem todas as mensagens identificadas nos diagramas de sequência.

- [Interações entre componentes](#Interactions). Para cada caso de uso, evento ou mensagem de entrada, você pode desenhar um diagrama de sequência que mostra como os principais componentes do sistema interagem para atingir a resposta necessária.

- [Modelo de dados dos componentes e interfaces](#Data). Você pode desenhar diagramas de classe para descrever as informações que são passadas entre componentes e armazenadas dentro dos componentes.

## <a name="Requirements"></a>Noções básicas sobre os requisitos
 O design de alto nível de um aplicativo completo é desenvolvido com mais eficiência junto com um modelo de requisitos ou outra descrição das necessidades dos usuários. Para obter mais informações sobre modelos de requisitos, consulte [requisitos de usuário de modelo](../modeling/model-user-requirements.md).

 Se o sistema que você está desenvolvendo for um componente em um sistema maior, parte ou todos os seus requisitos poderão ser incorporados em interfaces programáticas.

 O modelo de requisitos fornece essas informações essenciais:

- Interfaces fornecidas. Uma interface fornecida lista os serviços ou operações que o sistema ou componente deve fornecer a seus usuários, sejam usuários humanos ou outros componentes de software.

- Interfaces necessárias. Uma interface necessária lista os serviços ou operações que o sistema ou componente pode usar. Em alguns casos, você poderá criar todos esses serviços como parte do seu próprio sistema. Em outros casos, especialmente se você estiver criando um componente que pode ser combinado com outros componentes em muitas configurações, a interface necessária será definida por considerações externas.

- Requisitos de qualidade de serviço. O desempenho, a segurança, a robustez e outras metas e restrições que o sistema deve atender.

  O modelo de requisitos é escrito a partir do ponto de vista dos usuários do sistema, sejam eles pessoas ou outros componentes de software. Eles não sabem nada do funcionamento interno do seu sistema. Por outro lado, seu objetivo em um modelo de arquitetura é descrever os trabalhos internos e mostrar como eles atendem às necessidades dos usuários.

  Manter os requisitos e modelos de arquitetura separados é útil porque torna mais fácil discutir os requisitos com os usuários. Ele também ajuda a refatorar o design e a considerar as arquiteturas alternativas, mantendo os requisitos inalterados.

  Você pode separar os requisitos e modelos arquitetônicos de duas maneiras alternativas:

- Mantenha-os na mesma solução, mas em projetos diferentes. Eles aparecerão como modelos separados no Gerenciador de modelos UML. Diferentes membros da equipe podem trabalhar em paralelo nos modelos. Tipos limitados de rastreamento podem ser criados entre os modelos.

- Coloque-os no mesmo modelo UML, mas em pacotes diferentes. Isso facilita o rastreamento de dependências entre os modelos, mas impede que mais de uma pessoa por vez trabalhe no modelo. Além disso, um modelo muito grande levará mais tempo para carregar no Visual Studio. Portanto, essa abordagem é menos adequada para projetos grandes.

  A quantidade de detalhes que você deve colocar em requisitos ou em um modelo de arquitetura depende da escala do projeto e do tamanho e da distribuição da equipe. Uma pequena equipe em um pequeno projeto pode não ultrapassar o esboço de um diagrama de classe dos conceitos de negócios e de alguns padrões de design; um projeto grande distribuído em mais de uma região precisaria de maneira muito mais detalhada.

## <a name="BigDecisions"></a>Padrões de arquitetura
 No início de um desenvolvimento, você precisa escolher as principais tecnologias e elementos dos quais o design depende. As áreas nas quais essas opções devem ser feitas incluem o seguinte:

- Opções de tecnologia base, como a escolha entre um banco de dados e um sistema de arquivos, e a escolha entre um aplicativo em rede e um cliente Web, e assim por diante.

- Opções de estruturas, como uma opção entre Windows Workflow Foundation ou ADO.NET Entity Framework.

- Opções de método de integração, por exemplo, entre um barramento de serviço corporativo ou um canal ponto a ponto.

  Essas opções são frequentemente determinadas pelos requisitos de qualidade de serviço, como escala e flexibilidade, e podem ser feitas antes que os requisitos detalhados sejam conhecidos. Em um sistema grande, a configuração de hardware e software está fortemente relacionada.

  As seleções que você faz afetam a maneira como você usa e interpreta o modelo de arquitetura. Por exemplo, em um sistema que usa um banco de dados, as associações em um diagrama de classe podem representar relações ou chaves estrangeiras no banco de dados, enquanto em um sistema baseado em arquivos XML, as associações podem indicar referências cruzadas que usam XPath. Em um sistema distribuído, as mensagens em um diagrama de sequência podem representar mensagens em uma conexão; em um aplicativo independente, eles podem representar chamadas de função.

## <a name="Components"></a>Componentes e suas interfaces
 As principais recomendações desta seção são as seguintes:

- Crie diagramas de componentes para mostrar as partes principais do seu sistema.

- Desenhe dependências entre os componentes do ou suas interfaces para mostrar a estrutura do sistema.

- Use interfaces nos componentes para mostrar os serviços que cada componente fornece ou requer.

- Em um design grande, você pode desenhar diagramas separados para decompor cada componente em partes menores.

  Esses pontos são elaborados no restante desta seção.

### <a name="components"></a>Componentes
 As exibições centrais de um modelo de arquitetura são os diagramas de componentes que mostram as partes principais do sistema e como elas dependem umas das outras. Para obter mais informações sobre diagramas de componente, consulte [diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md).

 ![Diagrama de componente UML mostrando partes](../modeling/media/uml-barecomponent.png "UML_BareComponent")

 Um diagrama de componente típico para um sistema grande pode incluir componentes como estes:

- Presentation. O componente que fornece acesso ao usuário, normalmente em execução em um navegador da Web.

- Componentes de serviço Web. Fornece conexão entre clientes e servidores.

- Controladores de caso de uso. Conduza o usuário pelas etapas de cada cenário.

- Núcleo de negócios. Contém classes baseadas em classes no modelo de requisitos, implementa as principais operações e impõe restrições de negócios.

- Banco. Armazena os objetos comerciais.

- Log e tratamento de erros de componentes.

### <a name="dependencies-between-components"></a>Dependências entre componentes
 Além dos próprios componentes, você pode mostrar as dependências entre eles. Uma seta de dependência entre dois componentes mostra que as alterações no design de um podem afetar o design do outro. Isso geralmente acontece porque um componente usa os serviços ou funções que são fornecidos pelo outro componente, direta ou indiretamente.

 Uma arquitetura bem estruturada tem uma disposição clara das dependências, nas quais essas condições são verdadeiras:

- Não há loops em um mapa de código.

- Os componentes podem ser organizados em camadas nas quais cada dependência vai de um componente em uma camada para um componente no próximo. Todas as dependências entre duas camadas entram na mesma direção.

  Você pode mostrar dependências diretamente entre componentes ou pode mostrar dependências entre as interfaces necessárias e fornecidas que estão anexadas aos componentes. Usando interfaces, você pode definir quais operações são usadas em cada dependência. Normalmente, as dependências são mostradas entre os componentes quando os diagramas são primeiro desenhados e substituídos por dependências entre as interfaces à medida que mais informações são adicionadas. Ambas as versões são descrições corretas do software, mas a versão com interfaces fornece mais detalhes do que a versão anterior.

  O gerenciamento de dependências é mais importante para a produção de software passível de manutenção. Os diagramas de componente devem refletir todas as dependências em seu código. Se o código já existir, certifique-se de que todas as dependências sejam mostradas nos diagramas. Se o código estiver sendo desenvolvido, verifique se ele não inclui dependências que não estão planejadas no diagrama de componentes. Para ajudá-lo a descobrir dependências no código, você pode gerar diagramas de camada. Para ajudá-lo a garantir que suas restrições de dependência planejadas sejam atendidas, você pode validar o código em relação a diagramas de camada. Para obter mais informações, consulte [diagramas de camada: referência](../modeling/layer-diagrams-reference.md).

### <a name="interfaces"></a>Interfaces
 Ao colocar interfaces em seus componentes, você pode separar e nomear os principais grupos de operações que são fornecidos por cada componente. Por exemplo, os componentes em um sistema de vendas baseado na Web podem ter uma interface por meio da qual os clientes compram bens, uma interface por meio da qual os fornecedores atualizam seus catálogos e uma terceira interface por meio da qual o sistema é gerenciado.

 Um componente pode ter qualquer número de interfaces fornecidas e necessárias. As interfaces fornecidas mostram os serviços que o componente fornece para outros componentes usarem. As interfaces necessárias mostram os serviços que o componente usa em outros componentes.

 Se você definir as interfaces fornecidas e obrigatórias, isso ajudará a separar o componente de forma limpa do restante do design, para que você possa usar estas técnicas:

- Coloque o componente em um equipamento de teste no qual os componentes adjacentes sejam simulados pelo equipamento de teste.

- Desenvolva seu componente independentemente dos outros componentes.

- Reutilize o componente em outros contextos acoplando suas interfaces a componentes diferentes.

  Quando você quiser definir a lista de operações em uma interface, poderá criar outra exibição da interface em um diagrama de classes UML. Para fazer isso, localize a interface no Gerenciador de modelos UML e arraste-a para um diagrama de classe. Em seguida, você pode adicionar operações à interface.

  Uma operação em uma interface UML pode representar qualquer maneira na qual um comportamento de um componente possa ser invocado. Ele pode representar uma solicitação de serviço da Web, um sinal ou uma interação de algum outro tipo ou uma chamada de função de programa comum.

  Para determinar quais operações adicionar, crie diagramas de sequência para mostrar como os componentes interagem uns com os outros. Consulte [interações entre componentes](#Interactions). Cada um desses diagramas de sequência mostra as interações que ocorrem em um caso de uso diferente. Dessa maneira, você pode adicionar gradualmente à lista de operações na interface de cada componente, à medida que explora os casos de uso.

### <a name="decomposing-a-component-into-parts"></a>Decompondo um componente em partes
 Você pode aplicar o procedimento descrito nas seções anteriores para cada componente.

 Dentro de cada componente, você pode mostrar seus subcomponentes como partes. Uma parte é efetivamente um atributo de seu componente pai, que é um tipo de classe. Cada parte tem seu próprio tipo, que pode ser um componente. Você pode posicionar esse componente em um diagrama e mostrar suas partes. Para obter mais informações, consulte [diagramas de componentes UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md).

 É útil aplicar essa técnica ao sistema inteiro. Desenhe como um único componente e mostre seus principais componentes como partes. Isso ajuda a identificar claramente as interfaces do seu sistema com o mundo externo.

 Quando o design de um componente usa outro componente, com freqüência você tem a opção de representá-lo como parte ou como um componente separado que você acessa por meio de uma interface necessária.

 Use partes nas seguintes situações:

- O design do componente pai sempre deve usar o tipo de componente da parte. Portanto, o design da parte é integral para o design do componente pai.

- O componente pai não tem nenhuma existência concreta. Por exemplo, você poderia ter um componente conceitual chamado camada de apresentação que representa uma coleção de componentes reais que lidam com exibições e interações do usuário.

  Use componentes separados acessados por meio de interfaces necessárias nessas situações:

- O componente de solicitação pode ser acoplado por meio de suas interfaces para fornecer componentes diferentes em tempo de execução.

- O design é que seria fácil substituir um provedor por outro.

  O uso de interfaces necessárias geralmente é preferível ao uso de partes. Embora o design possa levar mais tempo, o sistema resultante é mais flexível. Também é mais fácil testar os componentes separadamente. Isso permite menos acoplamento em seus planos de desenvolvimento.

## <a name="Interactions"></a>Interações entre componentes
 As principais recomendações desta seção são as seguintes:

- Identifique os casos de uso do seu sistema.

- Para cada caso de uso, desenhe um ou mais diagramas para mostrar como os componentes do seu sistema atingem o resultado necessário colaborando entre si e com os usuários. Normalmente, são diagramas de sequência ou diagramas de atividade.

- Use interfaces para especificar as mensagens recebidas por cada componente.

- Descreva os efeitos das operações nas interfaces.

- Repita o procedimento para cada componente, mostrando como suas partes interagem.

  Por exemplo, em um sistema de vendas baseado na Web, o modelo de requisitos pode definir uma compra de cliente como um caso de uso. Você pode criar um diagrama de sequência para mostrar as interações que o cliente tem com os componentes na camada de apresentação e para mostrar as interações que eles têm com os componentes de depósito e contabilidade.

### <a name="identifying-the-initiating-events"></a>Identificando os eventos de inicialização
 O trabalho feito pela maioria dos sistemas de software pode ser convenientemente dividido pelas respostas que ele fornece a diferentes entradas ou eventos. O evento de inicialização pode ser um dos seguintes eventos:

- A primeira ação em um caso de uso. Ele pode aparecer no modelo de requisitos como uma etapa em um caso de uso ou em uma ação em um diagrama de atividade. Para obter mais informações, [diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md) e [diagramas de atividade UML: diretrizes](../modeling/uml-activity-diagrams-guidelines.md).

- Uma mensagem em uma interface programática. Se o sistema que você está desenvolvendo for um componente em um sistema maior, ele deverá ser descrito como uma operação em uma das interfaces do componente. Consulte [componentes e suas interfaces](#Components).

- Uma condição específica que é monitorada pelo seu sistema ou um evento regular, como uma hora do dia.

### <a name="describe-the-computations"></a>Descrever os cálculos
 Desenhe diagramas de sequência para mostrar como os componentes respondem ao evento inicial.

 Desenhe uma linha de vida para cada instância de componente que usa parte em uma sequência típica. Em alguns casos, pode haver mais de uma instância de cada tipo. Se você tiver descrito todo o seu sistema como um único componente, deve haver uma linha de vida para cada parte que ela contém.

 Para obter mais informações, consulte [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md).

 Os diagramas de atividade também são úteis em alguns casos. Por exemplo, se os componentes tiverem um fluxo contínuo de dados, você poderá descrevê-lo como um fluxo de objeto. Se o componente tiver um algoritmo complexo, você poderá descrevê-lo como um fluxo de controle. Certifique-se de tornar claro qual componente executa cada ação, por exemplo, usando comentários. Para obter mais informações, consulte [diagramas de atividade UML: diretrizes](../modeling/uml-activity-diagrams-guidelines.md).

### <a name="specify-the-operations"></a>Especificar as operações
 Os diagramas mostram as operações que são executadas por cada componente, representadas como mensagens em um diagrama de sequência ou ações em um diagrama de atividade.

 Colete essas operações juntas para cada componente. Crie interfaces fornecidas no componente e adicione as operações às interfaces. Normalmente, uma interface separada é usada para cada tipo de cliente. As operações são adicionadas mais facilmente às interfaces no **Gerenciador de modelos UML**. Da mesma maneira, colete as operações que cada componente usa dos outros componentes e coloque-as nas interfaces necessárias anexadas ao componente.

 É útil adicionar comentários aos diagramas de atividade ou de sequência para observar o que foi obtido após cada operação. Você também pode escrever o efeito de cada operação em sua propriedade de **condição local** .

### <a name="Data"></a>Modelo de dados dos componentes e interfaces
 Defina os parâmetros e os valores de retorno de cada operação nas interfaces de componente. Onde as operações representam invocações, como solicitações de serviço Web, os parâmetros são aquelas que são enviadas como parte da solicitação. Onde vários valores são retornados de uma operação, você pode usar parâmetros com a propriedade **Direction** definida como **out**.

 Cada parâmetro e valor de retorno têm um tipo. Você pode definir esses tipos usando diagramas de classe UML. Você não precisa representar detalhes de implementação nesses diagramas. Por exemplo, se você estiver descrevendo os dados transmitidos como XML, poderá usar uma associação para representar qualquer tipo de referência cruzada entre os nós do XML e usar classes para representar nós.

 Use comentários para descrever as restrições de negócios nas associações e atributos. Por exemplo, se todos os itens na ordem de um cliente devem vir do mesmo fornecedor, você pode descrever isso por referência às associações entre os itens do pedido e os itens no catálogo de produtos e entre o item de catálogo e seu fornecedor.

## <a name="Patterns"></a>Padrões de design
 Um padrão de design é uma estrutura de tópicos de como criar um aspecto específico do software, especialmente um que se repete em diferentes partes do sistema. Ao adotar uma abordagem uniforme em todo o projeto, você pode reduzir o custo de design, garantir a consistência na interface do usuário e reduzir o custo de entender e alterar o código.

 Alguns padrões de design gerais, como o observador, são bem conhecidos e amplamente aplicáveis. Além disso, há padrões que são aplicáveis apenas ao seu projeto. Por exemplo, em um sistema de vendas na Web, haverá várias operações no código em que as alterações são feitas no pedido de um cliente. Para garantir que o estado do pedido seja exibido com precisão em cada estágio, todas essas operações devem seguir um protocolo específico para atualizar o banco de dados.

 Parte do trabalho da arquitetura de software é determinar quais padrões devem ser adotados em todo o design. Normalmente, essa é uma tarefa em andamento, pois novos padrões e aprimoramentos para padrões existentes serão descobertos à medida que o projeto progride. É útil organizar o plano de desenvolvimento para que você exerça cada um dos seus principais padrões de design em um estágio inicial.

 A maioria dos padrões de design pode ser parcialmente incorporada no código do Framework. Parte do padrão pode ser reduzida para exigir que o desenvolvedor Use classes ou componentes específicos, como uma camada de acesso ao banco de dados que garante que o banco de dados seja manipulado corretamente.

 Um padrão de design é descrito em um documento e normalmente inclui estas partes:

- nomes.

- Descrição do contexto no qual ele é aplicável. Quais critérios devem fazer um desenvolvedor considerar a aplicação desse padrão?

- Breve explicação do problema que ele resolve.

- Modelo das partes principais e suas relações. Elas podem ser classes ou componentes e interfaces, com associações e dependências entre eles. Os elementos geralmente se enquadram em duas categorias:

  - Elementos que o desenvolvedor deve replicar em todas as partes do código em que o padrão é usado. Você pode usar tipos de modelo para descrever esses. Para obter mais informações, consulte [diagramas de caso de uso UML: referência](../modeling/uml-use-case-diagrams-reference.md).

  - Elementos que descrevem classes de estrutura que o desenvolvedor deve usar.

- Modelo das interações entre as partes, usando diagramas de sequência ou de atividade.

- Convenções de nomenclatura.

- Descrição de como o padrão resolve o problema.

- Descrição das variações que os desenvolvedores podem adotar.

## <a name="see-also"></a>Consulte também
 [Editar modelos e diagramas UML](../modeling/edit-uml-models-and-diagrams.md) [Visualizar](../modeling/visualize-code.md) [requisitos de usuário do modelo](../modeling/model-user-requirements.md) de código [desenvolver testes de modelos de](../modeling/develop-tests-from-a-model.md) uso de modelo [em seu processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)
