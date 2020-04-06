---
title: UX Essentials para Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c329eda477d77ab73be2ad913ac18d67ff3c08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698340"
---
# <a name="ux-essentials-for-visual-studio"></a>Fundamentos de UX para Visual Studio

## <a name="best-practices"></a>Práticas recomendadas

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Seja consistente dentro do ambiente do Visual Studio.

- Siga [os padrões](interaction-patterns-for-visual-studio.md) de interação existentes dentro da concha.

- Os recursos de design são consistentes com a linguagem visual e [os requisitos de artesanato](evaluation-tools-for-visual-studio.md)da concha.

- Use comandos e controles compartilhados quando existirem.

- Entenda a hierarquia do Visual Studio e como ela estabelece o contexto e impulsiona a interface do usuário.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Use o serviço de ambiente para fontes e cores.

- A ui deve respeitar a configuração atual [da fonte do ambiente,](fonts-and-formatting-for-visual-studio.md) a menos que esteja exposta para personalização na página Fontes e Cores na caixa de diálogo Opções.

- Os elementos de iu devem usar o [SERVIÇO VSColor,](colors-and-styling-for-visual-studio.md)usando tokens de ambiente compartilhados ou tokens específicos de recursos.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Faça todas as imagens consistentes com o novo estilo VS.

- Siga os princípios de design do Visual Studio para ícones, glifos e outros gráficos.

- Não coloque texto em elementos gráficos.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Projete a partir de uma perspectiva centrada no usuário.

- Crie o fluxo de tarefas antes que as características individuais dentro dele.

- Esteja familiarizado com seus usuários e torne esse conhecimento explícito em sua especificação.

- Ao revisar a ui, avalie a experiência completa, bem como os detalhes.

- Projete sua interface do usuário para que ela permaneça funcional e atraente, independentemente da localidade ou idioma.

## <a name="screen-resolution"></a>Resolução da tela

### <a name="minimum-resolution"></a>Resolução mínima

- A resolução mínima para o Visual Studio 2015 é **1280x720**. Isso significa que é *possível* usar o Visual Studio nesta resolução, embora possa não ser uma experiência ideal para o usuário. Não há garantia de que todos os aspectos serão utilizáveis em resoluções inferiores a 1280x720.

- A resolução alvo para o Visual Studio é **1366x768**. Esta é a resolução mais baixa na qual prometemos uma *boa* experiência de usuário.

- A altura inicial do diálogo deve ser **menor que 700 pixels,** por isso se encaixa dentro da resolução mínima do quadro IDE em 96 dpi.

### <a name="high-density-displays"></a>Displays de alta densidade
 A ui no Visual Studio deve funcionar bem em todos os fatores de dimensionamento de DPI que o Windows suporta fora da caixa: 150%, 200% e 250%.

## <a name="anti-patterns"></a>Anti-padrões
 Visual Studio contém muitos exemplos de IU que seguem nossas diretrizes e práticas recomendadas. Em um esforço para ser consistente, os desenvolvedores geralmente pegam emprestado de padrões de design de ida e primeira-feira semelhantes ao que estão construindo. Embora esta seja uma boa abordagem que nos ajuda a gerar consistência na interação do usuário e no design visual, fazemos em algumas ocasiões recursos de navios com alguns detalhes que não atendem às nossas diretrizes devido a restrições de horário ou priorização de defeitos. Nesses casos, não queremos que as equipes copiem um desses "antipadrões" porque proliferam ui ruim ou inconsistente dentro do ambiente do Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Campos/configurações necessários mostrados no estado de erro por padrão

#### <a name="feature-team-goals"></a>Objetivos da equipe de destaque

- Avise os usuários que eles adicionaram um elemento que deve ser configurado.

- Chamar a atenção do usuário para as áreas que precisam de entrada.

#### <a name="anti-pattern-solution"></a>Solução antipadrão
 Assim que o usuário iniciar uma ação e antes de concluir a tarefa, coloque imediatamente ícones de parada crítica ao lado das áreas que precisam de configuração.

#### <a name="example-manifest-designer-declarations"></a>Exemplo: Declarações de Manifest Designer
 Adicionar uma declaração à lista coloca-a imediatamente em um estado de erro, que persiste até que o usuário defina as propriedades necessárias.

 Neste caso, há uma preocupação adicional porque o ícone&times;usado para o alerta contém um ícone " " para que o ícone de remoção comum não possa ser usado ao lado dele. Como resultado, a uI usa um botão Remover, um controle mais desajeitado.

 ![Colocar a iu em um estado de erro por padrão é um anti-padrão do Visual Studio.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "Declarações de erro do ManifestDesigneranti-padrão")<br />Colocar a iu em um estado de erro por padrão é um anti-padrão do Visual Studio.

#### <a name="alternatives"></a>Alternativas

Uma solução melhor para este problema é:

- Permita que o usuário adicione uma declaração sem aviso e, em seguida, mova-se imediatamente para definir propriedades no item.

- Adicione o ícone de aviso (triângulo dourado) quando o foco se mover do item, como adicionar outra declaração à lista ou tentar alterar as guias dentro do designer.

- Se o usuário tentar alterar as guias antes de definir propriedades em quaisquer declarações, faça um diálogo explicando que o aplicativo não será construído (ou quaisquer que sejam as implicações) até que os avisos sejam resolvidos. Se o usuário descartar a caixa de diálogo e mudar as guias de qualquer maneira, um ícone (crítico ou aviso, conforme apropriado) será adicionado à guia Declarações.

### <a name="multiple-clicks-to-dismiss-ui"></a>Vários cliques para demitir a ui

