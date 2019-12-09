---
title: 'Diagramas de sequência UML: diretrizes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c5906084fc7db96ddf304e8362bf7692dac62d5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297143"
---
# <a name="uml-sequence-diagrams-guidelines"></a>Diagramas de sequência UML: diretrizes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No Visual Studio, você pode desenhar um *diagrama de sequência* para mostrar uma interação. Uma interação é uma sequência de mensagens entre instâncias típicas de classes, componentes, subsistemas ou atores.

 Os diagramas de sequência UML fazem parte de um modelo UML e existem somente em projetos de modelagem UML. Para criar um diagrama de sequência UML, no menu **arquitetura** , clique em **novo UML ou diagrama de camada**. Saiba mais sobre [elementos de diagrama de sequência de UML](../modeling/uml-sequence-diagrams-reference.md) ou [diagramas de modelagem UML](../modeling/edit-uml-models-and-diagrams.md) em geral. Para ver uma demonstração em vídeo, consulte [esboço de interações usando diagramas de sequência (2010)](https://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>Neste tópico
 [Usando diagramas de sequência UML](#Using)

 [Etapas básicas para desenhar diagramas de sequência](#BasicSteps)

 [Criando e usando diagramas de sequência simples](#Simple)

 [Classes e linhas de vida](#ClassesAndLifelines)

 [Criando sequências de interação reutilizáveis](#Multiple)

 [Recolhendo grupos de linhas de vida](#Collapse)

 [Descrevendo estruturas de controle com fragmentos](#Fragments)

## <a name="Using"></a>Usando diagramas de sequência UML
 Você pode usar diagramas de sequência para uma variedade de finalidades em diferentes níveis de detalhes do programa. As ocasiões típicas para desenhar um diagrama de sequência são as seguintes:

- Se você tiver um diagrama de caso de uso que resume os usuários do sistema e suas metas, você pode desenhar diagramas de sequência para descrever como os principais componentes do sistema interagem para atender à meta de cada caso de uso. Para obter mais informações, consulte [diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md).

- Se você identificou mensagens que chegam a uma interface de um componente, você pode desenhar diagramas de sequência para descrever como as partes internas do componente interagem para obter o resultado necessário para cada mensagem de entrada. Para obter mais informações, consulte [diagramas de componentes UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md).

  Os diagramas de sequência de desenho têm vários benefícios:

- Você pode ver facilmente como as tarefas são distribuídas entre os componentes.

- Você pode identificar padrões de interação que dificultam a atualização do software.

## <a name="relationship-to-other-diagrams"></a>Relação com outros diagramas
 Você pode usar diagramas de sequência UML junto com outros diagramas de várias maneiras.

#### <a name="lifelines-and-types"></a>Linhas de vida e tipos
 As linhas de vida que você desenha em um diagrama de sequência podem representar instâncias típicas dos componentes ou classes no seu sistema. Você pode criar linhas de vida de tipos e tipos de linhas de vida e mostrar os tipos em diagramas de classes UML e diagramas de componente UML. Para obter mais informações, consulte [classes e linhas de vida](#ClassesAndLifelines).

#### <a name="parameter-types"></a>Tipos de parâmetro
 Você também pode descrever em um diagrama de classes UML os tipos de parâmetros e valores retornados que foram usados nas mensagens enviadas entre as linhas de vida.

#### <a name="use-case-details"></a>Detalhes de caso de uso
 Um caso de uso representa a meta de um usuário, junto com uma sequência de etapas para atingir a meta. A sequência de etapas pode ser descrita de várias maneiras. Uma opção é desenhar um diagrama de sequência que mostre as interações entre os usuários e os principais componentes do sistema. Para obter mais informações, consulte [diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Etapas básicas para desenhar diagramas de sequência
 Para obter uma lista completa de elementos em diagramas de sequência, consulte [diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md).

> [!NOTE]
> As etapas detalhadas de como criar qualquer um dos diagramas de modelagem são descritas em [editar modelos e diagramas UML](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-sequence-diagram"></a>Para criar um diagrama de sequência

1. No menu **arquitetura** , clique em **novo UML ou diagrama de camada**.

2. Em **modelos**, clique em **diagrama de sequência UML**.

3. Nomeie o diagrama.

4. Em **Adicionar ao projeto de modelagem**, selecione um projeto de modelagem existente em sua solução ou **crie um novo projeto de modelagem**e clique em **OK**.

    Um novo diagrama de sequência é exibido com a caixa de ferramentas de **diagrama de sequência** . A caixa de ferramentas contém os elementos e conectores necessários.

   ![Partes de um diagrama de sequência](../modeling/media/uml-sequence.png "UML_Sequence")

#### <a name="to-draw-a-sequence-diagram"></a>Para desenhar um diagrama de sequência

1. Arraste linhas de **vida** (1) da **caixa de ferramentas** para o diagrama para representar instâncias de classes, componentes, atores ou dispositivos.

    > [!NOTE]
    > Você também pode criar uma linha de vida arrastando uma classe, interface, ator ou componente existente do **Gerenciador de modelos UML** para o diagrama. Isso cria uma linha da vida que representa uma instância do tipo escolhido.

2. Desenhe mensagens para mostrar como as linhas de vida colaboram para atingir uma meta específica.

     Para criar uma mensagem (3, 4, 6, 7), clique em uma ferramenta de mensagem. Em seguida, clique na linha de vida de envio no ponto em que você deseja que a mensagem seja iniciada e clique na linha de vida de recebimento.

     Uma ocorrência de execução (5) é exibida na linha de vida de recebimento. A ocorrência de execução representa um período de tempo durante o qual a instância está executando um método. Você pode criar outras mensagens que iniciam de uma ocorrência de execução.

3. Para mostrar uma mensagem proveniente de uma origem de evento desconhecida (9) ou difusões para destinatários desconhecidos (10), desenhe uma mensagem assíncrona de ou para um espaço em branco no diagrama. Essas mensagens são chamadas de *mensagens encontradas* (9) e *mensagens perdidas* (10).

    > [!NOTE]
    > Para mover um grupo de linhas de vida que perderam ou encontrou mensagens, siga estas etapas para selecionar as linhas de vida antes de movê-las: Desenhe um retângulo em volta dessas linhas de vida ou pressione e mantenha pressionada a tecla **Ctrl** enquanto clica em cada linha da vida. Se você usar **selecionar tudo** ou **Ctrl**+a para selecionar todas as **linhas de vida** e, em seguida, movê-las, todas as mensagens perdidas ou encontradas anexadas a essas linhas de vida não serão movidas. Se esse cenário ocorrer, será possível mover essas mensagens separadamente.

4. Desenhe diagramas de sequência para cada mensagem principal para o mesmo componente ou sistema.

#### <a name="to-change-the-order-of-messages"></a>Para alterar a ordem das mensagens

- Arraste uma mensagem para cima ou para baixo em sua linha da vida. Você pode arrastá-lo sobre outras mensagens ou para dentro ou fora de um bloco de execução.

     \- ou -

- Clique na mensagem e use as teclas **seta para cima** e seta para **baixo** para ajustar as posições das mensagens. Use **Shift + seta para cima** e **Shift + seta para baixo** para alterar a ordem das mensagens.

#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>Para mover ou copiar sequências de mensagens no diagrama de sequência

1. Clique com o botão direito do mouse em uma mensagem (3, 4) e clique em **copiar**.

2. Clique com o botão direito do mouse na ocorrência de execução (5) ou uma linha da vida (1) da qual você deseja que a nova mensagem seja enviada e, em seguida, clique em **colar**. Se desejar, o novo remetente poderá estar em um diagrama diferente.

     Uma cópia da mensagem e todas as suas mensagens subsidiárias são adicionadas ao final da ocorrência de execução ou ao final da linha de vida.

    > [!NOTE]
    > A mensagem colada sempre aparece no final da ocorrência de execução ou da linha de vida. Depois de colá-lo, você pode arrastá-lo para uma posição anterior.

#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>Para exibir e editar o texto da assinatura de uma mensagem

- A linha de vida de destino deve ser vinculada ou mapeada para tipos para que o texto da assinatura fique visível. Para realizar essa tarefa, execute uma das seguintes etapas:

  - Clique com o botão direito do mouse na linha de vida e escolha **criar classe**.

     - ou -

  - Selecione a linha da vida, pressione **F4**e, na janela **Propriedades** , defina a propriedade **Type** como um tipo existente ou especifique o nome para um novo tipo. Clique com o botão direito do mouse no rótulo da mensagem e escolha **criar operação**.

    O texto da assinatura é exibido abaixo do rótulo da mensagem. Agora você pode editar o texto da assinatura. Para obter mais informações, consulte [classes e linhas de vida](#ClassesAndLifelines).

#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>Para melhorar o layout de um diagrama de sequência

- Clique com o botão direito do mouse em uma parte em branco do diagrama e clique em **reorganizar layout**.

- Para desfazer a operação, clique em **Editar**e em **desfazer**.

#### <a name="to-change-the-package-that-owns-the-interaction"></a>Para alterar o pacote que possui a interação

1. No **Gerenciador de modelos UML**, localize a interação que o diagrama de sequência exibe.

    > [!NOTE]
    > A interação não será exibida no **Gerenciador de modelos UML** até que você adicione a primeira linha da vida ao diagrama de sequência.

2. Arraste a interação para o pacote.

     \- ou -

     Clique com o botão direito do mouse na interação e clique em **recortar**. Clique com o botão direito do mouse no pacote e clique em **colar**.

## <a name="Simple"></a>Criando e usando diagramas de sequência simples
 A forma mais simples e mais amplamente usada do diagrama de sequência contém apenas linhas de vida e mensagens. Um diagrama desse tipo permite mostrar claramente uma sequência típica de interações entre objetos no seu design ou entre o sistema e seus usuários. Isso é muitas vezes suficiente para ajudá-lo a discutir e comunicar seu design.

 Aqui estão algumas coisas a serem consideradas ao desenhar um diagrama de sequência simples.

### <a name="types-of-message"></a>Tipos de mensagem
 Há três ferramentas que você pode usar para criar mensagens.

- Use a ferramenta **síncrona** para descrever uma interação na qual o remetente espera que o destinatário retorne uma resposta (3).

     Um **<\<retornar > seta >** será mostrado no final da ocorrência de execução. Indica o retorno do controle para o remetente.

- Use a ferramenta **assíncrona** para descrever uma interação na qual o remetente pode continuar imediatamente sem esperar o receptor (4).

- Use a ferramenta **criar** para descrever uma interação na qual o remetente cria o receptor (8).

     Uma mensagem de criação deve ser a primeira mensagem que o receptor recebe.

### <a name="annotating-the-interactions"></a>Anotando as interações
 Para descrever mais detalhes sobre a sequência, você pode inserir um **Comentário** em qualquer lugar do diagrama.

 Usando **links de comentário**, você pode vincular um comentário a linhas de vida, execuções, usos de interação e fragmentos.

> [!CAUTION]
> Quando você quiser anexar um comentário a um ponto específico na sequência, vincule-o a uma ocorrência de execução, uso de interação ou fragmento. Não vinculá-lo a uma linha da vida, porque nesse caso, ele não permanece anexado no ponto correto na sequência.

 Use um comentário para:

- Observe o que foi obtido em pontos-chave na sequência. Isso ajuda os leitores a ver os objetivos das interações.

- Descreva o objetivo geral da sequência inteira. Anexe o comentário à ocorrência de execução inicial ou deixe-a desanexada. Por exemplo, "o cliente escolheu itens do menu e recebeu um preço".

- Descreva as responsabilidades de cada linha da vida. Anexe o comentário à linha da vida. Por exemplo, "gerente de pedidos coleta as opções de menu do cliente".

- Observação as exceções ou alternativas que podem ser executadas como uma alternativa à sequência típica mostrada. Por exemplo, "o cliente pode optar por ignorar o restante desta sequência".

  - Considere o uso de fragmentos como uma alternativa mais formal para esse tipo de observação. Consulte [descrevendo estruturas de controle com fragmentos](#Fragments)

## <a name="deciding-the-scope-of-the-diagram"></a>Decidindo o escopo do diagrama
 É importante estar claro sobre o que o diagrama pretende mostrar.

#### <a name="initiating-event"></a>Iniciando evento
 Cada diagrama deve mostrar a sequência de interações que resulta de um evento de inicialização. Isso pode ser, por exemplo:

- Um usuário que inicia um caso de uso, por exemplo, abrindo a página da Web para comprar uma refeição.

- Uma mensagem de um componente do sistema para outro, por exemplo, consultando a disponibilidade de itens que um cliente deseja comprar.

- Um evento disparado por uma alteração de estado, por exemplo, ações de um item que ficam abaixo de um limite.

#### <a name="level-of-detail"></a>Nível de detalhe
 Os diagramas de sequência podem mostrar diferentes níveis de detalhes. Você pode decidir o nível de detalhe em duas dimensões separadas quase de forma independente:

 As linhas de vida podem representar um destes níveis de detalhes:

- Objetos no código do programa, que existem ou que você está desenvolvendo.

- Componentes ou seus subcomponentes, geralmente omitindo fachadas, proxies e outros mecanismos de conexão.

- Seu sistema e atores externos

  As mensagens podem representar um desses níveis de detalhes:

- Mensagens de software no código do programa, em uma API ou em uma interface da Web.

- Transações ou subtransações, por exemplo, entre os usuários e o sistema, ou entre o código e o banco de dados.

- Casos de uso – interações principais entre os usuários e o sistema.

  Se você estiver explorando o código existente ou descrevendo um novo design, geralmente é útil desenhar e discutir as exibições menos detalhadas.

## <a name="describing-variations"></a>Descrevendo variações
 O diagrama mostra uma sequência de eventos única e típica. Se você quiser mostrar possibilidades alternativas, como cenários de falha, poderá usar uma destas opções:

- Desenhar diagramas de sequência separados para descrever esses cenários

- Use a [Descrição de estruturas de controle com fragmentos](#Fragments) para mostrar loops, alternativas e assim por diante.

## <a name="assessing-the-design"></a>Avaliando o design
 Você pode usar o diagrama para avaliar a distribuição de tarefas entre seus objetos ou componentes. Considere refatorar se você vir estes padrões:

- Uma linha da vida parece fazer tudo, fazendo chamadas para tudo o mais, enquanto as outras linhas de vida respondem passivamente.

- Muitas mensagens cruzam linhas de vida. Cada linha da vida deve enviar mensagens para apenas alguns vizinhos e não deve se comunicar com os vizinhos de seus vizinhos. Normalmente, deve ser possível organizar as linhas de vida para que haja apenas alguns lugares em que as mensagens cruzam as linhas de vida; e onde há cruzamentos, a linha da vida de destino não deve também trocar mensagens que têm as linhas de vida cruzadas.

- Algumas linhas de vida parecem lidar com mais de um tipo de tarefa. É fácil encontrar uma frase sucinta que descreve as responsabilidades de cada linha de vida, resumindo o trabalho que ele faz em resposta a cada mensagem que recebe.

## <a name="ClassesAndLifelines"></a>Classes e linhas de vida
 As linhas de vida em seus diagramas de sequência mostram instâncias de classes ou interfaces de componente. Você pode nomear uma linha de vida de duas maneiras:

|**Para essa finalidade**|**Usar este formato**|
|--------------------------|-------------------------|
|Instância anônima de um tipo.<br /><br /> Use-a se você tiver apenas uma linha da vida de cada tipo.|*typeName*|
|Instância nomeada de um tipo.<br /><br /> Use esta se desejar mostrar uma sequência que envolva mais de uma instância do mesmo tipo.|*objectname*:*TypeName*|

### <a name="creating-lifelines-from-types"></a>Criando linhas de vida de tipos
 Você pode criar novas linhas de vida de classes que você já definiu, por exemplo, em um diagrama de classe.

> [!NOTE]
> Verifique se você tem um diagrama de sequência existente antes de executar essa tarefa.

##### <a name="to-create-a-lifeline-from-an-existing-type"></a>Para criar uma linha de vida a partir de um tipo existente

- Arraste uma classe, componente ou interface do Gerenciador de modelos UML para um diagrama de sequência.

   \- ou -

  1. Clique com o botão direito do mouse na classe, componente ou interface em seu respectivo diagrama e, em seguida, clique em **Criar linha de vida**.

  2. Na caixa de diálogo **Criar linha de vida** , selecione um diagrama de sequência e clique em **OK**.

     Uma nova linha de vida de instância nomeada é exibida cujo tipo é o tipo que você arrastou.

  > [!NOTE]
  > Você pode repetir essa ação quantas vezes desejar. Isso criará linhas de vida com nomes de instância diferentes.

##### <a name="to-change-the-type-of-a-lifeline"></a>Para alterar o tipo de uma linha de vida

1. Clique com o botão direito do mouse em uma linha da vida e clique em **Propriedades**.

2. Na janela **Propriedades** , defina a propriedade **Type** . Você pode selecionar um tipo no menu suspenso ou digitar um novo nome.

### <a name="creating-classes-from-lifelines"></a>Criando classes de linhas de vida
 Quando você tiver criado um ou mais diagramas de sequência, poderá resumir as linhas de vida criando classes ou interfaces a partir delas.

##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>Para criar uma classe ou interface de uma linha de vida

1. Clique com o botão direito do mouse na linha de vida e clique em **criar classe** ou **criar interface**.

     Uma nova classe ou interface aparece no Gerenciador de modelos UML.

2. Crie operações na classe ou na interface para cada mensagem que a linha de vida recebe:

    1. Selecione todas as mensagens que você deseja incluir.

    2. Clique com o botão direito do mouse em uma das mensagens e clique em **criar método**.

         A nova classe ou interface tem operações para cada mensagem selecionada.

         O nome da operação é exibido abaixo de cada seta de mensagem e na propriedade **Operation** da mensagem.

         Se a mensagem tiver os parâmetros incluídos no formato "(parâmetro: tipo)", eles serão exibidos na lista de parâmetros da nova operação.

        > [!NOTE]
        > Você deve repetir esta etapa se adicionar novas mensagens no diagrama de sequência.

3. Para exibir a nova classe ou interface em detalhes, adicione-a a um diagrama de classe ou componente.

    1. Abra ou crie um diagrama de classe ou componente.

    2. Arraste a nova classe ou interface do **Gerenciador de modelos UML** para um diagrama de classe.

         A classe ou interface aparece no diagrama de classe.

         \- ou -

    3. Arraste a nova interface do **Gerenciador de modelos UML** para um componente ou porta em um diagrama de componente.

         A interface aparece no componente como uma pirulito.

### <a name="creating-classes-for-parameters"></a>Criando classes para parâmetros
 Você pode incluir parâmetros nas mensagens em um diagrama de sequência. Você pode usar um diagrama de classe UML para descrever os tipos de parâmetro.

## <a name="Multiple"></a>Criando sequências de interação reutilizáveis
 Você pode usar um diagrama separado para descrever uma sequência que contém detalhes que você deseja separar, ou que seja comum entre vários diagramas.

 Você pode criar um retângulo de uso de interação (12) em um diagrama que aponta para os detalhes em outro diagrama.

 Clique duas vezes em um uso de interação para abrir o diagrama de sequência que está vinculado a ele.

#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>Para criar uma sequência de interação reutilizável a partir de linhas de vida existentes

1. Na **caixa de ferramentas**, clique em **uso de interação**.

2. No diagrama de sequência, mantenha o botão do mouse pressionado enquanto arrasta pelas linhas de vida que você deseja incluir na sequência reutilizável. Inicie na posição vertical onde você deseja inserir o uso de interação.

     Um uso de interação é exibido nas linhas de vida selecionadas no diagrama de sequência.

3. Clique duas vezes no nome no uso da interação e renomeie-o para descrever o efeito da sequência reutilizável neste diagrama.

     \- ou -

     Escreva o nome como uma chamada de função, com parâmetros.

4. Vincule o uso de interação a outro diagrama de sequência. Clique com o botão direito do mouse no uso da interação e, em seguida:

     Clique em **criar nova sequência** para criar um novo diagrama de sequência

     \- ou -

     Clique em **vincular à sequência** para vincular a um diagrama existente.

     O Visual Studio cria um vínculo entre o uso de interação e a nova sequência de interação.

     Um novo diagrama de sequência aparece em sua solução. Ele contém as linhas de vida que você usou para criar o uso de interação.

    > [!NOTE]
    > Somente as linhas de vida que você usou para criar o uso de interação serão incluídas. O novo diagrama não incluirá linhas de vida que você criou após o uso da interação, mesmo que o uso da interação agora as cubra.

#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>Para criar uma sequência reutilizável a partir de mensagens existentes

- Clique com o botão direito do mouse na mensagem que você deseja mover e clique em **mover para o diagrama**.

  Visual Studio:

  - Substitui por uma interação use a mensagem selecionada e todas as mensagens da subsidiária.

  - Move as mensagens substituídas para um novo diagrama de sequência.

  - Cria um vínculo entre o uso de interação e o novo diagrama de sequência.

#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>Para navegar até a sequência referenciada por um uso de interação

- Clique duas vezes no uso da interação.

     \- ou -

     Clique com o botão direito do mouse no uso da interação e clique em **ir para sequência**.

### <a name="creating-a-placeholder-with-an-interaction-use"></a>Criando um espaço reservado com um uso de interação
 Você pode criar um uso de interação sem vinculá-lo a outro diagrama. Você pode usar isso como um espaço reservado para uma parte da sequência cujos detalhes ainda devem ser configurados. Use o nome do uso de interação para indicar o resultado desejado.

## <a name="Collapse"></a>Recolhendo grupos de linhas de vida
 Você pode recolher um conjunto de linhas de vida, para que o grupo apareça como uma linha da vida. Isso ajuda a Visualizar um grupo de objetos como um único componente. As mensagens e as utilizações de interação entre as linhas de vida em um grupo recolhido são ocultas. As mensagens e as sequências de interação que incluem outras linhas de vida são mostradas.

#### <a name="to-collapse-a-group-of-lifelines-together"></a>Para recolher um grupo de linhas de vida juntas

1. Selecione duas ou mais linhas de vida.

2. Clique com o botão direito do mouse em um deles e clique em **recolher**.

     As linhas de vida separadas são substituídas por uma única linha da vida.

     As mensagens e os usos de interação que envolvem apenas membros do grupo são ocultos.

3. Para renomear o grupo, clique no nome.

    > [!NOTE]
    > O nome do grupo será perdido quando você expandir o grupo.

#### <a name="to-expand-a-collapsed-group"></a>Para expandir um grupo recolhido

- Clique com o botão direito do mouse na linha de vida recolhida e clique em **expandir**.

    > [!NOTE]
    > O nome do grupo será perdido, junto com todos os links do grupo para comentários ou itens de trabalho.

## <a name="Fragments"></a>Descrevendo estruturas de controle com fragmentos
 Você pode usar fragmentos combinados (13) para definir loops, ramificações e processamentos simultâneos em um diagrama de sequência. Como alternativa, considere usar um diagrama de atividade em vez disso. O diagrama de atividade não é tão útil na exibição de mensagens entre atores, mas, em alguns casos, é melhor na exibição de loops, ramificações e simultaneidade.

 Para obter uma lista completa dos tipos de fragmento, consulte [descrever o fluxo de controle com fragmentos em diagramas de sequência UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).

#### <a name="to-create-a-combined-fragment"></a>Para criar um fragmento combinado

1. Selecione uma mensagem ou uma sequência de mensagens que comece na mesma ocorrência de execução ou linha de vida.

    > [!NOTE]
    > Selecione as setas de mensagem, não as ocorrências de execução às quais as mensagens apontam.

2. Clique com o botão direito do mouse em uma das mensagens, aponte para **surround com**e clique no tipo de fragmento que você precisa.

     Um novo fragmento é exibido. Ele contém as mensagens que você selecionou.

     Se o tipo de fragmento combinado permitir vários fragmentos, um fragmento vazio também será exibido.

3. Para definir a proteção de um fragmento, clique com o botão direito do mouse na borda do fragmento e clique em **Propriedades**. Defina a propriedade **Guard** .

     A proteção é usada para definir a condição para um Branch ou um loop.

4. Para adicionar um novo fragmento a um tipo que permita vários fragmentos, clique com o botão direito do mouse no limite de um fragmento e aponte para **Adicionar**. Clique em um **operando de interação antes** ou **operando de interação após**.

5. Para adicionar novas mensagens a um fragmento, use as ferramentas de mensagem ou copie e Cole.

## <a name="see-also"></a>Consulte também
 [Diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md) [editar modelos UML e diagramas](../modeling/edit-uml-models-and-diagrams.md) [diagramas de caso de uso UML: referenciar](../modeling/uml-use-case-diagrams-reference.md) [diagramas de classe UML: referenciar](../modeling/uml-class-diagrams-reference.md) diagramas de [componentes UML: referenciar](../modeling/uml-component-diagrams-reference.md) [diagramas de componentes UML:](../modeling/uml-component-diagrams-reference.md) [vídeo de referência: o esboço de interações usando diagramas](https://go.microsoft.com/fwlink/?LinkId=201113)
