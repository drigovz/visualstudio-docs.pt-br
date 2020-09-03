---
title: Animações
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c07fb0887ae01ec917b39f5d7537d5a78fb5a4c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825351"
---
# <a name="animations-for-visual-studio"></a>Animações para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>Conceitos básicos de animação

### <a name="animation-best-practices-in-visual-studio"></a>Práticas recomendadas de animação no Visual Studio
 Siga estas regras para garantir estilos de animação consistentes e amigáveis no IDE do Visual Studio.

- **Ser seletivo.** Limite as animações para as que atendem a finalidades específicas.

- O **tempo e a velocidade são importantes** para garantir que as transições pareçam rápidas e naturais:

  - Conclua as transições animadas dentro de um semestre (500 milissegundos).

  - As animações que ocorrem com frequência precisam ser rápidas o suficiente para que não interrompam o fluxo de trabalho do usuário.

  - As animações não devem ser tão rápidas ou dissonante que seja difícil de entender, mas não tão lentas que faz com que uma impaciente para a transição seja concluída.

  - Use o tempo variável para enfatizar a importância. Por exemplo, ao navegar por uma sequência de itens em um diagrama de classe, acelere as transições entre os itens e, em seguida, reduza o foco em itens importantes.

- **Use a atenuação não linear gradual** de um estado para outro, dando uma noção de movimento calmo e natural

- Quando possível, **use uma animação sutil ao focalizar** para indicar elementos interativos sob o mouse.

- Se você depender muito das animações em seus recursos, **forneça um meio para desativá-las** localmente (para todos os seus recursos) como uma opção na caixa de diálogo **ferramentas > opções** .

- **Apenas uma animação deve ocorrer por vez** e transmitir apenas uma informação.

- **As sutilezas são importantes.** Na maioria dos casos, a animação não precisa exigir a atenção do usuário para atender à sua finalidade. Alterações sutis em tempo, sequenciamento e comportamento podem afetar significativamente a percepção e podem fazer a diferença entre uma animação efetiva e ineficaz.

- Ao usar a animação para chamar a atenção para algo, certifique-se de **que vale a pena interromper o**treinamento de pensamento do usuário.

- **Ao mostrar o progresso ou o status** por meio de animação:

  - Parar de mostrar a movimentação de progresso quando o processo subjacente não estiver avançando.

  - Distinguir processos indeterminados de processos de encerramento.

  - Verifique se uma animação tem Estados de conclusão e falha identificáveis.

  - Minimize o uso de animações de efeito que mostrem o status e certifique-se de que elas tenham valor real, fornecendo informações adicionais sobre o uso real. Exemplos incluem alterações de status transitórias e emergências

#### <a name="do-not"></a>Não:

- Use pequenos movimentos (movimento em uma superfície pequena), preferindo-se e alterações na movimentação de objetos.

- Use animações que ocorrem em uma grande área do espaço da tela. Independentemente do tamanho, esse estilo de animação está distraindo o usuário.

- Use animações que não estejam relacionadas ao objeto ao qual o usuário está focalizado ou interagindo.