#### <a name="feature-team-goals"></a>Objetivos da equipe de destaque
 Não permita que o usuário descarte a ui sem antes ver o texto de explicação.

#### <a name="anti-pattern"></a>Anti-padrão
 A equipe que insere os links de vídeo em vários lugares&times;dentro da UI VS decidiu contra o padrão comum da explicação " botão de fechamento e dica de ferramenta, conforme especificado pelo UX, e em vez disso implementou um link drop-down e "Don't show again".

#### <a name="example-video-links-in-team-explorer"></a>Exemplo: Links de vídeo no Team Explorer
Forçar o usuário a ler texto explicativo antes de descartar a ui é um anti-padrão dentro do Visual Studio. Corretamente projetados, os links de vídeo devem exibir uma dica&times;de ferramenta com informações adicionais sobre o mouse, e clicar no " deve descartar a mensagem sem necessidade de mais interação.

 ![Texto explicativo anti&#45;padrão &#45; incorreto](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Uso incorretode múltiplos cliques")<br />Padrão de link de vídeo incorreto

Em vez de um simples botão de fechamento (um clique), o usuário é forçado a usar dois cliques para simplesmente descartar a interface do usuário em todos os lugares em que os links de vídeo aparecem.

O design correto para esta situação é seguir o padrão comum ao Internet Explorer, Office e Visual Studio: no hover, o usuário pode ver a descrição da dica da ferramenta e um clique esconde a ui.

 ![Texto explicativo anti&#45;padrão &#45; correto](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatóriotextanti-padrão correto")<br />Padrão correto de link de vídeo

### <a name="using-command-bars-for-settings"></a>Usando barras de comando para configurações

**A Figura A** representa este anti-padrão: colocar uma configuração debaixo de um botão de comando que se aplica a mais do que apenas o comando. Neste esboço, há comandos além de Iniciar a depuração — como Ver no Navegador, Iniciar Sem Depuração e Passo A Passo — que respeitarão a configuração selecionada.

![Figura A: Barra de comando anti-padrão](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-pattern-FigureA")<br />Figura A: Barra de comando anti-padrão

Ligeiramente melhor, mas ainda indesejável, está colocando configurações desse tipo nas barras de ferramentas, como mostrado na **Figura B**. Embora os botões divididos tomem menos espaço e, portanto, sejam uma melhoria em relação às quedas, ambos os designs ainda estão usando uma barra de ferramentas para promover algo que não é realmente um comando.

![Figura B: Melhor, mas ainda assim uma barra de comando anti-padrão](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-pattern-FigureB")<br />Figura B: Melhor, mas ainda assim uma barra de comando anti-padrão

Na abordagem correta mostrada na **Figura C,** a configuração está vinculada a uma série de comandos. Não há nenhuma configuração global sendo definida e estamos apenas alternando entre quatro comandos. Esta é a única situação em que os comandos na barra de ferramentas são aceitáveis.

![Figura C: Uso correto do padrão da barra de comando do Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-pattern-FigureC")<br />Figura C: Uso correto do padrão da barra de comando do Visual Studio

### <a name="control-anti-patterns"></a>Controle anti-padrões
 Alguns anti-padrões são simplesmente uso incorreto ou apresentação de um controle ou grupo de controles.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Sublinhando usado como um rótulo de grupo, não um hiperlink
 Sublinhar texto deve ser usado apenas para hiperlinks.

 **Ruim:**\
 ![Texto sublinhado que não é um hiperlink é um anti-padrão do Visual Studio.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Texto sublinhado que não é um hiperlink é um anti-padrão do Visual Studio.

 **Bom:**\
 ![Estilizado corretamente, o texto não-hiperlink aparece desadornado na fonte do ambiente.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Estilizado corretamente, o texto não-hiperlink aparece desadornado na fonte do ambiente.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Clicar em uma caixa de seleção resulta em uma caixa de diálogo pop-up
 Clicar na caixa de seleção "Habilitar área de trabalho remota para todas as funções" no assistente "Publicar aplicativo do Windows Azure" traz imediatamente uma caixa de diálogo pop-up, um anti-padrão do Visual Studio. Além disso, o campo caixa de seleção não preenche com uma caixa de seleção após ser selecionado, outra interação anti-padrão.

 ![Trazer uma caixa de diálogo depois de clicar em uma caixa de seleção é um anti-padrão do Visual Studio.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />Trazer uma caixa de diálogo depois de clicar em uma caixa de seleção é um anti-padrão do Visual Studio.

### <a name="hyperlink-anti-patterns"></a>Hiperlink anti-padrões
 O exemplo a seguir contém dois anti-padrões:

1. O primeiro plano que fica vermelho no hover significa que a cor compartilhada correta do serviço de fonte não está sendo usada.

2. "Saiba mais" não é o texto apropriado para um link para um tema conceitual. O objetivo do usuário não é aprender mais, é entender as ramificações de sua escolha.

   ![Ignorar o serviço de cores e usar "Saiba mais" para hiperlinks são anti-padrões do Visual Studio.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Ignorar o serviço de cores e usar "Saiba mais" para hiperlinks são anti-padrões do Visual Studio.

**Melhor solução:** Faça a pergunta que o usuário estaria fazendo clicando no link. Por exemplo:

- Como funcionam os serviços do Windows Azure?

- Quando eu preciso de um projeto de Serviços Móveis do Windows Azure?

#### <a name="using-click-here-for-links"></a>Usando "Clique aqui" para links
 Hiperlinks devem ser auto-descritivos. É um anti-padrão para usar "Clique aqui" ou qualquer variação semelhante.

 **Ruim:** "Clique aqui para obter instruções sobre como criar um novo projeto."

 **Bom:** "Como faço para criar um novo projeto?"
