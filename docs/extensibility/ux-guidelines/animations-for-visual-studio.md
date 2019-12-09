---
title: Animações para Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f113bf8d9a77e8569126a6f0c7d96f1fe4f0eea
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825240"
---
# <a name="animations-for-visual-studio"></a>Animações para Visual Studio
## <a name="animation-fundamentals"></a>Conceitos básicos de animação

### <a name="animation-best-practices-in-visual-studio"></a>Práticas recomendadas de animação no Visual Studio
Siga estas regras para garantir que os estilos de animação consistente e fácil de usar entre o IDE do Visual Studio.

- **Seja seletivo.** Limitar as animações para aqueles que servem para propósitos específicos.

- **Medição de tempo e a velocidade são importantes** para garantir que as transições de se sentir rápida e natural:

  - Concluir a transição animada no meio de um segundo (500 milissegundos).

  - As animações que podem ocorrer com frequência precisam ser rápido o suficiente para que eles não interrupção o fluxo de trabalho do usuário. Assista a animação em um loop e ajustar o tempo até que ele parece a coisa certo.

  - Animações não devem ser tão rápido ou brusca que é difícil de entender, mas não tão lento que ele faz um impaciente a transição concluir.

  - Use o tempo de variável para enfatizar a importância. Por exemplo, ao navegar por meio de uma sequência de itens em um diagrama de classe, acelerar por transições entre os itens e mais lento para se concentrar em itens importantes.

- **Usar a atenuação de não-linear gradual** de um estado para outro, dando uma ideia do movimento calmo e natural.

- Quando possível, **usar uma animação sutil em foco** para indicar elementos interativos sob o mouse.

- Se você depende muito animações em seus recursos, em seguida **fornecem um meio para desativá-las** localmente (para todos os seus recursos) como uma opção na **Ferramentas > Opções** caixa de diálogo.

- **Apenas uma animação deve ocorrer em um horário** e transmitem apenas uma parte das informações. Mais de um objeto movendo ou tentando transmitir várias coisas pode ser confuso.

- **Sutileza é importante.** Na maioria dos casos, a animação não tem a atenção do usuário de demanda para atender sua finalidade. Alterações sutis no prazo, o sequenciamento e o comportamento podem afetar significativamente a percepção e podem fazer a diferença entre uma animação em vigor e ineficaz.

- Ao usar a animação para chamar a atenção para algo, **Certifique-se de que vale a pena interromper o usuário**do raciocínio.

- **Ao mostrar o progresso ou status** através de animação:

  - Pare de mostrar com que o movimento de progresso quando o processo subjacente não está avançando.

  - Distingue os processos indeterminados de processos de determinada.

  - Certifique-se de que uma animação tem a identificação de estados de conclusão e falha.

  - Minimize o uso de animações do efeito que mostram o status e certifique-se de que eles têm um valor real, fornecendo informações adicionais de uso real. Os exemplos incluem emergências e alterações de status transitório

#### <a name="animation-donts"></a>Não faça a animação:

- Não use pequenos movimentos (movimentação em uma superfície pequena). Prefira esmaece e é alterado ao longo de movimentação de objetos.

- Não use animações que ocorrem em uma grande área da tela. Independentemente do tamanho, esse estilo de animação é distração ao usuário.

- Não use animações não relacionados com o objeto que o usuário está atualmente concentrado em ou interagindo com.

- Não use animações que exigem interação do usuário para redefinir o estado, como forçar o usuário a responder a uma notificação de intermitente para torná-lo parar piscando. Interagir com eles de forma alguma deve ser suficiente para ignorá-las.