- Use animações que exijam interação do usuário para redefinir o estado, como forçar o usuário a responder a uma notificação de piscar para que ele pare de piscar. Interagir com eles de qualquer forma deve ser suficiente para descartá-los.

  Para obter mais informações sobre aplicativos para essas práticas recomendadas, consulte [padrões de animação](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Métricas de animação

- O sistema deve reagir visivelmente aos gestos do usuário em menos de 10 milissegundos.

- As transições animadas não devem levar mais de 500 milissegundos para serem concluídas.

- Uma maneira de compensar as transições que exigem tempos mais longos é separá-las em duas partes; por exemplo, a primeira parte de uma animação pode ser o contêiner de conteúdo vazio (até 500 milissegundos) seguido pelo conteúdo esmaecido no contêiner (até 500 milissegundos).

- Para tempos de carregamento que podem ser calculados, um indicador de progresso de determinante (indicador de progresso percentual) é preferencial.

- Para tempos de carregamento que não podem ser calculados, um indicador ocupado, como um cursor ou uma animação giratória incorporada (indicador de carregamento ou de trabalho) é apropriado.

### <a name="animation-as-communicator"></a>Animação como Communicator
 Na interface do usuário do Visual Studio, a animação funciona apenas como uma ferramenta de comunicação.  Ele é usado para comunicar uma variedade de informações, como alterações estruturais na interface do usuário; por exemplo, quando um menu é aberto ou fechado. A animação pode ajudar a visualizar o comportamento dependente de tempo de sistemas complexos, como a visualização do progresso da instalação ou ser usada para atrair atenção com alertas e notificações.

 As animações da interface do usuário normalmente funcionam de quatro maneiras: Visualizar, atrair atenção, simular e indicar tempos de resposta/progresso.

#### <a name="visualize"></a>Visualizar
 A animação pode enfatizar a natureza tridimensional de objetos e tornar mais fácil para os usuários visualizarem sua estrutura espacial. Para fazer isso, a animação pode precisar girar o objeto em um círculo inteiro, ligá-lo lentamente e colocá-lo de forma mais aproximada e aproximar seu tamanho para enfatizar a sobreposição ou o foco.

 Embora objetos tridimensionais possam ser movidos com o controle de usuário, o designer deve determinar com antecedência (de forma programática ou manual) como animar melhor uma movimentação que fornece um entendimento ideal do objeto. Essa animação programada pode então ser ativada pelo usuário, colocando o cursor sobre o objeto, enquanto os movimentos controlados pelo usuário exigem que o usuário entenda como manipular o objeto. Limitar a movimentação para um único eixo ou orientação de cada vez; dimensione, gire ou traduza, mas não faça mais de um simultaneamente.

 A categoria Visualizar inclui os aspectos dos dados, relações, estado, estrutura, sequência e tempo.

##### <a name="data"></a>Dados
 Ilustrar informações complexas e variáveis:

- Passando por visualizações de informações como gráficos e grafos

- Percorrendo uma sequência, um tour guiado e uma paginação

- Chamando detalhes, apontando e realçando informações específicas

- Sobrepondo detalhes e informações adicionais na parte superior de um elemento focado

- Metamorfose de uma representação estrutural ou organizacional para outra

- Representando alterações ao longo do tempo usando controles deslizantes de tempo, rodas corrida-and-vaivém, e controlar transporte (Play, stop e Pause).

##### <a name="relationships"></a>Relações

- Ilustrar como os itens se relacionam uns com os outros ou quais itens estão relacionados a um determinado item.

- Mostrar hierarquias e relações pai-filho ou irmãos

- Um elemento gera outro

- Um elemento minimiza para outro elemento

- Um elemento cofuncionado para outro

##### <a name="state"></a>Estado

- Atualizações de conteúdo.

- Foco e seleção do usuário

- Progresso

- Errors

##### <a name="structure"></a>Estrutura

- Dinamizando a estrutura em um nó

- Reorientando

- Minimizar e maximizar, ou expandir e recolher

##### <a name="sequence"></a>Sequência

- Sequência de slides

- Invertendo imagens

##### <a name="time"></a>Hora

- Mostrar alteração ao longo do tempo, lapso de tempo e screencast

- Mover para lixeira, desfazer e refazer

- Restaurar Estado histórico

#### <a name="attract-attention"></a>Atraia atenção
 Se o objetivo é chamar a atenção do usuário para um único elemento de várias ou para alertar o usuário sobre as informações atualizadas, uma animação pode ser apropriada. Por exemplo, a página inicial de seus aplicativos pode empregar um botão de Introdução que os slides em vigor após o carregamento da página.

 Como regra, o último elemento de movimentação na tela atrai a atenção do usuário.  Em uma série de elementos animados, a atenção do usuário seguirá o último objeto de movimentação.

##### <a name="alert"></a>Alerta

- Alertar o usuário, obter atenção, mostrar progresso

- Mostrar que algo está sendo feito corretamente ou incorretamente ou mostrar alterações de progresso ou progresso

- Avisar os usuários durante uma tarefa, como encontrar mais informações online ou aprender sobre a tarefa atual

##### <a name="notifications"></a>Notificações

- Alertar o usuário sobre uma condição de erro

- Interromper o usuário para ver se gostaria de participar de outra coisa

- Informe com cuidado o usuário de que um processo foi concluído ou alterado, por exemplo, quando um download é concluído.

#### <a name="simulate"></a>Simular
 Essa categoria abrange a físicaidade e a dimensionalidade.

- Ilustrar de onde vêm os objetos ou de onde eles vão para

- Expandir e recolher ou abrir e fechar

- Panorâmica, rolagem e folheios de página

- Empilhamento e ordenação z

- Carrossel e acordeão

- Invertendo e girando a interface do usuário

#### <a name="response-and-progress-indicators"></a>Indicadores de resposta e progresso
 Os indicadores de progresso têm algumas vantagens notáveis:

- Os indicadores de progresso determinável e indeterminado asseguram o usuário de que o sistema não falhou e está trabalhando no problema.

- Os indicadores de deencerramento dão ao usuário uma noção do quanto a ação está progredindo, bem como uma sensação de ficar mais perto do término.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Padrões de animação

### <a name="overview"></a>Visão geral
 As animações no Visual Studio destinam-se a servir uma função específica e não atrapalham a produtividade do usuário. As características gerais de animação para aderir a incluem:

- Pequeno e não discreto

- Natural e realista

- Sutil e subdued

- Rápido e eficiente

- Relaxado, não apressado

  A ilustração a seguir mostra os estilos de animação recomendados para uso no Visual Studio. Nenhuma animação e animações sutis, como fade in/fade out, são usadas com mais frequência. Há um aplicativo limitado de animações de movimento, como expandir e recolher, alteração de posição X e Y e rotação.

  ![Estilos de animação recomendados para o Visual Studio](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202-a_VSAnimStyles")

  **Estilos de animação recomendados para o Visual Studio**

#### <a name="appear-and-disappear"></a>Aparecer e desaparecer
 Com esse padrão, um elemento alterna de visível para fora de exibição e de volta sem uma animação de transição:

 ![Aparecem&#47;animação desaparecer no Visual Studio](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202-b_AppearAndDisappear")

##### <a name="correct-usage"></a>Uso correto
 Novos elementos da interface do usuário que precisam aparecer instantaneamente ou desaparecer para que o usuário não seja distraídos nem obstruído. Além disso, animações de movimentação lentas podem ser percebidas como um arrastar de desempenho, o que não ocorrerá com o estilo aparecer e desaparecer.

##### <a name="incorrect-usage"></a>Uso incorreto
 Casos em que a interface do usuário é exibida de modo abruptamente, o usuário não tem idéia do que aconteceu e adicionar uma animação ajudaria com a compreensão contextual.

##### <a name="animation-properties"></a>Propriedades da animação
 O atraso de tempo geralmente é zero segundos.

##### <a name="examples"></a>Exemplos

- Janelas de ferramentas de ocultar automaticamente

- Interface do usuário do editor ativada por teclado, como IntelliSense e ajuda de parâmetro

- Regiões de código de expandir e recolher

#### <a name="fade-in-and-fade-out"></a>Fade-in e esmaecimento
 Com esse padrão, um elemento de interface de usuário faz a transição de não visível (opacidade de 0%) para visível (100% de opacidade) ou vice-versa:

 ![Esmaecer&#45;em&#47;esmaecer&#45;animação no Visual Studio](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202-c_FadeInFadeOut")

##### <a name="correct-usage"></a>Uso correto
 Essa é a animação de interface do usuário mais recomendada. É um efeito sutil que adiciona interesse sem interromper o fluxo. Em alguns casos, o usuário pode nem mesmo perceber que há uma animação e simplesmente percebe um sistema de interface do usuário suave e fluente.

##### <a name="animation-properties"></a>Propriedades da animação

- Opacidade inicial: 0% para fade-in, 100% para esmaecimento

- Opacidade final: 100% para fade-in, 0% para esmaecimento

- Duração: 200 milissegundos autônomos, 100 milissegundos quando usados como parte de uma sequência de animação de combinação

- Estilo de atenuação: seno de InOut

##### <a name="examples"></a>Exemplos

- Janelas de ferramentas de ocultar automaticamente

- Menu abrir e fechar

- Transições de guia em segundo plano e em primeiro plano

#### <a name="color-blend-from-a-to-b"></a>Mistura de cores de A para B
 Com esse padrão, um elemento de interface do usuário muda de cor para para cor B:

 ![Animação de mistura de cores no Visual Studio](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202-d_ColorBlend")

##### <a name="correct-usage"></a>Uso correto
 Como uma transição animada quando um elemento de interface do usuário altera a cor de um contexto ou estado para outro.

##### <a name="animation-properties"></a>Propriedades da animação

- Cor inicial: específico da interface do usuário

- Cor final: específica da interface do usuário

- Duração: 200 milissegundos autônomos, 100 milissegundos quando usados como parte de uma sequência de animação de combinação

- Estilo de atenuação: seno de InOut

##### <a name="examples"></a>Exemplos

- Transições de estado da janela de documento (ativa, última ativa e inativa)

- Transições de estado da janela de ferramentas (concentradas e sem foco)

#### <a name="expand-and-contract"></a>Expandir e contratar
 Com esse padrão, um elemento de interface do usuário se expande nas duas direções X, Y ou ambas:

 ![Expandir&#47;animação de contrato no Visual Studio](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202-e_ExpandContract")

##### <a name="correct-usage"></a>Uso correto
 Como uma transição animada quando um elemento de interface do usuário altera o tamanho de um contexto para outro.

##### <a name="animation-properties"></a>Propriedades da animação

- Escala X:% ou dimensão específica (em pixels)

- Escala Y:% ou dimensão específica (em pixels)

- Posição da âncora: geralmente no canto superior esquerdo (para idiomas da esquerda para a direita) ou superior direito (para idiomas da direita para a esquerda)

- Duração: 200 milissegundos autônomos, 100 milissegundos quando usados como parte de uma sequência de animação de combinação

##### <a name="examples"></a>Exemplos

- Expandir e recolher painel do Gerenciador de arquitetura

- Expandir e recolher item de página inicial

#### <a name="x-y-position-change"></a>Alteração da posição X-Y
 Com esse padrão, um elemento de interface do usuário altera sua posição X ou Y ou ambos:

 ![Animação de alteração de posição X&#47;Y no Visual Studio](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202-f_XYPositionChange")

##### <a name="correct-usage"></a>Uso correto
 Como uma transição animada quando um elemento de interface do usuário altera a posição de um contexto para outro.

##### <a name="animation-properties"></a>Propriedades da animação

- Posição X e Y inicial: específico da interface do usuário

- Posição X e Y final: específico da interface do usuário

- Caminho de movimento: nenhum

- Duração: 200 milissegundos autônomos, 100 milissegundos quando usados como parte de uma sequência de animação de combinação

- Estilo de atenuação: seno de InOut

##### <a name="example"></a>Exemplo
 Reordenação de guias

#### <a name="rotate"></a>Girar
 Com esse padrão, o elemento de interface do usuário gira:

 ![Girar animação no Visual Studio](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202-g_Rotate")

##### <a name="correct-usage"></a>Uso correto
 Somente para o indicador de progresso de rotação indeterminado.

##### <a name="animation-properties"></a>Propriedades da animação

- Grau de rotação: 360

- Centro de rotação: meio do objeto

- Duração: contínua

##### <a name="example"></a>Exemplo
 Indicador de progresso indeterminado (girando)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Ações de interface do usuário do Shell comuns e animações recomendadas

#### <a name="tab-open"></a>Abrir guia

- Estilo: aparece

- Duração: zero segundos

  ![Animação aberta de tabulação no Visual Studio](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202-h_TabOpen")

#### <a name="tab-close"></a>Fechamento de guia

- Estilo: alteração da posição X

- Duração: 200 milissegundos

  ![Animação de fechamento de guia no Visual Studio](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202-i_TabClose")

#### <a name="tab-reorder"></a>Reordenação da guia

- Estilo: alteração da posição X

- Duração: 200 milissegundos

  ![Reordenar animação de guia no Visual Studio](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202-j_TabReorder")

#### <a name="close-floating-document"></a>Fechar documento flutuante

- Estilo: aparece

- Duração: 200 milissegundos

  ![Fechar animação de documento flutuante no Visual Studio](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202-k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>Transição de estado da janela

- Estilo: para ser consistente com outras janelas, deixe que o sistema operacional atual defina a animação fechar documento.

- Duração: 200 milissegundos

  ![Animação de transição de estado de janela no Visual Studio](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202-l_WindowStateTransition")

#### <a name="menu-open"></a>Menu aberto

- Estilo: fade-in

- Duração: 200 milissegundos

  ![Menu abrir animação no Visual Studio](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202-m_MenuOpen")

#### <a name="menu-close"></a>Fechar menu

- Estilo: esmaecimento

- Duração: 200 milissegundos

  ![Menu fechar animação no Visual Studio](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202-n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>Revelar a janela de ferramentas automaticamente

- Estilo: aparece

- Duração: zero segundos

  ![&#45;automaticamente ocultar animação da janela de ferramentas no Visual Studio](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")
