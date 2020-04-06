---
title: Animações para Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc11eb7bab69728be5ceaa55143f56e93cd1fca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698601"
---
# <a name="animations-for-visual-studio"></a>Animações para Visual Studio
## <a name="animation-fundamentals"></a>Fundamentos da animação

### <a name="animation-best-practices-in-visual-studio"></a>Melhores práticas de animação no Visual Studio
Siga essas regras para garantir estilos de animação consistentes e fáceis de usar em todo o Visual Studio IDE.

- **Seja seletivo.** Limite as animações para aquelas que servem a propósitos específicos.

- **O tempo e a velocidade são importantes** para garantir que as transições sejam rápidas e naturais:

  - Completar transições animadas dentro de meio segundo (500 milissegundos).

  - Animações que ocorreriam frequentemente precisam ser rápidas o suficiente para que não interrompam o fluxo de trabalho do usuário. Observe a animação em um loop e ajuste o tempo até que pareça certo.

  - As animações não devem ser tão rápidas ou perturbadoras que seja difícil de entender, mas não tão lenta que faça um impaciente para a transição terminar.

  - Use o tempo variável para enfatizar a importância. Por exemplo, ao navegar através de uma seqüência de itens em um diagrama de classe, acelere através de transições entre itens e, em seguida, diminua a velocidade para se concentrar em itens importantes.

- **Use uma flexibilização gradual não linear** de um estado para outro, dando uma sensação de calma e movimento natural.

- Quando possível, **use uma animação sutil no hover** para indicar elementos interativos sob o mouse.

- Se você confiar fortemente em animações em seus recursos, então **forneça um meio de desatijá-los** localmente (para todos os seus recursos) como uma opção na caixa de diálogo Ferramentas > **Opções.**

- **Apenas uma animação deve ocorrer de cada vez** e transmitir apenas uma informação. Mais de um objeto se movendo ou tentando transmitir várias coisas pode ser confuso.

- **A sutileza é importante.** Na maioria dos casos, a animação não precisa exigir atenção do usuário para servir ao seu propósito. Mudanças sutis no tempo, sequenciamento e comportamento podem afetar significativamente a percepção, e podem fazer a diferença entre uma animação eficaz e ineficaz.

- Ao usar a animação para chamar a atenção para algo, **certifique-se de que vale a pena interromper a**linha de pensamento do usuário.

- **Ao mostrar progresso ou status** através de animação:

  - Pare de mostrar movimento de progresso quando o processo subjacente não está avançando.

  - Distinguir processos indeterminados de processos determinados.

  - Certifique-se de que uma animação tenha estados de conclusão e falha identificáveis.

  - Minimize o uso de animações de efeito que mostram o status e certifique-se de que elas tenham valor real, fornecendo informações adicionais de uso real. Exemplos incluem mudanças de status transitórias e emergências

#### <a name="animation-donts"></a>Animação não:

- Não use pequenos movimentos (movimento em uma pequena pegada). Prefira desbotae e muda em vez de objetos em movimento.

- Não use animações que ocorrem sobre uma grande área de imóveis de tela. Independentemente do tamanho, este estilo de animação está distraindo o usuário.

- Não use animações não relacionadas ao objeto em que o usuário está focado ou interagindo.

- Não use animações que requerem interação do usuário para redefinir o estado, como forçar o usuário a responder a uma notificação piscando para fazê-lo parar de piscar. Interagir com eles de qualquer forma deve ser suficiente para descartá-los.

