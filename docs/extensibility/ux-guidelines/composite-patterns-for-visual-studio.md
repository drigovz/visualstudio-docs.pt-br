---
title: Padrões compostos para estúdio visual | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 500ea8ffe7c33c1d747590ea074bff43fa1a3ab3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698623"
---
# <a name="composite-patterns-for-visual-studio"></a>Padrões de composição para Visual Studio
Padrões compostos combinam elementos de interação e design em configurações distintas. Alguns dos padrões compostos mais importantes no Visual Studio no que diz respeito à consistência incluem:

- [Visualização de dados](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [UI on-object e espiando](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modelos de seleção](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Configurações de persistência e salvamento](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Entrada de toque](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a>Visualização de dados

### <a name="overview"></a>Visão geral
 Os gráficos são uma forma visual de agregar e visualizar dados a fim de melhorar a tomada de decisões. Eles podem ajudar os usuários diante de muitos dados, mas pouco sentido ver o que merece atenção e o que pode precisar de uma ação.

 O usuário se beneficiará de um gráfico se alguma das seguintes condições for verdadeira:

- O gráfico ajudará os usuários a identificar tarefas em que podem atuar?

- O gráfico permitirá que os usuários pretem consequências de possíveis mudanças?

- O gráfico ajudará os usuários a descobrir tendências e identificar padrões?

- O gráfico permitirá que os usuários tomem melhores decisões?

- O gráfico ajudará a responder a uma pergunta específica que os usuários podem ter no determinado contexto?

#### <a name="general-rules-for-charts"></a>Regras gerais para gráficos

- Claramente rotular dados. Ilustrações sem explicação são apenas imagens bonitas.

- Inicie eixos a zero para evitar proporções distorcidas. Comprimento da linha e tamanho da barra são pistas visuais importantes para entender as relações entre os pontos de dados.

- Crie gráficos, não infográficos. Infográficos são representações artísticas de dados, e seu objetivo principal é contar histórias visuais. Os gráficos podem (e devem) ser visualmente atraentes, mas deixe os dados falarem por si mesmos.

- Evite esquemorfismo, gráficos de barras pictóricas, hashmarks de contraste e outros toques infográficos.

- Não use efeitos 3D como elemento decorativo. Use-os apenas se eles realmente integram a capacidade do usuário de compreender as informações.

- Evite usar várias linhas e preenchimentos, pois mais de duas cores podem dificultar a leitura e interpretação corretamente deste tipo de gráfico.

- Não use um gráfico (ou qualquer ilustração) como o único meio de entender um conceito ou interagir com dados. Isso apresenta dificuldades para usuários com deficiência visual.

- Não use gráficos como elementos gratuitos ou decorativos em uma página. Em outras palavras, se um gráfico não adicionar nenhum valor ou ajudar os usuários a resolver um problema, não o use.

### <a name="chart-types"></a>Tipos de gráfico
 Os tipos de gráficos usados no Visual Studio incluem gráficos de barras, gráficos de linha, um gráfico de torta modificado conhecido como gráfico de anel ou "gráfico de donuts", linhas de tempo, gráficos de dispersão (também chamados de "gráficos de cluster") e gráficos de Gantt. Cada tipo de gráfico é útil para comunicar um tipo diferente de informação.

### <a name="other-charting-considerations"></a>Outras considerações de gráficos

#### <a name="color"></a>Color
 Há uma paleta específica de cores de gráficos definidas para uso no Visual Studio. A paleta é acessível para os principais tipos de cegueira de cores, e as cores podem ser diferenciadas mesmo quando usadas como fatias muito estreitas de cor. Você pode usar essas cores em qualquer combinação para qualquer tipo de gráfico ou gráfico em sua ia. Você não precisa usar todas as sete cores se você não precisa de tantas cores distintas. Essas cores não foram projetadas para serem usadas com quaisquer elementos em primeiro plano, por isso não coloque texto ou glifos em cima dessas cores. Essas tonalidades devem ser codificadas e expostas à personalização do usuário em **Opções de > (ver** [Expondo cores para usuários finais](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Swatch|Hex|RGB|
|------------|---------|---------|
|![Swatch 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![Swatch BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Swatch FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Swatch 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Swatch 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Swatch 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Swatch B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a>UI on-object e espiando
 Esta seção dá contexto à espia, também conhecida como exibição de espia código, um tipo de interface do usuário no objeto exclusivo para o Visual Studio.

### <a name="overview"></a>Visão geral

- A ui on-object deve dar ao usuário mais informações ou interatividade sem prejudicar sua tarefa principal.

- O principal padrão de ui on-object no Visual Studio é conhecido como "informação no ponto de atenção".

- A ui on-object no Visual Studio é inline ou flutuante e durável ou transitória.

  - A exibição de peek de código, um tipo de ui on-object no Visual Studio, é inline e durável.

  - CodeLens, um tipo de ui on-object no Visual Studio, é flutuante e transitório

  Entender como um pedaço de código funciona, ou encontrar detalhes sobre esse código, muitas vezes requer que um desenvolvedor mude de contexto e vá para outro conteúdo ou outra janela. Essas mudanças de contexto podem ser disruptivas, porque os usuários podem perder o foco em sua tarefa original se saírem de sua janela principal. Além disso, recuperar esse contexto original pode ser difícil, especialmente se a troca de janelas fez com que seu código original fosse obscurecido por outras interfaces.

  A ui on-object segue um padrão chamado "informação no ponto de atenção". Essas mensagens, janelas pop-up e caixas de diálogo dão aos usuários informações adicionais e relevantes que adicionam esclarecimento ou interatividade sem perder o foco em sua tarefa principal. Exemplos de interface do usuário no objeto incluem janelas pop-up que aparecem quando um usuário paira sobre seu ponteiro sobre um ícone na área de notificação, o rabisco vermelho sob uma palavra mal escrita e a exibição de peek introduzida no Visual Studio 2013.

### <a name="decision-points"></a>Pontos de decisão
 Dentro do Visual Studio, existem várias maneiras de usar esse padrão de informação no ponto de atenção. Escolher o mecanismo certo e implementá-lo de forma consistente e previsível é essencial para a experiência geral. Caso contrário, os usuários podem ser apresentados com uma experiência confusa ou inconsistente que prejudica o foco do conteúdo em si.

#### <a name="relationships-between-master-and-detail-content"></a>Relações entre conteúdo mestre e detalhado
 Informações no ponto de atenção são usadas para exibir uma relação entre o conteúdo em que o usuário está focado (o conteúdo "mestre") e conteúdo adicional relacionado (o conteúdo "detalhe"). Neste padrão, o conteúdo de detalhes está claramente relacionado ao conteúdo com o qual o usuário está trabalhando e pode ser exibido perto do conteúdo mestre. Informações suplementares ou que não podem ser resumidas sem sobrecarregar o conteúdo mestre devem seguir outro padrão, como uma janela de ferramenta.

- **Sempre** exiba o conteúdo de detalhes próximo ao conteúdo principal.

- **Certifique-se sempre** de que o conteúdo detalhado ainda permite que o usuário permaneça focado no conteúdo mestre. Muitas vezes, a melhor maneira de conseguir isso é tornar o conteúdo detalhado o mais próximo possível do conteúdo mestre. Isso pode ser feito renderizando o conteúdo de detalhes em uma janela pop-up ao lado do conteúdo mestre, ou renderizando o conteúdo de detalhes em linha abaixo do conteúdo mestre.

- **Nunca** use informações no ponto de atenção que tire o usuário do conteúdo mestre. Se os usuários precisarem visualizar o conteúdo de detalhes separadamente, exponha uma ação explícita que permita que o usuário faça isso.

#### <a name="design-details"></a>Detalhes do design
 Uma vez que você tenha determinado que a ui no objeto é a escolha certa, existem quatro considerações principais de design:

1. **Persistência:** espera-se que o conteúdo seja durável ou transitório?
   Os usuários desejam manter as informações visíveis para se referir ou interagir? Ou os usuários vão querer olhar rapidamente para as informações e, em seguida, continuar com sua tarefa principal?

2. **Tipo de conteúdo:** o conteúdo será informativo, acionável ou navegável?
   O usuário precisa de mais detalhes sobre o conteúdo principal? O usuário precisa concluir uma tarefa que afete o conteúdo principal? Ou o usuário precisa ser direcionado para outro recurso?

3. **Tipo de indicador:** um indicador ambiente faz sentido?
   As informações podem ser resumidas de forma útil e exibidas sem sobrecarregar o conteúdo principal?

4. **Gestos:** que gestos serão usados para invocar e demitir a UI?
   Como o usuário vai trazer o conteúdo detalhado e enviá-lo embora? Há valor em adicionar um gesto como fixar para alternar entre estados transitórios e duráveis?

   Cada um desses quatro pontos de decisão terá um impacto sobre os principais componentes da ui on-object.

### <a name="on-object-ui-components"></a>Componentes de iu de ida e componente sumido no objeto

1. Tipo de contêiner (apresentador de conteúdo)

    - Flutuante

    - Embutido

2. Tipo de conteúdo

    - Informativo: dados que podem ser estáticos ou dinâmicos

    - Acionável: comandos que alteram o conteúdo mestre

    - Navegação: links que levam o usuário para outra janela ou aplicativo, como o MSDN

3. Gestos

    - Invocação

    - Demissão

    - Fixação

    - Outras interações

4. Persistência e modelo de compromisso

    - Transitório

    - Durável

    - Automático

    - Sob demanda

5. Indicadores ambientais (opcionais)

    - Sublinhado squiggle

    - Ícone de tag inteligente

    - Outros indicadores ambientais

#### <a name="container-content-presenter-type"></a>Tipo de contêiner (apresentador de conteúdo)
 Existem duas opções principais disponíveis para apresentar conteúdo no ponto de atenção:

1. **Inline:** um apresentador inline, como a visão de peek que foi introduzida no Visual Studio 2013 Code Editor, abre espaço para novos conteúdos mudando o conteúdo existente.

    - **Prefira** apresentadores inline se você espera que os usuários queiram gastar uma quantidade significativa de tempo se referindo ou interagindo com o conteúdo que você apresenta.

    - **Evite** apresentadores inline se você espera que os usuários queiram olhar para as informações que você apresenta, em seguida, continue com sua tarefa principal com interrupção mínima.

2. **Flutuante:** um apresentador flutuante é posicionado o mais próximo possível do conteúdo selecionado, mas não altera o layout do conteúdo existente. Várias estratégias podem ser empregadas, como exibir um painel de conteúdo flutuante sobre o espaço branco disponível mais próximo ao símbolo selecionado.

    - **Prefira** apresentadores flutuantes se você espera que os usuários queiram olhar para as informações que você apresenta, em seguida, continue com sua tarefa principal com o mínimo de interrupção.

    - **Evite** apresentadores flutuantes se você espera que os usuários queiram gastar uma quantidade significativa de tempo se referindo ou interagindo com o conteúdo que você apresenta.

#### <a name="content-type"></a>Tipo de conteúdo
 Existem três tipos principais de conteúdo que podem ser exibidos dentro de qualquer contêiner de ida e volta no objeto. Qualquer combinação desses tipos de informação pode ser mostrada. Os três tipos são:

1. **Informativo: a** maioria dos contêineres de iu no objeto exibirá algum tipo de conteúdo informativo. O conteúdo pode representar informações sobre o estado atual do ambiente ou pode representar informações sobre um potencial estado futuro do meio ambiente. Por exemplo, ele poderia ser usado para mostrar o efeito de um determinado comando, como uma refatoração, no código existente.

    - **Use sempre** a representação canônica das informações exibidas. Por exemplo, o código deve parecer código, completo com destaque de sintaxe, e deve respeitar qualquer fonte e outras configurações de ambiente que o usuário definiu.

    - **Sempre** considere apoiar quaisquer ações sobre o conteúdo informativo que seriam possíveis se essas mesmas informações forem apresentadas como conteúdo mestre. Por exemplo, se apresentar o código existente dentro de um contêiner de ida e volta no objeto, considere fortemente o suporte à capacidade de navegar e modificar esse código.

    - **Sempre** considere usar uma cor de fundo diferente se apresentar conteúdo informativo que represente um estado futuro potencial.

2. Acionável: alguns contêineres de iu on-object fornecerão a capacidade de executar alguma ação sobre o conteúdo mestre, como a realização de uma operação de refatoração.

    - **Sempre** posicione comandos acionáveis separadamente do conteúdo informativo.

    - **Sempre** habilite e desative ações quando apropriado.

    - **Consulte sempre** as diretrizes padrão para representar comandos dentro de caixas de diálogo.

    - **Mantenha sempre** o número de ações expostas em um contêiner de iu on-object ao mínimo. Interagir com a ui on-object deve ser uma experiência leve e rápida. O usuário não deve gastar energia no gerenciamento do próprio contêiner de iu on-object.

    - **Sempre** considere como e quando um contêiner de iu on-object será fechado ou descartado. Como uma prática recomendada, qualquer ação que conclua o diálogo entre o conteúdo mestre e detalhado também deve fechar o contêiner de ui on-object quando essa ação for invocada.

3. **Navegação:** alguns contêineres de interface do usuário incluem links que levam o usuário para outra janela ou aplicativo, como a abertura de um artigo mSDN no navegador da Web do usuário.

    - **Prepare sempre** qualquer link de navegação com "Open" para que os usuários não se surpreendam ao serem navegados para algum outro conteúdo.

    - **Sempre** separe links de navegação de links acionáveis.

#### <a name="ambient-indicators-optional"></a>Indicadores ambientais (opcionais)
 Os indicadores ambientais podem ser sutis, incluindo texto apresentado em uma cor contrastante do resto do código, ou óbvio, incluindo símbolos de cócegas, como sublinhados squiggle e ícones de tag inteligentes. Os indicadores ambientais comunicam a disponibilidade de informações adicionais e relevantes. Idealmente, eles fornecem informações úteis mesmo sem exigir que o usuário interaja com eles.

- **Posicione sempre** um indicador ambiente para que ele não distraia ou sobrecarregue o usuário. Se é impossível posicionar um indicador ambiental de tal forma, considere outra solução.

- **Posicione sempre** o indicador ambiente o mais próximo possível do conteúdo a que está relacionado.

- **Procure sempre** criar um indicador que siseja as informações que ele disponibiliza. Considere fornecer uma contagem do número de itens de dados disponíveis (por exemplo, "3 referências" em vez de simplesmente "Referências") ou pensar em outra maneira de resumir os dados.

  - Nos casos em que os dados de um indicador nem sempre podem ser computados e exibidos, considere imediatamente fornecer feedback progressivo à medida que os valores são computados. Por exemplo, considere as alterações animadoras que refletem atualizações nos dados disponíveis, semelhante à maneira como o e-mail live tile no Windows Phone é atualizado à medida que o número de e-mails não lidos aumenta.

- **Nunca** adicione mais indicadores do que um usuário pode razoavelmente receber um determinado conteúdo. Os indicadores ambientais devem ser úteis sem exigir qualquer interação do usuário. Os indicadores perdem seu ambiente se necessitam de transbordamento e outros controles de gestão para trazê-los à vista.

#### <a name="gestures"></a>Gestos
 Um aspecto fundamental de permitir que o usuário mantenha o foco no conteúdo principal é apoiar os gestos certos para abrir e descartar o conteúdo adicional de detalhes.

- **Sempre** exija que o usuário execute algum gesto explícito para abrir o conteúdo adicional. Gestos abertos comuns incluem:

  - **Hover: dicas** de ferramentas ou conteúdo informativo não interativo

  - **Comando explícito:** apresentador inline

  - **Clique duas vezes no indicador ambiente:** Janela pop-up codeLens

- **Sempre** descarte o conteúdo de detalhes sempre que o usuário pressionar a tecla Esc.

- **Sempre** considere o contexto da interface do usuário no objeto. Para os apresentadores de conteúdo que permitem a interação dentro do contêiner, considere cuidadosamente se deve mostrar informações adicionais sobre o hover, o que provavelmente será perturbador para o fluxo de trabalho do usuário.

- **Nunca** exiba conteúdo em hover que pareça ser editável ou convide a interação do usuário. Esse comportamento pode frustrar os usuários se eles tentarem mover o cursor sobre o conteúdo de detalhes, já que o comportamento padrão para uma dica de ferramenta é descartar imediatamente quando o cursor não estiver mais sobre o conteúdo mestre que o produziu.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a>Modelos de seleção

### <a name="overview"></a>Visão geral
 Um modelo de seleção é o mecanismo usado para indicar e confirmar operações em um ou mais objetos de interesse dentro da interface do usuário. Este tópico discute padrões de interação de seleção dentro de editores de documentos do Visual Studio: editores de texto, superfícies de design e superfícies de modelagem.

 Os usuários devem ter uma maneira de indicar ao Visual Studio o que estão trabalhando, e o Visual Studio deve responder previsivelmente com feedback aos usuários sobre o que está operando. Diferenças ou uma falha de comunicação entre o usuário e a interface do usuário podem fazer com que o usuário não perceba uma ação, o que pode ter consequências não intencionais. Muitas vezes, o erro passa despercebido até que o usuário veja que algo está faltando ou mudou. Os modelos de seleção são, portanto, uma das peças mais críticas do design da interface do usuário. Embora os modelos de seleção no Visual Studio sejam consistentes com o Windows, há pequenas variações.

 No Visual Studio, como no Windows, os modelos de seleção diferem dependendo do contexto em que a interação ocorre. As seleções podem ocorrer em quatro tipos de objetos:

- Texto

- Objetos gráficos

- Listas e árvores

- Grades

  Dentro desses objetos, existem três tipos de seleções:

- Contíguo

- Separado

- Região

#### <a name="scope"></a>Escopo
 O componente mais importante da seleção é garantir que o usuário saiba em que janela está trabalhando (ativação) e onde o foco está localizado (seleção). O Visual Studio amplia a funcionalidade de gerenciamento de janelas no Windows, mas o esquema de ativação é o mesmo: interagir com uma janela traz foco à janela. O Visual Studio tem dois indicadores para ativação: um para janelas de documentos e outro para janelas de ferramentas.

 Para janelas de documento, a janela ativa é indicada por uma guia de janela de documento que vem para a frente e altera sua cor de fundo:

 ![Seleção ativa de guias no Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Seleção ativa de guias**

 Para janelas de ferramentas, a janela ativa é indicada por uma alteração na cor da área da barra de título da janela da ferramenta:

 ![Seleção de janela de ferramenta ativa no Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Janela de ferramenta ativa mostrando a seleção primária de um nó**

 ![Seleção de janela de ferramentas inativas no Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Janela de ferramenta inativa, mostrando seleção latente de nó**

 Uma vez que uma janela está ativa, seu foco é indicado de acordo com os modelos de seleção descritos nesta seção das diretrizes.

#### <a name="context"></a>Contexto
 O Visual Studio foi projetado para manter um forte conceito de contexto, acompanhando onde o usuário está trabalhando. Apenas uma janela está ativa, seja uma ferramenta ou uma janela de documento. No entanto, a janela de documento mais alta sempre retém uma seleção latente. Embora o foco possa estar em uma janela de ferramenta, a janela do documento que foi ativa pela última vez exibe uma seleção, mesmo em um estado inativo. Isso é feito para manter o contexto do usuário no documento que eles estavam editando, mostrando-lhes que o Visual Studio manteve seu estado para que eles possam retornar e mudar perfeitamente entre janelas de ferramentas e janelas de documentos.

### <a name="text-selection"></a>Seleção de texto
 Os editores do Visual Studio que são estritamente texmários, como o editor de texto embutido, usam o mesmo modelo de seleção de texto e aparência descritos na página [Mouse and Pointers](/windows/desktop/uxguide/inter-mouse) das Diretrizes de Interação de Experiência do Usuário do Windows no MSDN. O foco de entrada no editor de texto é indicado por uma barra vertical chamada ponto de inserção. O ponto de inserção é um único pixel de espessura e colorido como o inverso do que aparece atrás dele. Ele pisca de acordo com a taxa definida pela configuração **de taxa de piscar cursor** na guia **Velocidade** do **applet do teclado** no painel de controle.

#### <a name="contiguous-and-disjoint-selection"></a>Seleção contígua e desarticulada
 A seleção dentro do editor de texto é apenas contígua. Seleções de texto desarticuladas não são permitidas, mas devem ser abordadas em editores de objetos gráficos. Quando o ponteiro do mouse do usuário estiver sobre uma área de texto, o cursor muda para um feixe I. Um único clique coloca o ponto de inserção no editor de texto no local do clique. Segurar o botão do mouse para baixo inicia um destaque de seleção e soltar o botão do mouse termina o destaque de seleção.

#### <a name="region-selection-box-selection"></a>Seleção da região (seleção de caixa)
 O Visual Studio suporta seleções de região no editor de texto, e isso é chamado de seleção de caixa. A seleção da caixa permite que o usuário selecione uma região de texto que não siga o fluxo de texto regular. Assim como na seleção padrão de texto, a seleção deve ser contígua. A seleção da caixa é iniciada segurando a tecla Alt enquanto arrasta com o mouse. A seleção da caixa também pode ser iniciada segurando as teclas Alt e Shift enquanto usa as teclas de seta para indicar a região de seleção. A seleção da caixa usa o destaque de seleção normal e mostra o cursor do ponto de inserção piscando no final da área de seleção.

 ![Seleção de&#41; de caixa de &#40;regional no Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Seleção de região (caixa) no Visual Studio**

#### <a name="text-selection-appearance"></a>Aparência de seleção de texto
 As cores usadas para seleção ativa e inativa no editor podem ser personalizadas. Para personalizar a aparência visual do editor, o usuário pode ir para **Ferramentas > Opções**e, em seguida, olhar em **Ambiente > Fontes e Cores > Editor de Texto**.

### <a name="graphical-selection"></a>Seleção gráfica

#### <a name="interaction"></a>Interação
 A seleção de objetos gráficos pode ser complexa e depende de uma série de fatores:

- **O modelo de seleção primária do editor.** Editores que contêm objetos gráficos também podem ser usados para editar texto ou grades. Por exemplo, o editor pode ser um editor baseado em texto que também suporta a colocação de objetos gráficos, como o designer Visual Studio XAML. O suporte a vários tipos de objetos pode afetar a forma como o usuário seleciona grupos compostos por diferentes tipos de objetos.

- **Suporte para estados de seleção primária e secundária.** Um editor pode fornecer estados de seleção primária e secundária para que os objetos possam ser editados em uníssão, alinhados entre si, redimensionados juntos, e assim por diante.

- **Suporte de edição no local.** Os editores também podem permitir que o conteúdo de seus objetos gráficos seja editado. Por exemplo, uma forma de retângulo também pode conter texto no interior que pode ser alterado pelo usuário. Além disso, esse texto poderia ser centrado ou justificado. A edição no local envolve um nível mais detalhado de interação do usuário e, portanto, requer um conjunto apropriado de pistas visuais para apresentar informações de estado ao usuário.

#### <a name="mouse-interaction"></a>Interação do mouse

|Entrada|Result|
|-----------|------------|
|Clique em um objeto não selecionado|Seleciona o objeto e exibe uma linha tracejada e alças de seleção, se o objeto for resizável.|
|Clique em um objeto selecionado|Ativa a edição no local se o objeto o suportar. Clicar fora do objeto desativa o modo de edição no local.|
|Clique duas vezes em um objeto|Abre o código atrás do objeto para edição e pode inserir um manipulador de eventos padrão, se apropriado.|
|Aponte para um objeto|Altera o ponteiro para o cursor de movimento. A aparência do objeto, como sua luminosidade ou cor, pode mudar.|
|Aponte para uma alça de seleção|Altera o ponteiro para o cursor de redimensionamento. Para objetos que suportam rotação, algumas alças de seleção podem alterar o ponteiro para um cursor rotativo à medida que o ponteiro é posicionado de forma diferente (por exemplo, movido mais longe) em relação ao cabo de seleção.|
|Arrastar|Mesmo que o objeto não esteja previamente selecionado, altera o ponteiro para o cursor de movimento e move o objeto.|
|Editor perde o foco|Desativa o modo de edição no local, embora o objeto retenha o conteúdo e a aparência que teve durante seu último estado de operação/seleção.|
|Seleção de objetos|Indicado por uma borda, linha pontilhada ou outro tratamento visualmente distinto para destacar o limite do objeto.|
|Redimensione um objeto selecionado|Indicado por alças de seleção.<br /><br /> Um objeto resizável tem oito alças, representando cada direção em que pode ser redimensionado. Podem ser utilizadas menos alças se o objeto só puder ser redimensionado em determinadas direções. Quando o usuário dimensiona um objeto até onde oito alças não seriam interativas, então quatro alças podem ser usadas. Os tamanhos das alças devem ser atrelados às métricas de borda e borda da janela com a função API **GetSystemMetrics** em tamanho proporcional à resolução do display.<br /><br /> ![Alças de redimensionamentos](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Gire um objeto selecionado|![Rodar alças](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interação com o teclado

|Entrada|Result|
|-----------|------------|
|Tab|Move o indicador de foco entre a ordem lógica dos objetos no editor. Isso pode ser da esquerda para a direita ou de cima para baixo, dependendo do valor de propriedade **do TabIndex** (ou equivalente), da ordem de criação do objeto e do propósito geral do editor. Shift+Tab inverte a direção do indicador de foco.|
|Barra de espaços|Ativa o modo de panorâmica enquanto a tecla é mantida. É necessária uma entrada adicional do mouse para panar a posição da porta de exibição.|
|Ctrl+Barra de espaços|Ativa o modo zoom enquanto a tecla é mantida. A entrada adicional do mouse é necessária para aumentar e diminuir o fator de zoom.|
|Sinal ctrl+alt+minus|Diminui o fator zoom em um nível.|
|Sinal Ctrl+Alt+Plus|Aumenta o fator zoom em um nível.|
|Shift OR Ctrl|Adiciona o objeto ao grupo de seleção. O CTRL também permite remover objetos individualmente do grupo de seleção.|
|Digite|Executa o comando padrão para o objeto (geralmente Abrir ou Editar).|
|F2|Ativa a edição no local para o objeto.|
|Teclas de direção|Move os objetos selecionados na direção da tecla de seta pressionada, em pequenos incrementos (por exemplo, 1 pixel de cada vez)|
|Teclas ctrl+seta|Move os objetos selecionados na direção da tecla de seta pressionada, em incrementos maiores (por exemplo, 10 pixels por vez)|
|Teclas shift+seta|Redimensiona os objetos selecionados na respectiva direção, em pequenos incrementos (por exemplo, 1 pixel de cada vez)|
|Teclas ctrl+shift+seta|Redimensiona os objetos selecionados na respectiva direção, em incrementos maiores (por exemplo, 10 pixels por vez)|

 Quando os usuários editam controles no lugar, pode fazer sentido que os objetos redimensionem automaticamente com a entrada do usuário. Por exemplo, se o usuário emite um controle de rótulo, então o rótulo deve crescer para exibir o texto que o usuário acabou de digitar. Se isso não for feito, o usuário deve redimensionar o controle manualmente após a edição do texto. Se o usuário tem muitos controles, isso se torna uma tarefa rotineira e improdutiva.

#### <a name="graphical-containers"></a>Recipientes gráficos
 Em alguns casos, os editores gráficos fornecem contêineres para outros objetos gráficos, como o controle do Painel de Formulários do Windows ou o controle de layout de grade no designer HTML. Se o editor fornecer recipientes para outros objetos gráficos, o seguinte modelo de seleção deve ser usado apenas para o contêiner (objetos dentro do recipiente seguem o modelo padrão conforme descrito acima):

|Entrada|Result|
|-----------|------------|
|Clique em um único clique no recipiente|Seleciona o objeto do contêiner sem selecionar diretamente nenhum dos objetos contidos. O recipiente pode ser movido e/ou redimensionado com entrada padrão de mouse e teclado (conforme descrito acima). Os objetos contidos são movidos em relação ao recipiente, mas os objetos contidos não são redimensionados a menos que também sejam selecionados diretamente.|
|Paire sobre a região de fronteira do contêiner|Transforma o mouse no cursor de movimento, indicando que o recipiente pode ser movido.|
|Arraste a região de fronteira do contêiner|Altera o mouse para o cursor de movimento e move o recipiente (e os objetos contidos dentro). O contêiner não pode ser movido sem antes ser selecionado com um único clique.|
|Clique em um único clique em um objeto dentro do recipiente|Desmarca o contêiner (se selecionado) e seleciona apenas o objeto clicado.|
|Shift+clique EM OR Ctrl+clique em um objeto contido e/ou contêiner|Adiciona o objeto clicado a um grupo de seleção ou seleção existente. Se o objeto clicado já for um membro do grupo de seleção, ele será removido do grupo de seleção.|

 Os objetos contidos devem aderir ao modelo básico de seleção, conforme descrito na seção anterior. A partir do teste de usabilidade do designer do Windows Forms, os usuários esperavam acesso perfeito aos objetos contidos sem intervir etapas (impostas pelo objeto de contenção).

#### <a name="disjoint-and-region-selections"></a>Seleções de desarticulação e região
 Os editores de objetos gráficos devem suportar seleções dedesarticuladas. Observe que este gráfico não mostra a aparência de controle do Visual Studio. Consulte [a aparência de seleção de objetos gráficos](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) para obter especificações visuais detalhadas.

 ![Seletores de desarticulação e região](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Seleção desarticulada**

 Os editores gráficos também devem fornecer seleções de região com um indicador de seleção do tipo letreiro. Se o editor gráfico suportar outros tipos de objeto (como texto), então as seleções de região podem não ser possíveis dependendo das restrições desses outros tipos de objeto.

 ![Seleção de letreiros](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Seleção de letreiros**

#### <a name="primary-and-secondary-selections"></a>Seleções primárias e secundárias
 Alguns editores de objetos gráficos permitem que o usuário edite ou alinhe objetos em grupos. Neste caso, é necessário introduzir o conceito de seleções primária e secundária. A seleção primária é o objeto ao qual todos os outros objetos respondem por operações em grupo. O objeto que o usuário seleciona primeiro se torna o controle primário, e as seleções subseqüentes se tornam as seleções secundárias. A seleção primária tem um tratamento visual distinto das seleções secundárias para indicar qual objeto é primário:

 ![Seleção primária e secundária](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Seleção primária com duas seleções secundárias**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a>Aparência de seleção de objetográfico
 As alças de seleção são quadrados desenhados em um padrão retangular ao redor da caixa delimitadora do objeto. O gráfico abaixo mostra exemplos dos vários estados que um objeto gráfico pode ter com a aparência de edição de alça, dimensionamento e edição no local. O tamanho das alças deve ser amarrado às métricas de borda e borda da janela usando a API **GetSystemMetrics.**

| Estado | Aparência | Detalhes visuais |
|-------------------------|---------------| - |
| **Não selecionado** | Padrão | ![Estado do botão padrão](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Seleção primária** | Redimensionável | ![Seleção primária com alças de redimensionamento](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Seleção primária** | Não é resizável | ![Seleção primária sem redimensionar alças](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Seleção primária** | Bloqueado | ![Seleção primária bloqueada](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Seleção secundária** | Redimensionável | ![Seleção secundária com alças de redimensionamento](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Seleção secundária** | Não é resizável | ![Seleção secundária sem redimensionar alças](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Seleção secundária** | Bloqueado | ![Seleção secundária bloqueada](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **UI ativo** | Padrão | ![UI estado ativo](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Ver modelos de seleção

#### <a name="tree-view"></a>Exibição de árvore
 A seleção em uma visualização de árvore é mostrada com um simples destaque. Se o usuário clicar em um nome de nó ou em um ícone de nó, o nó será selecionado. Os glifos triangulares à esquerda do nó expandem ou contraem o controle da árvore, mas não afetam a seleção do usuário, com uma exceção: ao desabar um nó pai quando a seleção estiver em um filho desse nó, a seleção passa para o pai.

 ![Vista típica da árvore no Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Vista típica da árvore no Visual Studio**

 As visualizações de árvores podem suportar seleções contíguas e desarticuladas, mesmo em vários níveis da árvore. Várias seleções contíguas ou desarticuladas devem ser feitas em nódulos de árvores visíveis. Se um nó é colapsado, a seleção dedesarticulada é perdida e o nó que foi colapsado obtém a seleção. Desta forma, o usuário pode ver os nódulos que serão afetados por uma operação. Quando os nós são colapsados, fica claro quais nós podem ser afetados.

 Quando um nó pai é selecionado, a operação deve se aplicar ao pai, embora possa haver casos em que faz sentido uma operação se aplicar ao pai e a todos os seus filhos. Neste caso, forneça iU adicional durante a operação, como uma caixa de seleção ou caixa de diálogo de confirmação para tornar explícita a opção "aplicar a todas as crianças" ao usuário.

##### <a name="renaming"></a>Renomear
 Se os nós na renomeação do suporte da árvore, a renomeação deve ser feita no lugar. A operação no local deve ser o padrão em todos os controles de árvores no Visual Studio. Forneça um comando de renomeação que ativa imediatamente o modo de edição no local, com a seleção de texto cobrindo o nome inteiro do nó, pronto para aceitar a entrada do usuário. Se o nó representar um arquivo, o nome do arquivo deve conter a extensão. O destaque da seleção deve incluir apenas o corpo do nome do arquivo e não a extensão.

|Entrada|Result|
|-----------|------------|
|Tecla Enter|Compromete a operação de renome: Renomear|
|Tecla Esc|Cancela a operação de renome|
|Clicando fora da região de edição no local|Compromete a operação de renome: Renomear|
|Desfazer|Fornecer fácil desfazer para cancelar a operação de renomear|

#### <a name="selection-within-lists-and-grid-controls"></a>Seleção dentro de listas e controles de grade
 O conceito-chave na seleção de listas é que ele é baseado em linha, o que significa que quando uma seleção é feita, toda a linha é selecionada como uma unidade. Em contraste, as grades podem permitir que células específicas sejam selecionadas sem afetar nenhum outro aspecto da linha. As grades também podem conter uma hierarquia de linhas aninhadas (como em um TreeGrid) que permitem que ramos inteiros da hierarquia sejam selecionados e desselecionados interagindo com as linhas-pai. A seleção em listas é mostrada por uma cor de destaque simples em toda a linha de dados. O foco é mostrado por uma borda pontilhada de um pixel em torno da linha ou célula editado atual (linha se todas as células forem somente leitura).

> [!NOTE]
> **Foco** e **seleção** são conceitos diferentes. *Foco* é uma indicação de qual elemento de IU é direcionado para receber entrada não explicitamente direcionada a outro objeto, enquanto a *seleção* refere-se ao estado de inclusão de um objeto em um conjunto de objetos nos quais as operações subsequentes podem ocorrer.

 As seleções nas listas podem ser contíguas, desarticuladas ou regionais. Quando várias seleções são permitidas, a seleção contígua e desarticulada deve ser sempre suportada, enquanto o suporte para seleções de região (caixa) é opcional. As seleções regionais são iniciadas arrastando-se no espaço branco do corpo da lista.

| Objeto | Seleção |
|--------|------------|
| Lista | Contíguo |
| Lista | Separado |
| Lista | Região |

 Clicar uma vez em uma lista seleciona a linha onde o clique ocorreu. Se o usuário clicar em uma célula de lista que suporta edição no local, a célula também será imediatamente ativada para edição no local. Caso contrário, toda a linha é imediatamente selecionada e mostra um destaque.

 Arrastando no corpo da lista faz uma de três coisas:

- Inicia uma seleção de região se a lista o suporta e o mouse-down estiver no espaço branco

- Inicia uma operação de arrastar/soltar se a célula de lista ou linha suportar ser uma fonte de arrasto

- Seleciona a linha atual

##### <a name="in-place-editing"></a>Edição no local
 Quando a edição no local é permitida, existem dois modelos básicos: controle de edição simples e seletor de propriedades. Com um simples controle de edição, o conteúdo é destacado e pronto para entrada do usuário assim que a edição no local for ativada. Quando um seletor de propriedades é implementado, o botão que invoca o seletor de propriedades é exibido uma vez que o modo de edição no local é ativado e a seleção atual não é destacada. O botão do catador deve ser justificado na cela. Para obter exemplos de edição no local, consulte a **janela de propriedades** e a lista de **tarefas** no Visual Studio.

##### <a name="keyboard-support"></a>Suporte de teclado
 O suporte ao teclado para seleção em listas e grades segue as convenções padrão do Windows:

- As teclas de seta navegam na lista, selecionando cada linha/célula à medida que o foco é movido.

- Shift + arrow realiza uma seleção contígua na direção das teclas de seta.

- Ctrl + seta seguida de alternações da barra de espaço entre adicionar e remover itens da lista da seleção, criando uma seleção dedesarticulada.

- Para grades que contêm hierarquias aninhadas, a tecla Seta direita expande uma linha pai, e a tecla Seta esquerda colapsa uma.

- A tecla Tab se move entre as células na linha atual se as células forem editáveis.

- A tecla Enter executa o comando padrão no item da lista (muitas vezes **Aberto**).

- A tecla F2 ativa a edição no local para a célula selecionada no momento.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a>Configurações de persistência e salvamento

### <a name="overview"></a>Visão geral
 Embora cada componente de software no Visual Studio seja geralmente responsável por seu próprio estado e persistência, o Visual Studio salva automaticamente as configurações em alguns casos, como com tamanhos de janelas e posições. A tabela abaixo é uma combinação de configurações salvas automaticamente e configurações que requerem um usuário explícito ou ações programadas a serem tomadas.

|Objeto|O que salvar|Quando salvar|Onde salvar|
|------------|------------------|------------------|-------------------|
|Objeto selecionável (por exemplo, uma linha de código)|Um ponto de ruptura em uma linha de código<br /><br /> Um atalho de usuário associado à linha de código|Quando o projeto é salvo|O arquivo **de opções do usuário (.suo)** para o projeto|
|caixa de diálogo|A localização do diálogo, se tivesse sido movido<br /><br /> A visualização que o usuário usou pela última vez na caixa de diálogo|Quando o diálogo se fecha<br /><br /> Quando a sessão do Visual Studio terminar|Na memória<br /><br /> Registro em **HKEY_Current_User**|
|Janela|O tamanho e a localização da janela|Quando a janela fecha<br /><br /> Quando o modo Visual Studio muda<br /><br /> Quando a sessão do Visual Studio terminar|O arquivo **de opções do usuário (.suo)** para o projeto<br /><br /> Arquivo de opções personalizadas para configurações de janela|
|Document|A seleção atual no documento<br /><br /> A visão do documento<br /><br /> Os últimos lugares que o usuário visitou|Quando o documento é salvo|O arquivo **de opções do usuário (.suo)** para o projeto|
|Project|Referências a arquivos<br /><br /> Referências a diretórios em disco<br /><br /> Referências a outros softwares<br /><br /> Componentes<br /><br /> Informações estaduais sobre o projeto em si|Quando o projeto é salvo|O arquivo de projeto|
|Solução|Referências a projetos<br /><br /> Referências a arquivos|Quando o projeto ou solução é salvo|O arquivo **solution (.sln)**|
|Configurações em **opções de > de ferramentas**|Personalizações do teclado<br /><br /> Personalizações da barra de ferramentas<br /><br /> Esquemas de cores|Quando a **caixa de diálogo Ferramentas > Opções** fecha<br /><br /> Quando a sessão do Visual Studio terminar|Registro em **HKEY_Current_User**|

 O que o usuário está fazendo e, quando está fazendo isso, dita se uma configuração está sendo salva na memória (durante a sessão), salva em disco (através de sessões como uma configuração de registro), como parte do próprio arquivo de projeto ou solução, como parte do arquivo de opções de **solução (.suo)** ou como um arquivo de configurações personalizado que só esse componente de software conhece. A tabela acima mostra vários eventos em que as configurações podem ser salvas. No entanto, há outras vezes em que você pode querer salvar o estado:

- Quando o usuário muda de local dentro de uma caixa de diálogo ou janela

- Quando o usuário transfere foco para outra janela

- Quando o usuário muda de design para modo de depuração

- Quando o usuário faz logoff de sua conta

- Quando o computador entra em hibernação ou desliga

- Quando o computador/disco rígido está prestes a ser reformado e configurado novamente

### <a name="window-configurations"></a>Configurações de janelas
 Uma configuração de janela é a apresentação básica do ambiente de desenvolvimento - é um esquema que consiste na lista de janelas de ferramentas presentes e na forma como elas são organizadas. Para janelas gerenciadas pelas janelas IDE (IDE), as informações de layout são persistidas por usuário, de modo que quando um usuário inicia o IDE, o layout da janela aparece o mesmo que quando saiu pela última vez do Visual Studio. O estado e a posição das janelas IDE são persistidos em um arquivo de opções personalizadas no formato XML. Janelas de ferramentas criadas por pacotes carregados no IDE persistem suas informações de estado no registro e podem ou não ser por usuário.

#### <a name="profile-specific-layouts"></a>Layouts específicos do perfil
 Cada perfil inclui layouts de janela de ferramentas, organizados de uma maneira familiar a personas específicas do desenvolvedor (os desenvolvedores do Visual C++ esperam ver o **Solution Explorer** no lado esquerdo do IDE, enquanto os desenvolvedores C# esperam ver o **Solution Explorer** à direita). Os layouts de janela específicos do perfil são carregados depois que o usuário escolhe um perfil na inicialização. Um autor do pacote deve determinar o layout da janela mais adequado para a experiência de seu cliente, sabendo que as alterações que o usuário faz na configuração da janela serão então persistidas.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a>Entrada de toque
 Os usuários estão cada vez mais usando produtos de desenvolvimento da Microsoft em dispositivos de toque. No entanto, existem barreiras que dificultam o uso de ferramentas de desenvolvimento em dispositivos de toque. Os usuários esperam que nossos produtos forneçam uma experiência de toque confiável e precisa. A intenção dessas diretrizes é informar as decisões sobre quais capacidades de toque incorporar e incentivar uma experiência de toque consistente em todo o Visual Studio e produtos relacionados.

### <a name="levels-of-experience"></a>Níveis de experiência
 Os seguintes níveis de experiência destinam-se a servir como um guia para ajudar as equipes a decidir quais capacidades de toque oferecer com base no nível desejado de interesse de investimento em contato.

- A **experiência básica** é para equipes que querem fornecer recursos de toque para que não haja becos sem saída ao longo de seu trabalho.

- A **experiência otimizada** é para equipes que desejam fornecer os recursos de toque mais comuns (por exemplo, aqueles normalmente disponíveis em aplicativos de navegadores de internet).

- A **experiência elevada** é para equipes que desejam adicionar recursos, como gestos ou outros recursos opcionais que podem tornar seu aplicativo amigável.

||Experiência básica|Experiência otimizada|Experiência elevada|
|-|----------------------|--------------------------|-------------------------|
|Permite que os usuários...|Corrigir código e leitura de solução/nível de projeto sem becos sem saída sem saída|Executar tarefas de manutenção, refatores e navegação|Opere em uma experiência consistente, intuitiva e fluida com confiança|
|Editor|Toque em panorâmica e seleção<br /><br /> Toque de barra de rolagem para saltar e pressionar+arrastar|Zoom de beliscão<br /><br /> Pergaminho rápido<br /><br /> Seleção<br /><br /> Fácil utilização do menu de contexto||
|Janelas de ferramentas superiores|Lista panorâmica<br /><br /> Seleção de item<br /><br /> Toque de barra de rolagem para saltar e pressionar+arrastar|Rolagem e seleção de itens fáceis||
|Windowing||Redimensionar janela<br /><br /> Acesso rápido||
|Documento bem||Fácil navegação entre arquivos abertos||
|Gestos||Certifique-se de que gestos comuns funcionem em todo o IDE|Ações baseadas em gestos<br /><br /> Suporte arrastar e soltar e designers|
|Outras considerações|||Teclado personalizado na tela|

#### <a name="gestures"></a>Gestos
 Os gestos fornecem aos usuários um atalho para comandos que, de outra forma, podem exigir uma interação mais complicada. Consulte as diretrizes do Windows sobre [gestos de toque comuns para aplicativos de desktop](/windows/desktop/wintouch/windows-touch-gestures-overview), e siga essa orientação para a maioria dos gestos, incluindo gestos simples, como panning e zoom.