Para obter mais informações sobre aplicativos essas práticas recomendadas, consulte [padrões de animação](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Métricas de animação

- O sistema visivelmente deve responder a gestos do usuário em menos de 10 milissegundos.

- Transição animada deve demorar mais de 500 milissegundos para concluir.

- É uma maneira de compensar as transições que exigem tempos mais longos para separá-la em duas partes. Por exemplo, a primeira parte de uma animação poderia ser o contêiner de conteúdo vazio (até 500 milissegundos), seguido de esmaecimento o conteúdo no contêiner (até 500 milissegundos).

- Para os tempos de carregamento podem ser calculados, um indicador de progresso determinante (indicador de progresso feito em porcentagem) é preferencial.

- Para os tempos de carregamento não podem ser calculados, um indicador de ocupado, como um cursor ou uma animação de rotação incorporado (indicador de trabalho ou carregamento) é apropriado.

### <a name="animation-as-communicator"></a>Animação como o communicator
Na IU do Visual Studio, a animação funciona somente como uma ferramenta de comunicação.  Ele é usado para comunicar-se a uma variedade de informações, como alterações estruturais na interface do usuário (por exemplo, quando um menu é aberta ou fechada). Animação pode ajudar a visualizar o comportamento dependente da hora de sistemas complexos, como a visualização do progresso de instalação. Animações também podem ser usadas para atrair a atenção com alertas e notificações.

 Animações de interface do usuário de função normalmente de quatro maneiras: visualizar, atrair a atenção, simulação e tempos de resposta/indicadores de progresso.

#### <a name="visualize"></a>Visualizar
Animação pode enfatizar a natureza tridimensional de objetos e torna mais fácil para os usuários visualizar sua estrutura espacial. Para conseguir isso, a animação pode precisar girar o objeto em um círculo completo, lentamente ativá-lo e para trás, ou trazer o objeto mais próximo e ligeiramente aumentar seu tamanho para enfatizar a substituição ou o foco.

Embora objetos tridimensionais podem ser movidos com o controle de usuário, o designer deve determinar com antecedência (programaticamente ou manualmente) como a melhor animar um movimento que fornece uma compreensão melhor do objeto. Isso programado animação pode então ser ativado pelo usuário, colocando o cursor sobre o objeto, enquanto os movimentos controlado pelo usuário exigem que o usuário entender como manipular o objeto. Limitar o movimento a um único eixo ou orientação por vez; o dimensionar, girar, ou converter, mas não fazer mais de uma simultaneamente.

A categoria de visualizar inclui os aspectos dos dados, relações, estado, estrutura, a sequência e a hora.

##### <a name="data"></a>Dados
Ilustra informações complexas e de variável:

- Movendo por meio de visualizações de informações, como tabelas e gráficos

- Percorrendo uma sequência, tour guiado e paginação

- Chamada de detalhes, apontando e informações específicas de realce

- Sobreposição de detalhes e informações adicionais sobre um elemento com foco

- Metamorfose de uma representação estrutural ou organizacional para outro

- Que representa as alterações ao longo do tempo usando os controles deslizantes de tempo, vaivém giratória rodas e os controles de transporte (play, stop e pause)

##### <a name="relationships"></a>Relações

- Ilustrar como os itens estão relacionados uns aos outros ou quais itens estão relacionados a um determinado item

- Mostrar hierarquias e filho do pai ou irmão relações

- Um elemento gera outra

- Um elemento minimiza a outro elemento

- Um elemento vinculado a outro

##### <a name="state"></a>Estado

- Atualizações de conteúdo

- Seleção e o foco do usuário

- Progresso

- Erros

##### <a name="structure"></a>Estrutura

- A estrutura em um nó a dinamização

- Reorientação

- Minimizar e maximizar, ou expandir e recolher

##### <a name="sequence"></a>Sequência

- Sequência de apresentação de slides

- Folheando imagens

##### <a name="time"></a>Hora

- Mostrar alterações ao longo do tempo, o tempo decorrido e screencast

- Mover para Lixeira, desfazer e refazer

- Restaurar o estado do histórico

#### <a name="attract-attention"></a>Atrair a atenção
Se a meta é chamar a atenção do usuário para um único elemento de fora várias ou para alertar o usuário para as informações atualizadas, uma animação pode ser apropriada. Por exemplo, sua página inicial do aplicativo pode empregar um botão guia de Introdução que entra em vigor depois que a página for carregada.

Como regra, o último elemento de movimentação na tela atrai a atenção do usuário.  Em uma série de elementos animados, a atenção do usuário seguirá o último objeto de animação.

##### <a name="alert"></a>Alerta

- Alertar o usuário, atenção, mostrar o progresso

- Mostrar que algo está sendo feito corretamente ou não ou mostrar o progresso ou alterações de progresso

- Solicitar que os usuários durante uma tarefa, como encontrar mais informações online ou aprender sobre a tarefa atual

##### <a name="notifications"></a>Notificações

- Alertar o usuário sobre uma condição de erro

- Interromper o usuário para ver se gostaria de participar de algo mais

- Com cuidado, informar ao usuário que um processo foi concluído ou alterado, como quando um download for concluído.

#### <a name="simulate"></a>Simular
Esta categoria abrange relacionamento físico tem posto e dimensionalidade.

- Ilustram onde os objetos vêm do ou em que elas vão para

- Expandir e recolher ou abrir e fechar

- Ativa o movimento panorâmico, a rolagem e a página

- O empilhamento e a ordenação z

- Carrossel e accordion

- Invertendo e girando a interface do usuário

#### <a name="response-and-progress-indicators"></a>Indicadores de progresso e de resposta
Indicadores de progresso tem algumas vantagens importantes:

- Ambos os indicadores de progresso indeterminado e determinada reforçar o usuário que o sistema não falhou e está trabalhando para o problema.

- Indicadores de determinada dar ao usuário que uma ideia de quão longe a ação está em andamento, bem como uma sensação de obtenção de mais próximo até o término.

## <a name="BKMK_AnimationPatterns"></a> Padrões de animação

### <a name="overview"></a>Visão geral
As animações no Visual Studio devem atender a uma função específica sem diminuir a produtividade do usuário. Geralmente, as animações no Visual Studio devem ser:

- Pequenas e não invasiva

- Natural e realista

- Sutis e subdued

- Rápido e eficiente

- Reduzida, não com pressa

Esta ilustração mostra os estilos de animação, que é recomendável para o Visual Studio. Nenhuma animação ou animações sutis que haja o fade in / fade out, são usadas com mais frequência. Há um aplicativo limitado de animações de movimento, como expandir e contrair, posições de X e Y de alterações e rotação.

![Estilos de animação recomendados para o Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "a_VSAnimStyles 1202")<br />Estilos de animação recomendados para o Visual Studio

#### <a name="appear-and-disappear"></a>Aparecem e desaparecem
Com esse padrão, um elemento alterna entre visível para fora do modo de exibição e de volta sem uma animação de transição.

![Aparecer e desaparecer da animação](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "b_AppearAndDisappear 1202")<br />Aparecem e desaparecem animação

##### <a name="correct-usage"></a>Uso correto
Elementos de interface do usuário atualizados que precisam aparecer ou desaparecer para que o usuário não é distraído nem obstruído de instantaneamente. Além disso, as animações lentos podem ser percebidas como uma operação de arrastar do desempenho, que não ocorre com o estilo que aparecem e desaparecem.

##### <a name="incorrect-usage"></a>Uso incorreto
Casos em que interface do usuário aparece abruptamente que o usuário não tem ideia o que aconteceu e adicionar uma animação ajudaria entendimento contextual.

##### <a name="animation-properties"></a>Propriedades de animação
Geralmente, o tempo de espera é zero segundos.

##### <a name="examples"></a>Exemplos
- Ocultar automaticamente janelas de ferramentas

- Ativado pelo teclado editor de interface do usuário, como o IntelliSense e a Ajuda do parâmetro

- Regiões de código de expandir e recolher

#### <a name="fade-in-and-fade-out"></a>Deslizamento e esmaecimento
Com esse padrão, um elemento de interface do usuário faz a transição de (0% opacidade) não é visível para visível (100% de opacidade) ou vice-versa.

![Animação de deslizamento e esmaecimento](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "c_FadeInFadeOut 1202")<br />Deslizamento e esmaecimento de animação

##### <a name="correct-usage"></a>Uso correto
Com mais frequência, isso é recomendado animação da interface do usuário. Ele é um efeito sutil que adiciona o interesse sem interromper o fluxo. Em alguns casos, o usuário pode nem mesmo perceber que há uma animação, perceber um smooth e fluindo de sistema de interface do usuário.

##### <a name="animation-properties"></a>Propriedades de animação

- Opacidade inicial: 0% para o fade in, 100% de esmaecimento

- Encerrando opacidade: 100% para o fade in, 0% de esmaecimento

- Duração: autônomo de 200 milissegundos, 100 milissegundos quando usado como parte de uma sequência de animação de combinação

- Estilo de atenuação: Seno InOut

##### <a name="examples"></a>Exemplos

- Ocultar automaticamente janelas de ferramentas

- Menu Abrir e fechar

- Transições de guia de plano de fundo e primeiro plano

#### <a name="color-blend-from-a-to-b"></a>Mistura de cores da para B
Com esse padrão, um elemento de interface do usuário muda de cor A cor B.

![Cor de animação do blend](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "d_ColorBlend 1202")<br />Animação do blend de cor

##### <a name="correct-usage"></a>Uso correto
Como uma transição animada quando um elemento de interface do usuário altera a cor de um contexto ou estado para outro.

##### <a name="animation-properties"></a>Propriedades de animação

- A cor inicial: UI-specific

- Cor final: UI-specific

- Duração: autônomo de 200 milissegundos, 100 milissegundos quando usado como parte de uma sequência de animação de combinação

- Estilo de atenuação: Seno InOut

##### <a name="examples"></a>Exemplos

- Transições de estado da janela de documento (Active Directory, da última ativas e inativas)

- Transições de estado da janela de ferramentas (com foco e sem foco)

#### <a name="expand-and-contract"></a>Expandir e contrair
Com esse padrão, um elemento de interface do usuário se expande no X, Y ou ambas as direções.

![Expandir e contrair animação](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "e_ExpandContract 1202")<br />Expandir e contrair de animação

##### <a name="correct-usage"></a>Uso correto
Como uma transição animada quando um elemento de interface do usuário altera o tamanho de um contexto para outro.

##### <a name="animation-properties"></a>Propriedades de animação

- Escala x: % ou dimensão específica (em pixels)

- Dimensionamento Y: % ou dimensão específica (em pixels)

- Posição de ancoragem: geralmente o canto superior esquerdo (para idiomas da esquerda para a direita) ou o canto superior direito (para idiomas da direita para esquerda)

- Duração: autônomo de 200 milissegundos, 100 milissegundos quando usado como parte de uma sequência de animação de combinação

##### <a name="examples"></a>Exemplos

- Painel do Explorer de arquitetura de expansão e recolhimento

- Item do Visual Studio 2017 início página Expandir e recolher

#### <a name="x-y-position-change"></a>Alteração de posição X-Y
Com esse padrão, um elemento de interface do usuário altera sua posição X ou Y ou ambos.

![Alterar a posição de X-Y animação](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "f_XYPositionChange 1202")<br />Animação de alteração de posição X-Y

##### <a name="correct-usage"></a>Uso correto
Como uma transição animada para um elemento de interface do usuário altera a posição de um contexto para outro.

##### <a name="animation-properties"></a>Propriedades de animação

- Posição inicial de X e Y: UI-specific

- Terminação de X e Y posição: UI-specific

- Caminho de movimento: nenhum

- Duração: autônomo de 200 milissegundos, 100 milissegundos quando usado como parte de uma sequência de animação de combinação

- Estilo de atenuação: Seno InOut

##### <a name="example"></a>Exemplo
Reordenação de guia

#### <a name="rotate"></a>Girar
Com esse padrão, o elemento de interface do usuário gira.

![Animação de rotação do elemento de interface do usuário](../../extensibility/ux-guidelines/media/1202-g_rotate.png "g_Rotate 1202")<br />Animação de rotação do elemento de interface do usuário

##### <a name="correct-usage"></a>Uso correto
Somente para o indicador de progresso indeterminado rotação.

##### <a name="animation-properties"></a>Propriedades de animação

- Grau de rotação: 360

- Centro de rotação: intermediária do objeto

- Duração: contínua

##### <a name="example"></a>Exemplo
Indicador de progresso indeterminado (rotação)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Ações de interface do usuário de shell comuns e recomendados de animações

#### <a name="tab-open"></a>Guia aberta
![Guia animação aberta](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "h_TabOpen 1202")<br />Guia de animação aberta

- Estilo: aparecem

- Duração: zero segundos

#### <a name="tab-close"></a>Fechar Guia
![Guia animação close](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "i_TabClose 1202")<br />Animação de fechar guia

- Estilo: Alterar a posição X

- Duração: 200 milissegundos

#### <a name="tab-reorder"></a>Reordenação de guia
![Guia de animação de novo pedido no Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "j_TabReorder 1202")<br />Animação de reordenação de guia

- Estilo: Alterar a posição X

- Duração: 200 milissegundos

#### <a name="close-floating-document"></a>Fechar documento flutuante
![Fechar flutuante animação de documento](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "k_CloseFloatingDocument 1202")<br />Fechar animação flutuante do documento

- Estilo: aparecem

- Duração: 200 milissegundos

#### <a name="window-state-transition"></a>Transição de estado de janela
![Animação de transição de estado de janela](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "l_WindowStateTransition 1202")<br />Animação de transição de estado de janela

- Estilo: para ser consistente com outras janelas, permitem que o sistema operacional atual definem a animação de fechamento do documento.

- Duração: 200 milissegundos

#### <a name="menu-open"></a>Menu Abrir
![Animação de menu abrir](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "m_MenuOpen 1202")<br />Animação de abrir menu

- Estilo: fade in

- Duração: 200 milissegundos

#### <a name="menu-close"></a>Feche o menu
![Animação de menu fechar](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "n_MenuClose 1202")<br />Animação de menu fechar

- Estilo: esmaecimento

- Duração: 200 milissegundos

#### <a name="auto-hide-tool-window-reveal"></a>Revelação de janela de ferramenta de ocultamento automático
![Ocultar automaticamente animação de revelação de janela de ferramenta](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "o_AutoHideToolWindowReveal 1202")<br />Ocultar automaticamente animação de revelação de janela de ferramenta

- Estilo: aparecem

- Duração: zero segundos
