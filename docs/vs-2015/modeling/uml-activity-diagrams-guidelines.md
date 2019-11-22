---
title: 'Diagramas de atividade UML: diretrizes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 692859008891439e4af3d751306bfd3ee6d351e8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298992"
---
# <a name="uml-activity-diagrams-guidelines"></a>Diagramas de atividade UML: diretrizes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No Visual Studio, você pode desenhar um diagrama de atividade para descrever um processo de negócios ou um algoritmo de software como um fluxo de trabalho por meio de uma série de ações. Pessoas, componentes de software ou dispositivos podem executar essas ações. Para ver uma demonstração em vídeo, consulte: [capturar fluxos de trabalho de negócios usando diagramas de atividade](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows).

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Para criar um diagrama de atividade UML, no menu **arquitetura** , clique em **novo UML ou diagrama de camada**.

 Você pode usar um diagrama de atividade para muitos propósitos:

- Descrever um processo de negócios ou um fluxo de trabalho entre usuários e seu sistema. Para obter mais informações, consulte [requisitos de usuário de modelo](../modeling/model-user-requirements.md).

- Para descrever as etapas executadas em um caso de uso. Para obter mais informações, consulte [diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md).

- Para descrever um método, uma função ou uma operação no software. Para obter mais informações, consulte [modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md).

  Desenhar um diagrama de atividade pode ajudá-lo a melhorar um processo. Se o diagrama de um processo existente comprova ser muito complexo, você pode considerar como o processo poderia ser simplificado.

  Para obter informações de referência sobre os elementos em diagramas de atividade, consulte [diagramas de atividade UML: referência](../modeling/uml-activity-diagrams-reference.md).

## <a name="Relationships"></a>Relação com outros diagramas
 Se você desenhar um diagrama de atividade para descrever um processo comercial ou uma maneira na qual os usuários usam o sistema, poderá desenhar um diagrama de caso de uso para mostrar uma exibição diferente das mesmas informações. No diagrama de caso de uso, você desenha ações como casos de uso. Dê ao caso de uso os mesmos nomes das ações correspondentes. As vantagens do modo de exibição de caso de uso são que você pode:

- Mostrar em um diagrama o quão maiores ações/casos de uso são compostos de menores, usando a relação de inclusão.

- Conecte cada caso de ação/uso explicitamente aos usuários ou sistemas externos envolvidos em sua execução.