Para obter mais informações sobre aplicações para essas práticas recomendadas, consulte [padrões de animação](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Métricas de animação

- O sistema deve reagir visivelmente aos gestos do usuário em menos de 10 milissegundos.

- Transições animadas não devem levar mais de 500 milissegundos para serem concluídas.

- Uma maneira de compensar as transições que requerem tempos mais longos é separá-la em duas partes. Por exemplo, a primeira parte de uma animação pode ser o recipiente de conteúdo vazio (até 500 milissegundos), seguido pelo conteúdo desaparecendo no recipiente (até 500 milissegundos).

- Para tempos de carga que podem ser calculados, um indicador de progresso determinante (indicador de progresso por cento feito) é preferido.

- Para tempos de carga que não podem ser calculados, um indicador ocupado como um cursor ou animação giratória incorporada (indicador de carga ou trabalho) é apropriado.

### <a name="animation-as-communicator"></a>Animação como comunicador
Na Visual Studio UI, a animação funciona apenas como uma ferramenta de comunicação.  É usado para comunicar uma variedade de informações, como mudanças estruturais na ui (por exemplo, quando um menu abre ou fecha). A animação pode ajudar a visualizar o comportamento dependente do tempo de sistemas complexos, como a visualização do progresso da instalação. Animações também podem ser usadas para atrair atenção com alertas e notificações.

 As animações de IU normalmente funcionam de quatro maneiras: visualizar, atrair atenção, simular e indicadores de tempo de resposta/progresso.

#### <a name="visualize"></a>Visualizar
A animação pode enfatizar a natureza tridimensional dos objetos e facilitar a visualização de sua estrutura espacial pelos usuários. Para conseguir isso, a animação pode precisar girar o objeto em um círculo completo, girar lentamente para frente e para trás, ou aproximar o objeto e aumentar ligeiramente seu tamanho para enfatizar a capotagem ou o foco.

Embora objetos tridimensionais possam ser movidos com o controle do usuário, o designer deve determinar com antecedência (programática ou manualmente) como melhor animar um movimento que forneça uma compreensão ideal do objeto. Esta animação programada pode então ser ativada pelo usuário colocando o cursor sobre o objeto, enquanto os movimentos controlados pelo usuário exigem que o usuário entenda como manipular o objeto. Limitar o movimento a um único eixo ou orientação de cada vez; escala, rotação ou tradução, mas não faça mais de um simultaneamente.

A categoria Visualização inclui os aspectos de dados, relacionamentos, estado, estrutura, seqüência e tempo.

##### <a name="data"></a>Dados
Ilustrar informações complexas e variáveis:

- Movendo-se através de visualizações de informações como gráficos e gráficos

- Passando por uma sequência, visita guiada e paginação

- Chamando detalhes, apontando e destacando informações específicas

- Sobrepondo detalhes e informações adicionais em cima de um elemento focado

- Transformando de uma representação estrutural ou organizacional para outra

- Representando mudanças ao longo do tempo usando controles deslizantes de tempo, rodas de corrida e transporte e controles de transporte (jogar, parar e pausar)

##### <a name="relationships"></a>Relações

- Ilustre como os itens se relacionam uns com os outros ou quais itens se relacionam com um determinado item

- Mostrar hierarquias e relações pai-filho ou irmãos

- Um elemento gera outro

- Um elemento minimiza para outro elemento

- Um elemento amarrado ao outro

##### <a name="state"></a>Estado

- Atualizações de conteúdo

- Foco e seleção do usuário

- Andamento

- Errors

##### <a name="structure"></a>Estrutura

- Pivotando a estrutura em um nó

- Reorientando

- Minimizar e maximizar, ou expandir e colapsar

##### <a name="sequence"></a>Sequência

- Sequência de apresentação de slides

- Folheando imagens

##### <a name="time"></a>Hora

- Mostrar mudança ao longo do tempo, lapso de tempo e screencast

- Mova-se para o lixo, desfaça e refaça

- Restaurar estado histórico

#### <a name="attract-attention"></a>Atrair atenção
Se o objetivo é chamar a atenção do usuário para um único elemento de vários ou alertar o usuário para informações atualizadas, então uma animação pode ser apropriada. Por exemplo, sua página inicial do aplicativo pode empregar um botão 'Iniciar', que desliza no lugar após o carregamento da página.

Como regra geral, o último elemento móvel na tela atrai a atenção do usuário.  Em uma série de elementos animados, a atenção do usuário seguirá o último objeto em movimento.

##### <a name="alert"></a>Alerta

- Alerte o usuário, preste atenção, mostre progresso

- Mostre que algo está sendo feito corretamente ou incorretamente ou mostre progresso ou mudanças de progresso

- Solicitar usuários durante uma tarefa, como encontrar mais informações on-line ou aprender sobre a tarefa atual

##### <a name="notifications"></a>Notificações

- Alerte o usuário sobre uma condição de erro

- Interrompa o usuário para ver se eles gostariam de atender a outra coisa

- Informe suavemente ao usuário que um processo foi concluído ou alterado, como quando um download está concluído.

#### <a name="simulate"></a>Simular
Esta categoria abrange a fisicalidade e a dimensionalidade.

- Ilustre de onde os objetos vêm ou para onde vão

- Expandir e colapsar ou abrir e fechar

- Panorâmica, rolagem e viradas de página

- Empilhamento e z-ordering

- Carrossel e acordeom

- Invertendo e girando ui

#### <a name="response-and-progress-indicators"></a>Indicadores de resposta e progresso
Os indicadores de progresso têm algumas vantagens notáveis:

- Os indicadores de progresso determinados e indeterminados tranquilizam o usuário de que o sistema não caiu e está trabalhando no problema.

- Indicadores determinados dão ao usuário uma noção de quão longe a ação está progredindo, bem como uma sensação de se aproximar do acabamento.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a>Padrões de animação

### <a name="overview"></a>Visão geral
As animações no Visual Studio destinam-se a servir uma função específica sem prejudicar a produtividade do usuário. Geralmente, as animações no Visual Studio devem ser:

- Pequeno e discreto

- Natural e realista

- Sutil e subjugado

- Rápido e eficiente

- Relaxado, não apressado

Esta ilustração mostra os estilos de animação que recomendamos para o Visual Studio. Nenhuma animação ou animações sutis como fade in/fade out são as mais usadas. Há uma aplicação limitada de animações de movimento como expansão e contrato, mudança de posição X e Y e rotação.

![Estilos de animação recomendados para Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Estilos de animação recomendados para Visual Studio

#### <a name="appear-and-disappear"></a>Apareça e desapareça
Com este padrão, um elemento muda de visível para fora de vista e para trás sem uma animação de transição.

![Aparecer e desaparecer animação](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Aparecer e desaparecer animação

##### <a name="correct-usage"></a>Uso correto
Elementos de UI frescos que precisam aparecer ou desaparecer instantaneamente para que o usuário não esteja distraído nem obstruído. Além disso, animações em movimento lento podem ser percebidas como um arrasto de desempenho, o que não ocorrerá com o estilo de aparecer e desaparecer.

##### <a name="incorrect-usage"></a>Uso incorreto
Casos em que a ui aparece tão abruptamente que o usuário não tem ideia do que aconteceu, e adicionar uma animação ajudaria com a compreensão contextual.

##### <a name="animation-properties"></a>Propriedades de animação
O atraso de tempo geralmente é de zero segundos.

##### <a name="examples"></a>Exemplos
- Janelas de ferramentas de ocultação automática

- UI do editor ativado pelo teclado, como IntelliSense e Ajuda de Parâmetros

- Regiões de código de expansão e colapso

#### <a name="fade-in-and-fade-out"></a>Fade-in e fade-out
Com este padrão, um elemento de IU passa de não visível (0% de opacidade) para visível (100% de opacidade) ou vice-versa.

![Animação fade-in e fade-out](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Animação fade-in e fade-out

##### <a name="correct-usage"></a>Uso correto
Esta é a animação de iu mais recomendada. É um efeito sutil que adiciona interesse sem interromper o fluxo. Em alguns casos, o usuário pode nem perceber que há uma animação, percebendo um sistema de ida e baixo e fluindo.

##### <a name="animation-properties"></a>Propriedades de animação

- Opacidade inicial: 0% para desbotamento, 100% para fade-out

- Fim da opacidade: 100% para desbotamento, 0% para fade-out

- Duração: 200 milissegundos autônomos, 100 milissegundos quando usado como parte de uma seqüência de animação combinada

- Estilo de facilitação: Sine InOut

##### <a name="examples"></a>Exemplos

- Janelas de ferramentas de ocultação automática

- Menu aberto e fechado

- Transições de guia de fundo e primeiro plano

#### <a name="color-blend-from-a-to-b"></a>Mistura de cores de A a B
Com este padrão, um elemento de UI muda da cor A para a cor B.

![Animação de mistura de cores](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animação de mistura de cores

##### <a name="correct-usage"></a>Uso correto
Como uma transição animada quando um elemento de Interface do Usuário muda de cor de um contexto ou estado para outro.

##### <a name="animation-properties"></a>Propriedades de animação

- Cor inicial: Específico para ui

- Cor final: Específico para ui

- Duração: 200 milissegundos autônomos, 100 milissegundos quando usado como parte de uma seqüência de animação combinada

- Estilo de facilitação: Sine InOut

##### <a name="examples"></a>Exemplos

- Transições de estado da janela de documento (ativa, última ativa e inativa)

- Transições do estado da janela da ferramenta (focadas e desfocadas)

#### <a name="expand-and-contract"></a>Expandir e contratar
Com este padrão, um elemento de IA se expande nas direções X, Y ou ambas as direções.

![Expandir e contratar animação](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Expandir e contratar animação

##### <a name="correct-usage"></a>Uso correto
Como uma transição animada quando um elemento de Interface do UI muda de tamanho de um contexto para outro.

##### <a name="animation-properties"></a>Propriedades de animação

- X escala: % ou dimensão específica (em pixels)

- Escala y: % ou dimensão específica (em pixels)

- Posição de âncora: geralmente de alta esquerda (para línguas da esquerda para a direita) ou de centro-direita (para línguas da direita para a esquerda)

- Duração: 200 milissegundos autônomos, 100 milissegundos quando usado como parte de uma seqüência de animação combinada

##### <a name="examples"></a>Exemplos

- Painel Architecture Explorer expande e colapsa

- Item do Visual Studio 2017 Start Page expande e colapsa

#### <a name="x-y-position-change"></a>Mudança de posição X-Y
Com este padrão, um elemento de UI muda sua posição X ou Y ou ambos.

![Animação de mudança de posição X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animação de mudança de posição X-Y

##### <a name="correct-usage"></a>Uso correto
Como uma transição animada quando um elemento de Interface do UI muda de posição de um contexto para outro.

##### <a name="animation-properties"></a>Propriedades de animação

- Posição de partida X e Y: Específico para UI

- Terminando a posição X e Y: Específico para ui

- Caminho de movimento: nenhum

- Duração: 200 milissegundos autônomos, 100 milissegundos quando usado como parte de uma seqüência de animação combinada

- Estilo de facilitação: Sine InOut

##### <a name="example"></a>Exemplo
Reordenamento de guias

#### <a name="rotate"></a>Girar
Com este padrão, o elemento UI gira.

![Animação de rotação de elementos de ui](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animação de rotação de elementos de ui

##### <a name="correct-usage"></a>Uso correto
Apenas para o indicador de progresso de giro indeterminado.

##### <a name="animation-properties"></a>Propriedades de animação

- Grau de rotação: 360

- Centro de rotação: meio do objeto

- Duração: contínua

##### <a name="example"></a>Exemplo
Indicador de progresso indeterminado (giro)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Ações comuns de UI shell e animações recomendadas

#### <a name="tab-open"></a>Guia aberta
![Animação aberta de guia](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animação aberta de guia

- Estilo: appear

- Duração: zero segundos

#### <a name="tab-close"></a>Guia próxima
![Animação de fechamento de guia](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Animação de fechamento de guia

- Estilo: X mudança de posição

- Duração: 200 milissegundos

#### <a name="tab-reorder"></a>Reordenação de guias
![Animação de reordenação de guias no Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animação de reordenação de guias

- Estilo: X mudança de posição

- Duração: 200 milissegundos

#### <a name="close-floating-document"></a>Fechar documento flutuante
![Animação de documento flutuante próximo](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Animação de documento flutuante próximo

- Estilo: appear

- Duração: 200 milissegundos

#### <a name="window-state-transition"></a>Transição do estado da janela
![Animação de transição do estado da janela](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animação de transição do estado da janela

- Estilo: para ser consistente com outras janelas, deixe que o sistema operacional atual defina a animação de fechamento do documento.

- Duração: 200 milissegundos

#### <a name="menu-open"></a>Menu aberto
![Animação aberta do menu](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Animação aberta do menu

- Estilo: fade-in

- Duração: 200 milissegundos

#### <a name="menu-close"></a>Menu fechado
![Animação de fechamento do menu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Animação de fechamento do menu

- Estilo: fade-out

- Duração: 200 milissegundos

#### <a name="auto-hide-tool-window-reveal"></a>Janela de ferramenta de ocultação automática revelam
![Janela de ferramenta de ocultação automática revelam animação](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Janela de ferramenta de ocultação automática revelam animação

- Estilo: appear

- Duração: zero segundos
