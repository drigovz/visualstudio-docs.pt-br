---
title: 'Diagramas de caso de uso UML: diretrizes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c9ccd5285f9a2744704c0ee13094a1dac31c53b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302842"
---
# <a name="uml-use-case-diagrams-guidelines"></a>Diagramas de caso de uso UML: diretrizes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No Visual Studio, você pode desenhar um *diagrama de caso de uso* para resumir quem usa seu aplicativo ou sistema e o que eles podem fazer com ele. Para criar um diagrama de caso de uso UML, no menu **arquitetura** , clique em **novo UML ou diagrama de camada**.

 Para uma demonstração em vídeo, consulte [organizando recursos em casos de uso](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases).

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Com a ajuda de um diagrama de caso de uso, você pode discutir e se comunicar:

- Os cenários nos quais seu sistema ou aplicativo interage com pessoas, organizações ou sistemas externos.

- As metas que ele ajuda esses atores a atingir.

- O escopo do seu sistema.

  Um diagrama de caso de uso não mostra os detalhes dos casos de uso: ele resume apenas algumas das relações entre casos de uso, atores e sistemas. Em particular, o diagrama não mostra a ordem em que as etapas são executadas para atingir as metas de cada caso de uso. Você pode descrever esses detalhes em outros diagramas e documentos, que podem ser vinculados a cada caso de uso. Para obter mais informações, consulte [descrevendo casos de uso em detalhes](#Details) neste tópico.

  As descrições que você fornecer para casos de uso usarão vários termos relacionados ao domínio no qual o sistema funciona, como venda, menu, cliente e assim por diante. É importante definir esses termos e suas relações claramente, e você pode fazer isso com a ajuda de um diagrama de classes UML. Para obter mais informações, consulte [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md).

  Os casos de uso lidam apenas com os requisitos funcionais de um sistema. Outros requisitos, como regras de negócio, requisitos de qualidade de serviço e restrições de implementação, devem ser representados separadamente. A arquitetura e os detalhes internos também devem ser descritos separadamente. Para obter mais informações sobre como definir os requisitos de usuário, consulte [modelo requisitos de usuário](../modeling/model-user-requirements.md).

  Os exemplos usados neste tópico estão relacionados a um site no qual os clientes podem solicitar refeições de restaurantes locais.

  ![Elementos em um diagrama de caso de uso](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

- Um *ator* (1) é uma classe de pessoa, organização, dispositivo ou componente de software externo que interage com seu sistema. Os atores de exemplo são **cliente**, **restaurante**, **sensor de temperatura**, **autorizador de cartão de crédito.**

- Um *caso de uso* (2) representa as ações que são executadas por um ou mais atores na busca de uma meta específica. Exemplos de casos de uso são **refeição de pedido**, **menu atualizar**, **pagamento de processo**.

   Em um diagrama de caso de uso, os casos de uso são associados (3) aos atores que os executam.

- Seu *sistema (4)* é tudo o que você está desenvolvendo. Pode ser um pequeno componente de software, cujos atores são apenas outros componentes de software; ou pode ser um aplicativo completo; ou pode ser um grande pacote distribuído de aplicativos implantados em vários computadores e dispositivos. Os subsistemas de exemplo são **site de pedido de refeição**, empresa de entrega de **refeições**, **site versão 2**.

   Um diagrama de caso de uso pode mostrar quais casos de uso têm suporte do seu sistema ou de seus subsistemas.

## <a name="BasicSteps"></a>Etapas básicas para desenhar diagramas de caso de uso

> [!NOTE]
> As etapas detalhadas para a criação de qualquer um dos diagramas de modelagem são descritas em [editar modelos e diagramas UML](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-new-use-case-diagram"></a>Para criar um novo diagrama de caso de uso

1. No menu **arquitetura** , clique em **novo UML ou diagrama de camada**.

2. Em **modelos**, clique em **diagrama de caso de UMLUse**.

3. Nomeie o diagrama.

4. Em **Adicionar ao projeto de modelagem**, selecione um projeto de modelagem existente em sua solução ou **crie um novo projeto de modelagem**e clique em **OK**.

#### <a name="to-draw-a-use-case-diagram"></a>Para desenhar um diagrama de caso de uso

1. Arraste os limites do **subsistema** da caixa de ferramentas para o diagrama, para representar todo o seu sistema ou seus principais componentes.

    - Você pode desenhar um diagrama de caso de uso sem limites do sistema se não quiser descrever quais casos de uso têm suporte no seu sistema ou seus componentes.

    - Arraste o canto de um sistema para torná-lo maior, se for necessário.

    - Renomeie-o adequadamente.

2. Arraste **atores** da caixa de ferramentas para o diagrama (colocando-os fora de qualquer limite do sistema).

    - Os atores representam classes de usuários, organizações e sistemas externos que interagem com o sistema.

    - Renomeie-os. Por exemplo: **cliente, restaurante, agência de cartão de crédito.**

3. Arraste os **casos de uso** da caixa de ferramentas para os sistemas apropriados.

    - Casos de uso representam as atividades que os atores executam com a ajuda do seu sistema.

    - Renomeie-os usando títulos que os próprios atores entenderão. Não use títulos relacionados ao seu código. Por exemplo: **pedido de refeição, pagar por refeição, entregar refeição**.

    - Comece com transações principais, como **pedido de refeição**, deixando até interações menores posteriores, como **selecionar item de menu**.

    - Coloque cada caso de uso no sistema ou no subsistema principal que ofereça suporte a ele (ignorando qualquer fachada ou componente envolvido apenas na conexão com o usuário).

    - Você pode desenhar um caso de uso fora do limite do sistema para mostrar que ele não é suportado pelo seu sistema, talvez em uma versão ou liberação específica.

4. Clique em **Associação** na caixa de ferramentas, em seguida, em um caso de uso e em um ator que participa do caso de uso. Vincule cada ator a seus casos de uso dessa maneira.

5. Estruturar os casos de uso com as relações de **inclusão**, **extensão** e **generalização** . Para criar cada um desses links, clique na ferramenta, em seguida, no caso de uso de origem e, em seguida, no destino. Consulte a seção a seguir intitulada como [estruturar casos de uso](#Structuring).

6. Descreva os casos de uso em mais detalhes. Consulte a seção a seguir intitulada [descrevendo casos de uso em detalhes](#Details).

7. Desenhe diagramas separados para se concentrar em diferentes subsistemas ou em grupos diferentes de casos de uso relacionados. Todos os diagramas em um projeto de modelagem são exibições do mesmo modelo.

## <a name="Actors"></a>Desenhando atores e casos de uso
 A principal finalidade de um diagrama de caso de uso é mostrar quem interage com seu sistema e as metas principais que eles obtêm com ele.

- Crie **atores** para representar classes de pessoas, organizações, outros sistemas, software ou dispositivos que interagem com seu sistema ou subsistema.

  - Para saber como desenhar atores e outros elementos, consulte [Editar diagramas e modelos UML](../modeling/edit-uml-models-and-diagrams.md).

  - Para cada conjunto distinto de metas, identifique os atores por seu tipo ou função, mesmo que as pessoas físicas ou entidades possam ser iguais. Por exemplo, restaurante e Customer são atores separados, embora um funcionário de restaurante, às vezes, pode ser um cliente.

- Crie **casos de uso** para cada um dos objetivos que cada ator busca obter com o sistema.

  - Nomeie e descreva os casos de uso em palavras que o ator entenderia, em vez de termos de implementação.

- Use **associações** para vincular atores a casos de uso.

### <a name="inheritance-between-actors"></a>Herança entre atores
 ![Diagrama de caso de uso mostrando herança](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")

 Você pode desenhar um link de **generalização** entre atores. O ator especializado, como o cliente do clube, no exemplo, herda os casos de uso do ator generalizado, como Customer. A ponta de seta deve apontar para o ator mais geral, como Customer. Ao criar o link, aponte primeiro para o ator mais especializado.

 O ator especializado pode ter seus próprios casos de uso adicionais que não estão disponíveis para os outros atores.

> [!CAUTION]
> Você não deve fazer loops de relações de generalização que resultem em generalizar um ator. Os loops podem gerar erros.

### <a name="alternative-actor-icons"></a>Ícones de ator alternativos
 Você pode usar ícones personalizados para representar um ator, em vez da figura de adesivo padrão. Por exemplo, você pode alterá-lo para se parecer com um dispositivo, restaurante, banco e assim por diante.

##### <a name="to-change-the-appearance-of-an-actor"></a>Para alterar a aparência de um ator

1. Clique com o botão direito do mouse no ator e clique em **Propriedades**.

     A janela **Propriedades** é exibida.

2. Defina a propriedade **caminho da imagem** como o local de um arquivo de imagem.

    - Você pode usar qualquer um dos vários formatos de imagem, incluindo. gif,. jpg e. bmp.

    - Use um arquivo que esteja incluído na solução ou no controle do código-fonte do projeto para que ele ainda esteja disponível quando a solução for movida ou copiada.

3. Para replicar essa aparência em outros diagramas de caso de uso, copie o ator e cole-o em outro diagrama.

    - A alteração da imagem se aplica somente à exibição em um diagrama específico. Ele não se aplica ao elemento de modelo subjacente. Se você arrastar o ator do Gerenciador de modelos UML para outro diagrama, ele será exibido como a figura de adesivo padrão.

### <a name="multiplicities-between-actors-and-use-cases"></a>Multiplicidades entre atores e casos de uso
 A associação entre um ator e um caso de uso pode mostrar uma *multiplicidade* em cada extremidade.

 ![Use o caso de um para um com ator](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")

> [!NOTE]
> As multiplicidades de uma associação em um diagrama de caso de uso serão ocultadas se forem **1**.

 Por padrão, cada multiplicidade é **1**. Em uma interpretação estrita do modelo, uma multiplicidade de 1 significa que, por exemplo, apenas um cliente está envolvido na ordenação de cada refeição e que cada cliente solicita apenas uma refeição por vez.

 Você pode alterar essas multiplicidades.

 Por exemplo:

 ![Caso de uso mostrando a multiplicidade muitos para muitos](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")

- Para declarar que vários atores da mesma classe podem participar em uma única ocorrência de um caso de uso, defina a multiplicidade na extremidade do ator da associação como **1..\*** .

   Na ilustração, um ou mais restaurantes podem fazer parte do cumprimento da mesma ordem de refeição.

- Para mostrar que cada ator pode participar ao mesmo tempo em várias ocorrências de um caso de uso, defina a multiplicidade no final do caso de uso da Associação para **\*** .

   Na ilustração, cada restaurante pode trabalhar para atender a mais de um pedido por vez.

##### <a name="to-set-multiplicities-on-an-association"></a>Para definir multiplicidades em uma associação

1. Clique com o botão direito do mouse na associação e clique em **Propriedades**.

2. Expanda a **primeira função** ou a **segunda função**.

    *Role* significa o elemento em uma extremidade da associação.

3. Defina a propriedade multiplicidade, escolhendo na lista:

   - **1** para declarar que exatamente uma instância dessa função participa de cada link.

   - **1..\*** para declarar que uma ou mais instâncias dessa função participam de cada link.

   - **0.. 1** para indicar que a participação é opcional.

   - **\*** para declarar que zero ou mais instâncias dessa função participam do link.

> [!NOTE]
> Muitas equipes não colocam informações de multiplicidade em diagramas de caso de uso, deixando as multiplicidades com o valor padrão de 1. Em vez disso, eles fornecem as informações em descrições separadas dos casos de uso. Nesse caso, todas as multiplicidades nos diagramas de caso de uso serão ocultas.

### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Usando um ator ou caso de uso em vários diagramas
 Você pode mostrar os mesmos atores e casos de uso em vários diagramas. Por exemplo:

- Você pode descrever em diferentes diagramas os diferentes casos de uso em que um ator está envolvido.

- Você pode usar um diagrama para mostrar os atores e subsistemas com os quais um caso de uso está associado e usar outro diagrama para mostrar como o caso de uso é estruturado em casos de uso incluídos e estendidos.

##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>Para mostrar o mesmo ator ou caso de uso em diagramas diferentes

1. Crie o ator ou o caso de uso em um diagrama.

2. Crie outro diagrama de caso de uso.

3. Arraste um ator ou um caso de uso fora do **Gerenciador de modelos** para o novo diagrama.

    > [!NOTE]
    > Se você posicionar no novo diagrama um ator e um caso de uso que já esteja associado, a associação entre eles será exibida automaticamente no novo diagrama.

## <a name="Details"></a>Descrevendo casos de uso em detalhes
 Um caso de uso representa:

- Uma meta de um ator no uso do sistema, como **comprar um refeição**; e

- Um ou mais *cenários*, ou seja, sequências de etapas executadas na busca da meta, como: {**pedido de refeição, pagamento, entrega**}. Além dos cenários de sucesso, pode haver vários cenários de falha ou exceção, como o **cartão de crédito rejeitado**.

  Um caso de uso pode ser descrito em diferentes níveis de detalhes. Em um estágio inicial do design, apenas o nome no diagrama de caso de uso é suficiente.  Posteriormente, descrições mais detalhadas dos cenários podem ser escritas.

  No Visual Studio Ultimate, você pode descrever um caso de uso de várias maneiras, que pode ser usado separadamente ou em conjunto:

- Vincule o caso de uso a outro diagrama ou Diagram no projeto.

  - Um diagrama de atividade ajuda a explicar um processo mais complexo em que há loops, branches e threads paralelos. Ele também pode mostrar o fluxo de dados entre partes do processo. Para obter mais informações, consulte [diagramas de atividade UML: diretrizes](../modeling/uml-activity-diagrams-guidelines.md).

  - Um diagrama de sequência ajuda a explicar uma série complexa de interações entre atores diferentes. Você também pode usá-lo para mostrar o que acontece dentro do sistema em resposta a cada caso de uso. Para obter mais informações, consulte [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md).

- Vincule o caso de uso a uma página, seção ou parágrafo do OneNote que descreve o caso de uso em detalhes.

- Vincule o caso de uso a um documento do Word, no qual você usa texto, capturas de tela e assim por diante para descrever os cenários de caso de uso. Para obter mais informações, consulte [requisitos de usuário de modelo](../modeling/model-user-requirements.md).

#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Para vincular um caso de uso a um diagrama ou arquivo na mesma solução

1. Desenhe um diagrama, como um diagrama de sequência ou um diagrama de atividade, para ilustrar um cenário do caso de uso.

2. Volte para o diagrama de caso de uso.

3. Arraste o diagrama ou o arquivo de Gerenciador de Soluções para uma parte em branco do diagrama de caso de uso.

4. Conecte-se do artefato ao caso de uso usando uma **dependência**.

#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Para vincular a um arquivo de solução, como um documento do Word ou apresentação do PowerPoint

1. Escreva um documento que use texto, capturas de tela e assim por diante para descrever o cenário do caso de uso.

2. Adicione o documento à solução.

    1. Mova o documento do Word para a mesma pasta do Windows que a solução.

    2. Em Gerenciador de Soluções, clique com o botão direito do mouse na solução, aponte para **Adicionar**e clique em **Item existente**.

    3. Navegue até o documento do Word e clique em **Adicionar**.

         O documento do Word aparece em uma pasta de solução no Gerenciador de Soluções.

3. Arraste o documento do Word de Gerenciador de Soluções para uma parte em branco do diagrama de caso de uso.

     Um novo artefato é exibido.

4. Conecte-se do artefato ao caso de uso usando uma **dependência**.

#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Para vincular a um documento compartilhado, elemento do OneNote ou página da Web

1. Obtenha a URL do elemento compartilhado. Isso pode ser, por exemplo, um caminho de arquivo de rede que começa com '\\\\' ou uma página da Web ou URL do SharePoint começando com ' http://' ou um link para uma seção, página ou parágrafo do OneNote que comece ' OneNote: '.

2. Na caixa de ferramentas, clique em **artefato** e, em seguida, clique no diagrama de caso de uso.

3. Com o novo artefato selecionado, digite ou cole a URL na propriedade **Hyperlink** .

> [!NOTE]
> Você pode clicar duas vezes em um artefato para abrir o diagrama ou documento ao qual ele se vincula.

### <a name="linking-use-cases-to-work-items"></a>Vinculando casos de uso a itens de trabalho
 Se o seu projeto usa [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] e você tem [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], você pode vincular cada caso de uso a um item de trabalho no [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Para saber como fazer esses links, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).

 Isso permite que você:

- Descreva o caso de uso no item de trabalho vinculado. Em particular, se o seu projeto usar o modelo de processo formal do Visual Studio, você poderá vincular a um item de trabalho de caso de uso. Este tipo de item de trabalho fornece campos para descrever as metas e os cenários do caso de uso.

- Vincule casos de teste ao caso de uso para que você possa obter relatórios sobre a distância com que o código que está sendo desenvolvido implementa o caso de uso.

- Vincule tarefas ao caso de uso para que você possa acompanhar o progresso do trabalho de desenvolvimento.

## <a name="Structuring"></a>Estruturando casos de uso
 Você deve tentar descrever o comportamento do sistema com apenas alguns casos de uso principais. Cada caso de uso grande define uma meta principal que um ator alcança, como comprar um produto ou, do ponto de vista do fornecedor, fornecendo produtos para venda.

 Depois de tornar essas metas claras, você pode entrar em mais detalhes sobre como cada meta é alcançada e sobre variações nas metas básicas.

 Evite decompor os casos de uso em muito detalhes. Os casos de uso são sobre a experiência dos usuários do seu sistema, em vez de seus trabalhos internos. Além disso, em geral, você achará mais produtivo criar versões de trabalho antecipadas do código, em vez de gastar tempo delimitando casos de uso em detalhes.

 Você pode resumir em um diagrama de caso de uso as relações entre os casos de uso principal e mais detalhado. As seções a seguir descrevem isso:

- [Mostrando os detalhes de um caso de uso com include](#Include)

- [Compartilhando metas com generalização](#Inheritance)

- [Separando casos variantes com extend](#Extend)

### <a name="Include"></a>Mostrando os detalhes de um caso de uso com include
 Use uma relação de **inclusão** para mostrar que um caso de uso descreve alguns dos detalhes de outro. Na ilustração, **pedido uma refeição** inclui **pagamento**, **escolha menu**e **escolha item de menu**. Cada um dos casos de uso incluídos e mais detalhados é uma etapa que o ator ou os atores podem ter que realizar para atingir o objetivo geral do caso de uso, incluindo o caso. A seta deve apontar para o caso de uso mais detalhado, incluído.

> [!CAUTION]
> Você não deve fazer loops de incluir relações que resultem em um caso de uso, incluindo a si mesma. Os loops podem gerar erros.

 Você pode compartilhar casos de uso incluídos. No exemplo, a **ordem uma refeição** e **a assinatura para revisar casos de** uso incluem **Pay**.

 ![Casos de uso decomposto com include](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")

 A meta e os cenários de um caso de uso incluído devem fazer sentido independentemente para que possam ser incluídos em casos de uso criados posteriormente.

 Separar casos de uso em partes de inclusão e incluídas é útil para atingir os seguintes objetivos:

- Estruture suas descrições de caso de uso em diferentes camadas de detalhes.

- Evite repetir cenários compartilhados em diferentes casos de uso.

#### <a name="Steps"></a>Definindo a ordem das etapas detalhadas
 O diagrama de caso de uso não diz nada sobre a ordem na qual as etapas mais detalhadas devem ser executadas, nem sobre se cada uma delas é sempre necessária.

 Para tornar a ordem das etapas clara, você pode usar um **artefato** para anexar um documento separado ao, incluindo o caso de uso. No exemplo a seguir, um diagrama de atividade anexado ao caso de uso pedido de refeição. Como alternativa, você pode usar um documento de texto que tenha uma lista de etapas ou uma sequência de capturas de tela. Para obter mais informações, consulte [descrevendo casos de uso em detalhes](#Details).

 Observe essas convenções de nomenclatura ao usar um diagrama de atividade:

- O nome da atividade inteira é o mesmo que a inclusão do caso de uso.

- As ações no diagrama de atividade têm os mesmos nomes dos casos de uso incluídos.

  Para obter mais informações, consulte [diagramas de atividade UML: diretrizes](../modeling/uml-activity-diagrams-guidelines.md).

  ![Etapas de caso de uso mostradas no diagrama de atividades vinculadas](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")

### <a name="Inheritance"></a>Compartilhando metas com generalização
 Use uma relação de generalização para mostrar que um caso de uso *especializado* é uma maneira específica de atingir as metas expressas por outro caso de uso *geral* . A ponta de seta aberta deve apontar para o caso de uso mais geral.

 ![Casos de uso que mostram a relação de generalização](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")

 Por exemplo, **pague** generaliza o **pagamento por cartão de crédito** e **pague por dinheiro**.

> [!CAUTION]
> Você não deve fazer loops de relações de generalização, que resultam em um ator generalizando-se. Os loops podem gerar erros.

 Casos de uso especializados podem ajudá-lo a mostrar maneiras diferentes de que seu sistema pode atingir o mesmo objetivo.

 Os casos de uso especializados são considerados para herdar as metas e os atores do caso de uso geral. O caso de uso geral não precisa ter cenários próprios; suas especializações descrevem diferentes maneiras de atingir as metas.

##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>Para refatorar as metas comuns de dois ou mais casos de uso

1. Crie e nomeie o novo caso de uso geral.

2. Crie uma relação de **generalização** com a seta grande apontando para o novo caso de uso geral.

    1. Clique em **generalização** na caixa de ferramentas.

    2. Clique em um caso de uso especializado (**pagar por cartão de crédito** no exemplo).

    3. Clique no caso de uso geral (**pagar** no exemplo).

3. Se você tiver descrito as metas para os casos de uso especializados, mova as partes comuns para a descrição do caso de uso geral.

4. Os atores compartilhados entre os casos de uso especializados podem ser movidos para o caso de uso geral.

### <a name="Extend"></a>Separando casos variantes com extend
 Use um link de extensão para mostrar que um caso de uso pode adicionar funcionalidade a outro caso de uso em determinadas circunstâncias. A seta deve apontar para o caso de uso principal e estendido.

 ![Um caso de uso que estende outra](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")

> [!CAUTION]
> Você não deve fazer loops de Extend Relationships, que resultam em um ator generalizando-se. Os loops podem gerar erros.

 Por exemplo, o caso de uso de **logon** de um site típico pode incluir **registrar novo usuário** -mas somente quando o usuário ainda não tiver uma conta.

##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>Para separar um caso de uso em partes principal e estendida

1. Crie e nomeie o caso de uso da nova extensão.

2. Crie uma relação de **extensão** com a seta apontando no caso de uso estendido.

   1. Clique em **estender** na caixa de ferramentas.

   2. Clique no caso de uso de extensão (**registrar novo usuário** no exemplo).

   3. Clique no caso de uso estendido (**logon** no exemplo).

       > [!NOTE]
       > Evite criar um loop de estender relações no diagrama. Está incorreto para um caso de uso ser uma extensão de si mesmo.

3. Se você já tiver criado cenários para o caso de uso estendido, mova as etapas relevantes para o cenário da extensão.

4. A descrição da extensão (**registrar novo usuário** no exemplo) deve incluir detalhes de onde nos cenários de caso de uso principal ele ocorrerá e em quais circunstâncias. Imagine-o como modificar a descrição do caso principal.

   O caso de uso da extensão representa as etapas do cenário que, caso contrário, seriam parte dos cenários do caso de uso principal. O cenário e a meta da extensão serão sempre lidos no contexto do caso de uso principal, portanto, eles não precisam ser úteis independentemente.

   Separar extensões pode ser útil para descrever essas situações:

- Há atores adicionais envolvidos apenas no caso de uso de extensão. Por exemplo, um administrador é necessário para aprovar o registro de um cliente no site.

- Um subsistema separado tratará do caso de uso de extensão.

- Essa extensão estará disponível somente em versões específicas do sistema. Você pode mostrar cada versão como um subsistema separado no diagrama de caso de uso.

## <a name="Subsystems"></a>Usando limites de subsistema
 Use um limite de subsistema para mostrar quais casos de uso estão dentro do escopo do seu sistema.

#### <a name="to-draw-a-subsystem-boundary"></a>Para desenhar um limite de subsistema

1. Na caixa de ferramentas, clique em **subsistema**e, em seguida, clique no diagrama.

    Um subsistema é exibido no diagrama.

2. Arraste os cantos do subsistema para ajustar seu tamanho.

3. Arraste os casos de uso existentes para dentro ou para fora do subsistema para ajustar seu conteúdo.

   \- ou -

   Para criar um novo caso de uso diretamente em um subsistema, clique em **caso de uso** na caixa de ferramentas e clique dentro do subsistema.

> [!NOTE]
> A propriedade **Subjects** de um caso de uso indica em qual subsistema ele está contido.

### <a name="use-cases-outside-the-system-scope"></a>Casos de uso fora do escopo do sistema
 Geralmente, é útil incluir nos casos de uso de diagrama que fazem parte do negócio, mas que não são tratados pelo sistema que você está desenvolvendo. Isso ajuda os desenvolvedores a entender o contexto de seu trabalho. Por exemplo, a entrega de uma refeição pode ser mostrada como um caso de uso envolvendo os atores restaurante e Customer, mas fora da responsabilidade do site de pedidos de refeições.

### <a name="multiple-subsystems"></a>Vários subsistemas
 Você pode criar vários limites de subsistemas para mostrar como casos de uso diferentes são tratados por diferentes componentes do sistema. Por exemplo, **Adicionar a avaliação de restaurante** pode ser tratada em um site de fórum separado. Lembre-se de que um diagrama de caso de uso deve lidar com o que é visível para o usuário. Se você quiser descrever a divisão interna do trabalho no sistema, considere usar um diagrama de componente.

### <a name="system-versions"></a>Versões do sistema
 Você pode usar limites de subsistema diferentes para ilustrar versões diferentes do sistema. Por exemplo, o caso de uso de pagamento pode ser incluído na versão 2 do site, mas não na versão 1. isso implica que o sistema ajuda os clientes a fazer seus pedidos. No entanto, eles precisam pagar o restaurante diretamente.

 Use relações de **dependência** para vincular subsistemas que representam diferentes versões ou variantes.

 ![Os subsistemas mostram versões diferentes de um sistema](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")

## <a name="see-also"></a>Consulte também
 [Modelos de usuário de modelo](../modeling/model-user-requirements.md) [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md) [editar modelos UML e diagramas diagramas de](../modeling/edit-uml-models-and-diagrams.md) [caso de uso UML: referenciar](../modeling/uml-use-case-diagrams-reference.md) [diagramas de classes UML: referenciar](../modeling/uml-class-diagrams-reference.md) [diagramas de componentes UML:](../modeling/uml-component-diagrams-reference.md) referência [diagramas de atividade UML: diretrizes](../modeling/uml-activity-diagrams-guidelines.md) [vídeo: organizando recursos em casos](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases)