- Desenhe limites em relação às ações/casos de uso com suporte no seu sistema ou a cada componente principal dele.

  Você também pode desenhar um diagrama de atividade para descrever o design detalhado de uma operação de software.

  Em um diagrama de atividade, você pode mostrar o fluxo de dados passado entre as ações. Consulte a seção sobre como [descrever o fluxo de dados](#DataFlows). Mas um diagrama de atividade não descreve a estrutura dos dados. Para essa finalidade, você pode desenhar um diagrama de classes UML. Para obter informações, consulte [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Etapas básicas para desenhar diagramas de atividade
 As etapas detalhadas para a criação de qualquer um dos diagramas de modelagem são descritas em [editar modelos e diagramas UML](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-draw-an-activity-diagram"></a>Para desenhar um diagrama de atividade

1. No menu **arquitetura** , clique em **novo UML ou diagrama de camada**.

2. Em **modelos**, clique em **diagrama de atividade UML**.

3. Nomeie o diagrama.

4. Em **Adicionar ao projeto de modelagem**, selecione um projeto de modelagem existente em sua solução ou **crie um novo projeto de modelagem**.

#### <a name="to-draw-elements-on-an-activity-diagram"></a>Para desenhar elementos em um diagrama de atividade

1. Arraste elementos da caixa de ferramentas para o diagrama.

     Comece colocando as principais atividades no diagrama, conectando-as e, em seguida, adicionando os toques finais, como os nós inicial e final.

    > [!NOTE]
    > Não é possível arrastar elementos existentes para o diagrama do Gerenciador de modelos UML.

2. Para conectar os elementos, siga estas etapas:

    1. Na caixa de ferramentas **diagrama de atividade** , clique em **conector**.

    2. No diagrama, clique no elemento Source.

    3. Clique no elemento de destino.

        > [!NOTE]
        > Para usar uma ferramenta várias vezes, clique duas vezes na ferramenta na caixa de ferramentas.

#### <a name="to-move-an-activity-to-another-package"></a>Para mover uma atividade para outro pacote

- No **Gerenciador de modelos UML**, arraste a atividade para um pacote.

     \- ou -

- No **Gerenciador de modelos UML**, clique com o botão direito do mouse na atividade e clique em **recortar**. Em seguida, clique com o botão direito do mouse no pacote e clique em **colar**.

    > [!NOTE]
    > A atividade será exibida no Gerenciador de modelos UML somente quando você adicionar o primeiro elemento ao diagrama.

## <a name="SimpleControlFlow"></a>Descrevendo o fluxo de controle
 Um diagrama de atividade descreve um processo de negócios ou um algoritmo de software como uma série de ações. As setas do conector mostram como o controle é passado sequencialmente de uma ação para a próxima. Normalmente, uma ação pode ser iniciada somente após a conclusão da ação anterior.

 A figura a seguir é um exemplo de como você pode mostrar uma sequência de ações com ações, conectores, branches e loops. Cada elemento é explicado com mais detalhes nas seções a seguir.

 ![Um diagrama de atividade simples](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")

 Os diagramas de atividade usam **ações** e **conectores** para descrever seu sistema ou aplicativo como uma série de ações com o controle que flui sequencialmente de uma ação para a próxima.

- Crie uma **ação** (1) para cada tarefa principal executada por um usuário, o sistema ou ambos em colaboração.

  > [!NOTE]
  > Tente descrever seu processo ou algoritmo com apenas algumas ações. Você pode usar **ações de comportamento de chamada** para definir cada ação mais detalhadamente em um diagrama separado, conforme descrito em [descrevendo subatividades com ações de comportamento de chamada](#Subactivities).

- Certifique-se de que o título de cada ação indica claramente o que normalmente é obtido.

- Vincule as ações em sequência com **conectores** (2).

- Cada ação termina antes do início da próxima ação no fluxo de controle. Se você quiser descrever as ações sobrepostas, use um **nó de bifurcação** , conforme descrito na seção [fluxos simultâneos](#Concurrent).

  Embora o diagrama descreva a sequência de ações, ele não descreve como as ações são executadas ou como o controle é passado de uma ação para a próxima. Se você usar o diagrama para representar um processo de negócios, o controle poderá ser passado, por exemplo, quando uma pessoa enviar uma mensagem de email para outra. Se você usar o diagrama para representar um design de software, o controle poderá ser passado pelo fluxo normal de execução de uma instrução para a próxima.

### <a name="describing-decisions-and-loops"></a>Descrevendo decisões e loops

- Use um **nó de decisão** (3) para indicar um ponto em que o resultado de uma decisão determina a próxima etapa. Você pode desenhar Quantos caminhos de saída desejar.

- Se você usar o diagrama de atividade para definir parte de um aplicativo, deverá definir as proteções (4) para que fique claro quando cada caminho deve ser obtido. Clique com o botão direito do mouse no conector, clique em **Propriedades**e, na janela **Propriedades** , digite um valor para o campo de **proteção** .

- Nem sempre é necessário definir as proteções. Por exemplo, se você usar o diagrama de atividade para descrever um processo de negócios ou um protocolo de interação, uma ramificação definirá o intervalo de opções abertas para o usuário ou para os componentes interagindo.

- Use um **nó de mesclagem** (5) para reunir dois ou mais fluxos alternativos que são ramificados em um **nó de decisão**.

    > [!NOTE]
    > Você deve usar um **nó de mesclagem** para reunir fluxos alternativos, em vez de colocar os fluxos juntos em uma ação. No exemplo, ele não estaria correto para se conectar do nó de decisão diretamente de volta para **escolher item de menu**. Isso ocorre porque uma ação não é iniciada até que threads de controle tenham chegado a todos os seus conectores de entrada. Portanto, você deve colocar apenas fluxos simultâneos em uma ação. Para obter mais informações, consulte [fluxos simultâneos](#Concurrent).

- Use branches para descrever loops, conforme mostrado no exemplo.

    > [!NOTE]
    > Tente aninhar loops de forma bem estruturada, como você faria no código do programa. Se você estiver descrevendo um processo de negócios existente, isso poderá revelar algumas oportunidades para melhorá-lo.

### <a name="starting-the-activity"></a>Iniciando a atividade
 Há duas maneiras de indicar pontos de entrada em uma atividade:

- **Nó inicial**

     Crie um **nó inicial** (6) para indicar a primeira ação da atividade.

     Esse método é mais útil quando você está descrevendo uma subatividade, ou onde você não precisa declarar explicitamente o que inicia a atividade. Por exemplo, a ordem da atividade de uma refeição é claramente iniciada quando um cliente fica mais à sua.

- **Aceitar nó de evento**

     Crie **nós de evento Accept**, conforme descrito na seção [fluxos simultâneos](#Concurrent), para indicar o início de um thread que responde a um evento específico, como uma entrada do usuário. Não forneça um fluxo de entrada para o nó. Omitir um fluxo de entrada indica que um thread será iniciado toda vez que o evento ocorrer.

     Esse método é mais útil quando você descreve uma resposta a um evento externo específico.

### <a name="ending-the-activity"></a>Finalizando a atividade
 Use um **nó final da atividade** (7) para indicar o final de uma atividade.

- Quando um thread de controle atinge um **nó final da atividade**, todas as ações e subatividades simultâneas da atividade são encerradas.

- Você pode usar mais de um nó final da atividade para reduzir a confusão de conectores adicionais.

### <a name="interrupting-the-activity"></a>Interrompendo a atividade
 Para descrever como o fluxo comum de uma atividade pode ser interrompido, por exemplo, se o usuário decidir cancelar o processo, você poderá criar um nó de evento Accept que escuta esse evento. Para obter mais informações, consulte a seção [fluxos simultâneos](#Concurrent). Crie um fluxo de controle do para um nó final da atividade (7).

### <a name="swimlanes"></a>Raias
 Às vezes, é útil organizar as ações de uma atividade em áreas correspondentes a diferentes objetos ou funções de negócios que executam as ações. Essas áreas são organizadas de maneira convencional em colunas e são chamadas de *raias*.

- Use linhas ou retângulos da seção **formas simples** da caixa de ferramentas para desenhar raias ou outras áreas.

- Para rotular cada raia, crie um comentário e defina sua propriedade **Transparent** como **true**.

  Formas simples não formam parte do modelo UML e não aparecem no Gerenciador de modelos UML.

## <a name="DataFlows"></a>Descrevendo o fluxo de dados
 Você pode descrever os dados que passam e saem de uma atividade de uma das duas maneiras:

- Use um **nó de objeto**. Esse é o método mais simples de descrever as informações que fluem entre as atividades. Um nó de objeto é como uma variável em um programa. Ele representa algo que armazena um ou mais valores que estão passando de uma ação para outra.

- Use um **PIN de saída** e um **PIN de entrada**. Esse método permite que você descreva separadamente as saídas de uma ação e as entradas para outra. Os Pins são como parâmetros em um programa. Os Pins representam as portas em que os objetos podem entrar e sair de uma ação.

    > [!NOTE]
    > Para obter uma visão geral dos elementos usados nesta seção, consulte a seção fluxos de dados do tópico ver [diagramas de atividade UML: referência](../modeling/uml-activity-diagrams-reference.md).

### <a name="describing-data-flow-with-object-nodes"></a>Descrevendo o fluxo de dados com nós de objeto
 A maioria dos fluxos de controle transporta dados. Por exemplo, o fluxo de saída da ação "o cliente fornece detalhes" transporta uma referência para o endereço de envio.

 Se você quiser descrever os dados em seu diagrama, poderá substituir um conector por um nó de objeto e dois conectores, conforme mostrado na figura a seguir.

 ![Os nós de objeto podem mostrar os dados passados entre as ações](../modeling/media/uml-actguidedata.png "UML_ActGuideData")

 Observe que os retângulos com cantos arredondados, como mercadorias de expedição, representam ações em que o processamento ocorre. Os retângulos com cantos quadrados, como endereço de remessa, representam um fluxo de objetos de uma ação para outra.

 Dê ao nó do objeto um nome que reflita a função do nó como um canal ou buffer dos objetos que fluem entre as ações.

 Você pode definir o **tipo** do nó de objeto no janela Propriedades. O tipo pode ser um tipo primitivo como inteiro ou uma classe, interface ou enumeração que você definiu em um diagrama de classe. Por exemplo, você pode criar um endereço de remessa de classe, com atributos de endereço, cidade e assim por diante, junto com uma associação a outra classe chamada Customer. Para obter mais informações, consulte [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md).

> [!NOTE]
> Se você digitar o nome de um tipo que ainda não foi definido, um item será adicionado sob tipos não **especificados** no Gerenciador de modelos UML. Se, posteriormente, você definir um tipo desse nome em um diagrama de classe, deverá redefinir o tipo do nó de objeto para que ele se refira ao novo tipo.

#### <a name="buffering-data-in-object-nodes"></a>Armazenando dados em buffer em nós de objeto
 Um nó de objeto pode atuar como um buffer para vários objetos. Na ilustração a seguir, o fluxo de controle mostra que o usuário pode percorrer o loop [escolher mais] (1) muitas vezes, enquanto o nó de objeto itens de menu escolhido (2) acumula as opções do usuário. Por fim, quando o usuário tiver concluído sua seleção, o controle passará para a ação confirmar pedido (3), que aceita a lista completa de opções do buffer de itens de menu escolhido.

 ![Armazenando dados em buffer em nós de objeto](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")

 Você pode especificar como os itens em um buffer são armazenados definindo as propriedades do nó do objeto:

- Defina a propriedade de **ordenação** :

  - Não **ordenado** para especificar uma ordem aleatória ou não especificada. (Padrão.)

  - **Ordenado** para especificar um pedido de acordo com uma chave específica.

  - **PEPS** para especificar uma ordem de primeiro a entrar, primeiro a sair.

  - **UEPS** para especificar uma ordem de último a entrar, primeiro a sair.

- Defina a propriedade **limite superior** para especificar o número máximo de objetos que podem estar contidos no buffer. O padrão é *. Isso significa que não há nenhum limite.

### <a name="describing-data-flow-with-input-and-output-pins"></a>Descrevendo o fluxo de dados com Pins de entrada e saída
 Use um **pino de saída** e um **PIN de entrada** para descrever separadamente as saídas de uma ação e as entradas para outra.

 ![Os Pins de entrada e saída são parâmetros de ação](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")

 Para criar um PIN, clique em **pino de entrada** ou pino de **saída** na caixa de ferramentas e clique em uma ação. Em seguida, você pode mover o PIN em todo o perímetro da ação e alterar seu nome. Você pode criar Pins de entrada e saída em qualquer tipo de ação, incluindo **ações de comportamento de chamada**, ações de operação de **chamada**, ações de sinal de **envio**e ações de **evento de aceitação**.

 Um conector entre dois Pins representa um fluxo de objeto, assim como os fluxos de e para um nó de objeto.

 Dê um nome a cada PIN que indique a função dos objetos que ele produz ou aceita, como um nome de parâmetro.

 Você pode definir o tipo de objetos transmitidos na propriedade **Type** . Ele deve ser um tipo que você criou em um diagrama de classes UML.

 Os objetos que fluem entre os Pins conectados devem ser compatíveis de alguma maneira. Isso pode ocorrer porque os objetos produzidos pelo pino de saída pertencem a um tipo derivado do tipo do pino de entrada.

 Como alternativa, você pode especificar que o fluxo de objeto inclua uma transformação que converte dados entre o tipo do pino de saída e o tipo do PIN de entrada. A transformação mais comum desse tipo apenas extrai a parte apropriada de um tipo maior. O exemplo na figura implica a existência de uma transformação que extrai o endereço de envio dos detalhes do pedido.

## <a name="Details"></a>Definindo uma ação com mais detalhes
 Além de usar o nome da ação para tornar claro o resultado que ela normalmente deve atingir, aqui estão algumas maneiras de adicionar mais detalhes a uma ação:

- Escreva uma descrição mais detalhada na propriedade **Body** . Por exemplo, você poderia escrever um fragmento de código do programa ou pseudo-código ou uma descrição completa dos resultados obtidos.

- Substitua a ação por uma ação de comportamento de chamada e descreva seu comportamento detalhado em um diagrama de atividade separado. Consulte [descrevendo subatividades com ações de comportamento de chamada](#Subactivities).

- Defina as propriedades de **condição local** e as condições **de pré-condições locais** da ação para descrever seu resultado em detalhes mais específicos. Para obter mais informações, consulte [definindo condições e pré-condições](#Postcondition).

### <a name="Subactivities"></a>Descrevendo subatividades com ações de comportamento de chamada
 Você pode descrever o comportamento detalhado de uma ação usando um diagrama de atividade separado. Um comportamento chamado é um diagrama de atividade que é representado em seu diagrama de atividade principal por uma ação de comportamento de chamada. Você também pode usar a ação chamar comportamento para descrever o comportamento compartilhado entre diferentes atividades para que você não precise desenhar a subatividade várias vezes.

 Na figura a seguir, o diagrama 1 mostra uma atividade que tem uma ação de comportamento de chamada e o diagrama 2 mostra o diagrama de subatividade que mostra o comportamento chamado.

 ![Um diagrama de atividade separado mostra ações detalhadas](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")

##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>Para descrever uma subatividade com uma ação de comportamento de chamada

1. Para criar o diagrama para a subatividade, em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto de modelagem, aponte para **Adicionar**e clique em **novo item**.

2. Na caixa de diálogo **Adicionar novo item** , em **modelos** , clique em **diagrama de atividade** e na caixa **nome** , digite o nome que você planeja para dar sua ação de **comportamento de chamada**.

3. Desenhe o fluxo de trabalho detalhado para a subatividade. Esse é o comportamento chamado.

    - No diagrama de subatividade chamado, o **nó inicial** indica onde o controle é iniciado quando o comportamento chamado é invocado. O **nó final da atividade** mostra onde o controle deve retornar à atividade pai.

4. Defina a propriedade **Behavior** da **ação de comportamento da chamada** para fazer referência ao diagrama de comportamento chamado.

    > [!NOTE]
    > O diagrama de subatividade deve ter alguns elementos ou o diagrama não estará disponível na lista suspensa para a propriedade de **comportamento** . Além disso, o ícone Trident não será exibido na forma de **ação de comportamento de chamada** até que você defina sua propriedade de **comportamento** .

5. Defina a propriedade **é síncrona** da ação para indicar se sua atividade aguarda a conclusão da atividade chamada.

    - Se você definir **é síncrono** como falso, você está indicando que o fluxo pode continuar para a próxima ação antes de a atividade chamada ser concluída. Você não deve definir os Pins de saída ou os fluxos de dados enviados da ação.

### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Descrevendo o fluxo de dados dentro e fora das subatividades
 Você pode descrever os dados que entram e saem de subatividades, da mesma maneira que usa parâmetros no software.

- Crie Pins de entrada e saída (1) na ação de comportamento chamada, para cada parte dos dados que flui para dentro ou para fora da ação. Nomeie cada uma delas adequadamente.

- No diagrama de subatividade, crie um **nó de parâmetro de atividade** (2) para cada PIN de entrada e saída na ação de chamada. Dê a cada nó o mesmo nome do PIN correspondente.

  > [!NOTE]
  > Um nó de parâmetro de atividade é semelhante a um nó de objeto. Para verificar o tipo de nó que você está vendo, clique com o botão direito do mouse no nó e clique em **Propriedades**. O tipo de nó é mostrado no cabeçalho da janela Propriedades.

- No diagrama de subatividade, desenhe conectores que mostram o fluxo de objetos para dentro ou fora de cada nó de parâmetro de atividade.

  ![Os Pins no comportamento de chamada mapeiam para parâmetros de atividade](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")

### <a name="Postcondition"></a>Definindo condições e pré-condições
 Você pode usar as propriedades de **condição** local e as pré-condições **locais** para especificar em detalhes o resultado de uma ação. Essas propriedades descrevem o efeito da ação sem descrever como o efeito é atingido.

 Para definir essas propriedades, clique com o botão direito do mouse na ação e clique em **Propriedades**. Digite valores nas propriedades na janela Propriedades.

#### <a name="local-postconditions"></a>Condições locais
 Uma pré-condição é uma condição que deve ser satisfeita antes que a ação possa ser considerada concluída. No exemplo de ordem de confirmação de ação, a condição de exclusão pode ser:

 O cliente forneceu detalhes completos e válidos que são necessários para processar seu cartão de crédito.

 Uma condição de espera pode expressar uma relação entre os Estados antes e depois da ação. Por exemplo:

 A taxa de juros é o dobro do que era antes.

 Você pode escrever condições em um estilo mais formal, referindo-se a atributos específicos dos dados tratados com o nas ações. Por exemplo:

 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`

#### <a name="local-preconditions"></a>Pré-condições locais
 Uma pré-condição é uma condição que deve ser verdadeira quando a ação estiver pronta para começar. Por exemplo, a ação confirmar ordem pode ter a pré-condição:

 O cliente escolheu pelo menos um item do menu.

### <a name="describing-calls-to-operations"></a>Descrevendo chamadas para operações
 Geralmente, uma ação descreve o trabalho que é executado por qualquer combinação de pessoas, software ou computadores. Mas você pode usar uma ação chamar operação para descrever uma chamada para um método ou função de software específico.

- Defina o nome da ação de operação de chamada para indicar qual operação é chamada e em qual objeto ou componente.

- Adicione Pins de entrada e saída à ação chamar operação para descrever os parâmetros e valores de retorno.

- Você pode definir a propriedade **síncrona is** da ação para indicar se sua atividade aguarda a conclusão da operação.

  - Se você definir **é síncrono** como falso, você está indicando que o fluxo pode continuar para a próxima ação antes que a operação chamada seja concluída. Você não deve definir os Pins de saída ou os fluxos de dados enviados da ação.

## <a name="Concurrent"></a>Fluxos simultâneos
 Você pode usar o **nó Fork** e o **nó Join** para descrever dois ou mais threads de atividades que podem ser executados ao mesmo tempo.

 ![Os nós de bifurcação e junção mostram fluxos simultâneos](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")

 O efeito do **nó de bifurcação** (1) é dividir o thread de controle em dois ou mais threads. Quando a ação anterior terminar, todas as ações no lado de saída da bifurcação poderão ser iniciadas.

 Um **nó de junção** (2) traz threads simultâneos juntos. A ação após o **nó de junção** pode não ser iniciada até que todas as ações que levam ao **nó de junção** sejam concluídas.

### <a name="describing-signals-and-events"></a>Descrevendo sinais e eventos
 Você pode mostrar uma etapa em um processo que envia um sinal como uma ação de sinal de envio em uma atividade. Você pode mostrar uma etapa que aguarda um sinal ou evento específico antes que a etapa possa continuar como uma ação de evento Accept.

 Por exemplo, você pode mostrar uma etapa que envia uma ordem e, em seguida, outra etapa que deve receber a ordem antes de processar essa ordem.

#### <a name="sending-a-signal"></a>Enviando um sinal
 Use uma ação de sinal de envio (3) para indicar que um sinal ou mensagem de algum tipo é enviado para outras atividades ou processos. Use o nome da ação para indicar que tipo de mensagem ele envia.

- O controle passa imediatamente para a próxima ação no fluxo de controle, se houver um.

- Você não pode usar uma ação enviar sinal para descrever como seu processo responde a qualquer informação retornada. Para fazer isso, use uma ação de evento Accept separada.

- Você pode mostrar o fluxo de dados de entrada para uma ação de sinal de envio, para indicar quais dados podem ser enviados com a mensagem de saída. Para obter mais informações, consulte [descrevendo o fluxo de dados](#DataFlows).

#### <a name="waiting-for-a-signal-or-event"></a>Aguardando um sinal ou evento
 Use uma ação de evento Accept (4) para indicar que essa atividade aguarda algum evento externo ou mensagem de entrada. Use o nome da ação para indicar o tipo de evento que ele espera.

- Para mostrar que sua atividade aguarda um evento ou uma mensagem externa em um ponto específico em seu fluxo, desenhe uma ação de evento Accept com um fluxo de entrada, no local apropriado da atividade.

- Para mostrar que sua atividade pode responder a um evento ou mensagem externa a qualquer momento, desenhe uma ação de evento Accept sem nenhum fluxo de entrada. Quando o evento externo nomeado ocorrer, um novo thread começará em sua atividade, a partir da ação de evento Accept.

- Você não pode usar uma ação de evento Accept para descrever qualquer valor retornado ao remetente do sinal. Use uma ação de sinal de envio separada para essa finalidade.

- Você pode mostrar fluxos de dados de saída da ação, para mostrar como sua atividade processa os dados que são recebidos no sinal. Se você quiser mostrar mais de um fluxo de saída, defina a propriedade **IsUnmarshall** da ação de evento Accept, que indica que a ação analisa o sinal de entrada em seus componentes separados. Para obter mais informações, consulte [descrevendo o fluxo de dados](#DataFlows).

### <a name="describing-multiple-data-flows"></a>Descrevendo vários fluxos de dados
 Você pode desenhar mais de um fluxo de controle ou fluxo de objeto saindo de uma ação para indicar que mais de um thread surge quando a ação termina. O efeito é semelhante ao de uma bifurcação, exceto pelo fato de que você pode usar uma mistura de fluxos de controle e de objeto.

 O exemplo a seguir mostra vários fluxos de ações de e para.

 ![Fluxos de objeto paralelos](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")

 Quando a ação "o cliente fornece detalhes" é concluída, ela produz dois objetos: "endereço de entrega" e "detalhes do cartão de crédito". Os dois objetos avançam para o processamento por ações diferentes.

 Como uma ação requer que todas as suas entradas estejam disponíveis antes que ele possa ser iniciado, a última ação não é iniciada até que todas as ações que levam a ela sejam concluídas.

### <a name="streams"></a>Fluxos
 Você pode usar um diagrama de atividade para ajudá-lo a descrever um pipeline ou uma série de ações executadas ao mesmo tempo e passar continuamente dados de uma ação para outra.

 A intenção no exemplo a seguir é que cada ação pode produzir objetos e continuar a trabalhar. Como não há nenhum fluxo de controle, cada ação pode ser iniciada assim que recebe seus primeiros objetos.

 Observe que os conectores neste exemplo são fluxos de objeto, pois todos têm pelo menos uma extremidade em um nó de parâmetro de atividade, nó de objeto ou em um PIN de entrada ou saída.

 ![Um fluxo de dados](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")

 1. O exemplo tem três nós de parâmetro de atividade, que representam suas entradas e saídas.

 2. Os nós de objeto, os Pins de entrada e os Pins de saída podem representar buffers. Você pode definir a propriedade de limite superior de um nó de objeto para indicar quantos objetos podem estar no buffer ao mesmo tempo.

 3. Você pode usar nós de decisão para mostrar que um fluxo divide, enviando objetos diferentes para baixo em diferentes ramificações. Você pode usar comentários ou os títulos dos nós para explicar o que é o critério de divisão.

 4. Você pode usar nós de bifurcação para mostrar que duas ou mais cópias dos objetos são feitas, enviando-as para processamento simultâneo.

 5. Você pode usar nós de junção para mostrar que dois fluxos de processamento são mesclados novamente em um.

### <a name="selection-and-transformation"></a>Seleção e transformação
 Você pode especificar que os objetos em um fluxo de objeto sejam transformados, selecionados ou ambos. Um fluxo de objeto é um fluxo de ou para um PIN ou um nó de objeto.

- Uma transformação descreve como os objetos que entram em um fluxo são convertidos em outro tipo.

- Uma seleção descreve como apenas alguns dos objetos que inserem um fluxo são transmitidos para a ação de recebimento.

  O exemplo mostra uma transformação. A primeira ação no diagrama 1 produz um código postal, ou CEP, em um pino de saída. Isso está conectado a um PIN de entrada na segunda ação. Mas a segunda ação espera um endereço totalmente especificado. A conversão de um tipo para outro é especificada em uma segunda atividade, pesquisa de endereço. Isso é referenciado da propriedade Transformation do fluxo do objeto. A atividade de pesquisa de endereço contém um nó de parâmetro de atividade para o CEP de entrada e outro nó de parâmetro de atividade para o endereço completo de saída.

  ![Transformação de objeto definida em outro diagrama](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")

  Você pode especificar uma transformação ou seleção de duas maneiras:

- Anexe um comentário ao PIN de entrada ou saída.

  - Para distinguir essa descrição de um comentário geral, você pode iniciar o comentário com <\<**transformação**> > ou < **seleção**\<>.

- Especifique a transformação ou a seleção em detalhes em um diagrama de atividade separado.

  - Se você usar esse método, anexe um comentário também para torná-lo claro para os leitores de que a transformação foi definida.

##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Para especificar uma transformação ou seleção em um diagrama de atividade separado

1. Crie um novo diagrama de atividade no qual descrever a transformação ou o fluxo de seleção.

   - Em **Gerenciador de soluções**, clique com o botão direito do mouse em seu projeto, aponte para **Adicionar**, clique em **novo item**e clique em **diagrama de atividade**. Dê ao diagrama um nome apropriado para a transformação ou o fluxo de seleção. Clique em **Adicionar**.

2. No novo diagrama:

   1. Crie dois nós de parâmetro de atividade, um para o fluxo de entrada e outro para a saída.

   2. Criar ações interconectadas com fluxos de objeto. Isso mostra como a transformação ou seleção funciona.

3. Em qualquer diagrama em que você deseja usar a transformação ou seleção:

   1. Crie um fluxo de objeto, ou seja, um conector para ou de um PIN de entrada ou saída, um nó de objeto ou um nó de parâmetro de atividade.

   2. Clique com o botão direito do mouse no fluxo de objeto e clique em **Propriedades**.

   3. Na propriedade **transformação** ou **seleção** , selecione o diagrama em que você especificou a transformação ou o fluxo de seleção.

   Você também pode definir uma seleção para um nó de objeto e em Pins de entrada e saída individuais. Defina uma atividade de seleção como no procedimento anterior e, em seguida, defina a propriedade **Selection** do nó do objeto ou o PIN de entrada ou saída.

## <a name="see-also"></a>Consulte também
 [Editar modelos UML e diagramas](../modeling/edit-uml-models-and-diagrams.md) [diagramas de sequência UML: referenciar](../modeling/uml-sequence-diagrams-reference.md) [diagramas de componentes UML: referenciar](../modeling/uml-component-diagrams-reference.md) diagramas de [caso de uso UML: referenciar](../modeling/uml-use-case-diagrams-reference.md) diagramas de [classes UML: referenciar](../modeling/uml-class-diagrams-reference.md) [diagramas de componentes UML:](../modeling/uml-component-diagrams-reference.md) [vídeo de referência: capturar fluxos de trabalho comerciais usando diagrama](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows)
