---
title: Padrões comuns de controle para o Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5a1904c01f5688a00e45de7feed7ae326d9b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698707"
---
# <a name="common-control-patterns-for-visual-studio"></a>Padrões de controle comuns para Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Controles comuns

### <a name="overview"></a>Visão geral
Controles comuns compõem a maior parte da interface do usuário no Visual Studio. Os controles mais comuns usados na interface do Visual Studio devem seguir as [diretrizes de interação do Windows Desktop](/windows/desktop/uxguide/controls). Este tópico é específico do Visual Studio e abrange situações especiais ou detalhes que aumentam essas diretrizes do Windows.

#### <a name="common-controls-in-this-topic"></a>Controles comuns neste tópico

- [Barras de rolagem](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Campos de entrada](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Caixas de combinação e listas de paradas](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Caixas de seleção](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Botões](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Quadros de grupo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Botões e hiperlinks](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Modos de exibição de árvore](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Estilo visual
A primeira coisa a considerar quando os controles de estilo são se os controles serão usados em ui temático. Os controles na ia de usuário padrão são ui não temáticos e devem seguir o [estilo normal do Windows Desktop,](/windows/desktop/uxguide/controls)o que significa que eles não são re-modelados e devem aparecer em sua aparência de controle padrão.

- **Diálogos padrão (utilitário): não temáticos.** Não retemplatere. Use padrões básicos de estilo de controle.

- **Janelas de ferramentas, editores de documentos, superfícies de design e diálogos temáticos:** Use aparência temática especializada usando o serviço de cores.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a>Barras de rolagem
 As barras de rolagem devem seguir [padrões comuns de interação para barras de rolagem](/windows/desktop/Controls/about-scroll-bars) do Windows, a menos que sejam aumentadas com informações de conteúdo, como no editor de código.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Campos de entrada
 Para um comportamento típico de interação, siga as [diretrizes](/windows/desktop/uxguide/ctrl-text-boxes)do Windows Desktop para caixas de texto .

#### <a name="visual-style"></a>Estilo visual

- Os campos de entrada não devem ser estilizados em diálogos de utilidade. Use o estilo básico intrínseco ao controle.

- Os campos de entrada temáticos só devem ser usados em diálogos temáticos e janelas de ferramentas.

#### <a name="specialized-interactions"></a>Interações especializadas

- Os campos somente leitura terão um plano de fundo cinza (desativado), mas padrão (ativo).

- Os campos ** \<** necessários devem ter exigido>como marcas d'água dentro deles. Você não deve alterar a cor do fundo, exceto em situações raras.

- Validação de erros: veja [Notificações e Progresso para o Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Os campos de entrada devem ser dimensionados para se adequarem ao conteúdo, não para se adequarem à largura da janela em que são mostrados, nem para corresponder arbitrariamente ao comprimento de um campo longo, como um caminho. O comprimento pode ser uma indicação para o usuário de limitações quanto à quantidade de caracteres permitidos no campo.

     ![Comprimento de campo de entrada incorreto: é improvável que o nome seja tão longo.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Comprimento de campo de entrada incorreto: é improvável que o nome seja tão longo.

     ![Comprimento correto do campo de entrada: o campo de entrada é uma largura razoável para o conteúdo esperado.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Comprimento correto do campo de entrada: o campo de entrada é uma largura razoável para o conteúdo esperado.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Caixas de combinação e listas de paradas
Para um comportamento típico de interação, siga as diretrizes do [Windows Desktop para listas de paradas e caixas de combinação](/windows/desktop/uxguide/ctrl-drop).

#### <a name="visual-style"></a>Estilo visual

- Em diálogos de utilidade, não remodele o controle. Use o estilo básico intrínseco ao controle.

- Na ui temática, caixas de combinação e drop-downs seguem o tema padrão para os controles.

#### <a name="layout"></a>Layout
As caixas de combo e as gotas devem ser dimensionadas para se adequarao ao conteúdo, não para se adequar à largura da janela em que são mostradas, nem para corresponder arbitrariamente ao comprimento de um campo longo, como um caminho.

![Incorreto: a largura suspensa é muito longa para o conteúdo que será exibido.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Incorreto: a largura suspensa é muito longa para o conteúdo que será exibido.

![Correto: a queda é dimensionada para permitir o crescimento da tradução, mas não desnecessariamente longa.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Correto: a queda é dimensionada para permitir o crescimento da tradução, mas não desnecessariamente longa.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Caixas de seleção
Para um comportamento típico de interação, siga as diretrizes do [Windows Desktop para caixas de seleção](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Estilo visual

- Em diálogos de utilidade, não remodele o controle. Use o estilo básico intrínseco ao controle.

- Na ui temática, as caixas de seleção seguem o tema padrão para os controles.

#### <a name="specialized-interactions"></a>Interações especializadas

- A interação com uma caixa de seleção nunca deve estourar uma caixa de diálogo ou navegar para outra área.

- Alinhe as caixas de seleção com a linha de base da primeira linha de texto.

     ![Incorreto: a caixa de seleção está centrada no texto.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Incorreto: a caixa de seleção está centrada no texto.

     ![Correto: a caixa de seleção está alinhada com a primeira linha do texto.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Correto: a caixa de seleção está alinhada com a primeira linha do texto.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Botões
Para um comportamento típico de interação, siga as [diretrizes](/windows/desktop/uxguide/ctrl-radio-buttons)do Windows Desktop para botões de rádio .

#### <a name="visual-style"></a>Estilo visual
Em diálogos de utilidade, não estilize botões de rádio. Use o estilo básico intrínseco ao controle.

#### <a name="specialized-interactions"></a>Interações especializadas
Não é necessário usar um quadro de grupo para fechar opções de rádio, a menos que você precise manter a distinção de grupo em um layout apertado.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Quadros de grupo
Para um comportamento típico de interação, siga as diretrizes do [Windows Desktop para quadros de grupo](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Estilo visual
Em diálogos de utilidade, não estilize quadros de grupo. Use o estilo básico intrínseco ao controle.

#### <a name="layout"></a>Layout

- Não é necessário usar um quadro de grupo para fechar opções de rádio, a menos que você precise manter a distinção de grupo em um layout apertado.

- Nunca use um quadro de grupo para um único controle.

- Às vezes é aceitável usar uma regra horizontal em vez de um recipiente de quadro de grupo.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Controles de texto

### <a name="static-text-fields"></a>Campos de texto estáticos

Um campo de texto estático apresenta informações somente leitura e não pode ser selecionado pelo usuário. Evite usá-lo para qualquer texto que o usuário queira copiar para a área de transferência. No entanto, o texto estático somente leitura pode mudar para refletir uma mudança no estado. No exemplo abaixo, o texto estático nome de saída sob o grupo Informações altera para refletir quaisquer alterações feitas na caixa de texto Root Namespace acima dele.

Existem duas maneiras de exibir informações de texto estáticas.

O texto estático pode ser por conta própria em um diálogo sem qualquer contenção quando não há conflito de agrupamento. Decida se as linhas extras de uma caixa são realmente necessárias. Um exemplo é a exibição de um caminho de diretório sob uma seção criada por uma linha de grupo, conforme mostrado abaixo:

![Informações de texto estáticos em controles de texto](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "ExibindoStaticText.png")<br />Informações de texto estáticos em controles de texto

Em um diálogo onde existem outras áreas agrupadas e a contenção das informações ajudaria a legibilidade, e quando uma seção pode ser oculta da da dada ou mostrada (como no painel de descrição da **janela Propriedades)** ou você deseja ser consistente com a ui semelhante, coloque o texto estático dentro de uma caixa. Esta caixa de grupo deve ser `ButtonShadow`uma única regra e colorida com o :

![Texto estático na janela Propriedades](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropriedadesWindow.png")<br />Texto estático na janela Propriedades

### <a name="read-only-text-box"></a>Caixa de texto somente leitura

Isso permite que o usuário selecione o texto dentro do campo, mas não editá-lo. Estas caixas de texto são cercadas pelo `ButtonShadow` cinzel 3D usual com um preenchimento.

Uma caixa de texto pode se tornar ativa (editável) quando um usuário altera um controle associado, como verificar/desmarcar uma caixa de seleção ou selecionar/desmarcar um botão de rádio. Por exemplo, na página **Opções de ferramentas &gt; ** mostrada abaixo, a caixa de texto da página **inicial** fica ativa quando a caixa de seleção Usar **padrão** é desmarcada.

![Caixa de texto somente leitura, mostrando estados inativos e ativos](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Caixa de texto somente leitura, mostrando estados inativos e ativos

### <a name="using-text-in-dialogs"></a>Usando texto em diálogos

Principais diretrizes para texto em diálogos:

- Os rótulos para caixas de texto, caixas de lista e quadros em diálogos não temáticos começam com um verbo, têm um capital inicial apenas na primeira palavra e terminam com um cólon.

    > Os controles de texto em diálogos temáticos seguem [as diretrizes do UX da área de trabalho do Windows](/windows/desktop/uxguide/top-violations) e não tomam pontuação final, com exceção dos pontos de interrogação nos links de Ajuda.

- Os rótulos para caixas de seleção e botões de opção começam com um verbo, um capital inicial apenas na primeira palavra, e não têm pontuação final.

- Rótulos para botões, menus, itens de menu e guias têm maiúsculas iniciais em cada palavra (caso do título).

- A terminologia do rótulo deve ser consistente com rótulos semelhantes em outros diálogos.

- Se possível, mande um escritor/editor escrever ou aprovar o texto antes de ir para o desenvolvedor para implementação.

- Todos os controles devem ter etiquetas, exceto em circunstâncias especiais em que a abas é suficiente.
Use texto de ajuda quando apropriado.

### <a name="helper-text"></a>Texto auxiliar

Incluído nos diálogos para ajudar o usuário a entender o propósito da caixa de diálogo ou indicar qual ação tomar. O texto do ajudante deve ser usado somente quando necessário para evitar diálogos simples. As duas variações de texto auxiliar são diálogo e marca d'água.

Siga os locais comuns para texto de ajuda e seja seletivo na introdução de novas áreas. Os cenários comuns para texto de ajudante são:

- Texto auxiliar em diálogos, para dar uma orientação adicional sobre como interagir com um diálogo complexo.

- Texto de marca d'água em janelas ou diálogos vazios de ferramentas, para explicar por que nenhum conteúdo é visível.

- Um painel de descrição, como na parte inferior da **janela Propriedades.**

- Texto marca d'água em um editor vazio, para explicar que ação o usuário deve tomar para começar.

### <a name="dialog-helper-text"></a>Texto auxiliar de diálogo

Um designer de experiência do usuário pode ajudar a determinar quando o texto auxiliar é apropriado. O designer pode definir onde o texto auxiliar aparece, bem como seu conteúdo geral. A assistência do usuário pode escrever/editar o texto real.

### <a name="watermarks"></a>Marcas d' água

Os diálogos beneficiam-se de diretrizes ligeiramente diferentes de marca d'água. Como uma caixa de diálogo pode aparecer ocupada com muitos elementos de IU (rótulos, texto de dica, botões e outros controles `ButtonShadow`de contêiner com texto), especialmente quando aqueles aparecem em preto, as marcas d'água se destacam melhor em cinza escuro (VSColor: ). Normalmente, uma marca d'água aparece dentro de um controle `Window`como uma caixa de lista com um fundo branco (VSColor: ).

- O texto aparece em cinza `ButtonShadow`escuro (VSColor: ). No entanto, se a marca d'água aparecer em `ButtonFace`um fundo cinza médio ou outro colorido (VSColor: `WindowText`) e houver preocupação com sua legibilidade, vá com texto preto (VSColor: ).

- As marcas d'água podem ser centradas ou niveladas à esquerda. Aplique regras de design padrão ao tomar decisões de alinhamento. A marca d'água não pode ser selecionada no plano de fundo.

![Exemplo de texto da marca d'água](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Exemplo de texto da marca d'água

### <a name="context-specific-dynamic-text"></a>Texto específico de contexto (dinâmico)

O texto dinâmico pode ser usado de duas maneiras em uma ui de diálogo ou modeless: seja como um rótulo dinâmico ou como conteúdo dinâmico.

- Rótulo dinâmico: um uso comum de texto dinâmico está em painéis descritivos que oferecem mais informações para o item selecionado, como em uma caixa de diálogo que contém uma lista de elementos e propriedades para os elementos exibidos em uma grade à direita. O rótulo para a grade de propriedade pode ser dinâmico de modo que, quando um item é selecionado à esquerda, a grade à direita mostra informações para esse item específico.

- Texto dinâmico: pode ser útil em casos em que você precisa exibir informações específicas e não informações gerais dessa forma, mas deve-se tomar cuidado para não usar em excesso.

Se você quiser que os usuários tenham a capacidade de copiar as informações, o texto dinâmico deve estar em um campo de texto somente leitura.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Botões e hiperlinks

### <a name="overview"></a>Visão geral
Botões e controles de link (hiperlinks) devem seguir [as orientações básicas do Windows Desktop sobre hiperlinks](/windows/desktop/uxguide/ctrl-links) para uso, redação, dimensionamento e espaçamento.

### <a name="choosing-between-buttons-and-links"></a>Escolhendo entre botões e links
Tradicionalmente, os botões têm sido usados para ações e hiperlinks foram reservados para navegação. Botões podem ser usados em todos os casos, mas a função dos links foi expandida no Visual Studio para que botões e links sejam mais intercambiáveis em algumas condições.

Quando usar botões de comando:

- Comandos primários

- Exibindo janelas usadas para coletar entradas ou fazer escolhas, mesmo que sejam comandos secundários

- Ações destrutivas ou irreversíveis

- Botões de compromisso dentro de assistentes e fluxos de página

Evite botões de comando nas janelas das ferramentas ou se você precisar de mais de duas palavras para o rótulo. Os links podem ter rótulos mais longos.

 Quando usar links:

- Navegação para outra janela, documento ou página da Web

- Situações que requerem um rótulo mais longo ou sentença curta para descrever a intenção da ação

- Espaços apertados onde um botão sobrecarregaria a ui, desde que a ação não seja destrutiva ou irreversível

- Desenfatizando comandos secundários em situações onde há muitos comandos

#### <a name="examples"></a>Exemplos
![Links de comando usados na InfoBar seguindo uma mensagem de status](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Links de comando usados na InfoBar seguindo uma mensagem de status

![Links usados no popup CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Links usados no popup CodeLens

![Links usados para comandos secundários onde botões atrairiam muita atenção](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Links usados para comandos secundários onde botões atrairiam muita atenção

### <a name="common-buttons"></a>Botões comuns

#### <a name="text"></a>Texto
Siga as diretrizes de escrita em [texto e terminologia da UI.](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)

#### <a name="visual-style"></a>Estilo visual

##### <a name="standard-unthemed"></a>Padrão (sem tema)
A maioria dos botões no Visual Studio aparecerá em diálogos utilitários e não deve ser estilizado. Eles devem refletir a aparência padrão dos botões conforme ditado pelo sistema operacional.

##### <a name="themed"></a>Temáticos
Em alguns casos, os botões podem ser usados dentro da ui estilizada e esses botões devem ser estilizados adequadamente. Consulte [Diálogos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) para obter informações sobre controles temáticos.

### <a name="special-buttons"></a>Botões especiais

#### <a name="browse-buttons"></a>Navegar... Botões
**[Procurar...]** botões são usados em grades, diálogos e janelas de ferramentas e outros elementos de ida e outras opinas modeless. Eles exibem um catador que auxilia o usuário a preencher um valor em um controle. Há duas variações deste botão, longa e curta.

![O botão longo [Procurar...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />O botão longo [Procurar...]

![O botão elipse-only [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />O botão elipse-only [...]

Quando usar o botão curto somente para elipse:

- Se houver mais de um longo botão **[Procurar...]** em uma caixa de diálogo, como quando vários campos permitem a navegação. Use o botão curto **[...]** para evitar as chaves de acesso confusas criadas por essa situação** (&Browse** e **B&rowse** na mesma caixa de diálogo).

- Em um diálogo apertado, ou quando não há um lugar razoável para colocar o botão longo.

- Se o botão aparecer em um controle de grade.

Diretrizes para o uso do botão:

- Não use uma chave de acesso. Para acessá-lo usando o teclado, o usuário deve fazer a guia do controle adjacente. Certifique-se de que a ordem da guia é tal que qualquer botão de navegação caia imediatamente após o campo que ele irá preencher. Nunca use um sublinhado abaixo do primeiro período.

- Defina a propriedade Microsoft Active Accessibility (MSAA) **name** para **procurar...** (incluindo a elipse) para que os leitores de tela a leiam como "Procurar" e não "ponto-ponto-ponto" ou "período de período de período". Para controles gerenciados, isso significa definir a propriedade **AccessibleName.**

- Nunca use um botão ellipsis **[...]** para qualquer coisa, exceto uma ação de navegação. Por exemplo, se você precisa de um botão **[Novo...]** mas não tem espaço suficiente para o texto, então a caixa de diálogo precisa ser redesenhada.

##### <a name="sizing-and-spacing"></a>Dimensionamento e espaçamento
![Dimensionamento [Procurar...] botões: versão padrão é 75x23 pixels, versão curta é 26x23 pixels](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Dimensionamento [Procurar...] botões

![Botões de espaçamento [Procurar...]: espaçamento entre o controle relacionado e o botão padrão de Navegação de 7 pixels, espaçamento entre o controle relacionado e o curto botão Browse 5 pixels](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Botões de espaçamento [Procurar...]

#### <a name="graphical-buttons"></a>Botões gráficos
Alguns botões devem sempre usar uma imagem gráfica e nunca incluir texto para conservar espaço e evitar problemas de localização. Estes são frequentemente usados em catadores de campo e outras listas classificadas.

> [!NOTE]
> Os usuários têm que fazer a guia para esses botões (não há chaves de acesso), por isso coloque-os em uma ordem sensata. Mapeie a `name` propriedade do botão para a ação que ele leva para que os leitores de tela interpretem corretamente a ação do botão.

| Função | Botão |
| --- | --- |
| Adicionar | ![Botão gráfico "Adicionar"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Remover | ![Botão gráfico "Remover"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Adicionar todos | ![Botão gráfico "Adicionar tudo"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Remover Tudo | ![Botão gráfico "Remover tudo"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Mover para Cima | ![Botão gráfico "Move Up"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Mover para Baixo | ![Botão gráfico "Mover para baixo"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Excluir | ![Botão gráfico "Delete"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Dimensionamento e espaçamento
O dimensionamento para botões gráficos é o mesmo da versão curta do botão **[Browse...]** (26x23 pixels):

![Aparência de uma imagem gráfica no botão, com e sem cor transparente mostrando](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Aparência de uma imagem gráfica no botão, com e sem cor transparente mostrando

### <a name="hyperlinks"></a>Hiperlinks
Os hiperlinks são adequados para ações baseadas em navegação, como abrir um tópico de Ajuda, diálogo modal ou assistente. Se um hiperlink for usado para um comando, ele deve sempre exibir uma alteração visível e perceptível na ui. Em geral, ações que se comprometem com uma ação (como Salvar, Cancelar e Excluir) são melhor comunicadas usando um botão.

#### <a name="writing-style"></a>Estilo de escrita
Siga a [orientação](/windows/desktop/uxguide/text-ui)do Windows Desktop para texto de interface do usuário . Não use frases de "Saiba mais sobre", "Conte-me mais sobre" ou "Obter ajuda com isso". Em vez disso, a frase Ajude a vincular texto em termos da pergunta principal respondida pelo conteúdo da Ajuda. Por exemplo,**"Como adiciono um servidor ao Server Explorer?"**

#### <a name="visual-style"></a>Estilo visual

- Os hiperlinks devem sempre usar [o serviço VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Se um hiperlink não for estilizado corretamente, ele pisca vermelho quando ativo ou mostra uma cor diferente após ser visitado.

- Não inclua sublinhados no estado de repouso de controle, a menos que o link seja um fragmento de frase dentro de uma frase completa, como em uma marca d'água.

- Sublinhados não devem aparecer no pairo. Em vez disso, o feedback para o usuário de que o link está ativo é uma pequena mudança de cor e o cursor de link apropriado.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Vista de árvores

As visualizações de árvores fornecem uma maneira de organizar listas complexas em grupos de pais e filhos. Um usuário pode expandir ou colapsar grupos de pais para revelar ou ocultar itens subjacentes à criança. Cada item dentro de uma visualização de árvore pode ser selecionado para fornecer mais ação.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Estilo visual de visão de árvore

#### <a name="expanders"></a>Expansores
Os controles de visualização de árvores devem estar em conformidade com o design de expansor usado pelo Windows e pelo Visual Studio. Cada nó usa um controle expansor para revelar ou ocultar itens subjacentes. O uso de um controle de expansor fornece consistência para usuários que podem encontrar diferentes visualizações de árvores dentro do Windows e do Visual Studio.

![Correto: estilo adequado do nó de exibição de árvore usando um controle de expansor](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correto: estilo adequado do nó de exibição de árvore usando um controle de expansor

![Incorreto: estilo impróprio do nó de exibição de árvore](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Incorreto: estilo impróprio do nó de exibição de árvore

#### <a name="selection"></a>Seleção
Quando um nó é selecionado na exibição da árvore, o destaque deve expandir-se para toda a largura do controle de visualização da árvore. Isso ajuda os usuários a identificar claramente qual item eles selecionaram. As cores da seleção devem refletir o tema atual do Visual Studio.

![Correto: o destaque do nó selecionado se encaixa em toda a largura do controle de visualização da árvore.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correto: o destaque do nó selecionado se encaixa em toda a largura do controle de visualização da árvore.

![Incorreto: o destaque do nó selecionado não se encaixa em toda a largura do controle de visualização da árvore.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Incorreto: o destaque do nó selecionado não se encaixa em toda a largura do controle de visualização da árvore.

#### <a name="icons"></a>Ícones
Os ícones só devem ser usados em controles de visualização de árvores se eles ajudarem a identificar visualmente diferenças entre itens. Em geral, os ícones devem ser usados apenas em listas heterogêneas nas quais os ícones carregam informações para diferenciar os tipos de elementos. Em uma lista homogênea, o uso de ícones pode ser visto com freqüência como ruído e deve ser evitado. Nesse caso, o ícone de grupo (pai) pode transmitir o tipo de itens dentro dele. A exceção a esta regra seria se o ícone for dinâmico e for usado para indicar estado.

#### <a name="scroll-bars"></a>Barras de rolagem
As barras de rolagem devem estar sempre ocultas se o conteúdo se encaixar no controle de visualização da árvore. É aceitável que as barras de rolagem sejam ocultas ou semi-transparentes em uma janela rolável e apareçam quando a janela que contém a visão da árvore tiver foco, ou no pairar da própria visão da árvore.

![As barras de rolagem vertical e horizontal são exibidas porque o conteúdo excedeu os limites do controle de visualização da árvore.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />As barras de rolagem vertical e horizontal são exibidas porque o conteúdo excedeu os limites do controle de visualização da árvore.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a>Interações de visualização de árvores

#### <a name="context-menus"></a>Menus de contexto
Um nó de exibição de árvore pode revelar opções de submenu em um menu de contexto. Normalmente, isso ocorre quando um usuário clica com o botão direito ou pressiona a tecla Menu em um teclado do Windows com o item selecionado. É importante que o nó ganhe foco e seja selecionado. Isso ajuda o usuário a identificar qual item o submenu pertence.

![O item que gerou o menu de contexto ganha foco para notificar o usuário qual item foi selecionado.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />O item que gerou o menu de contexto ganha foco para notificar o usuário qual item foi selecionado.

#### <a name="keyboard"></a>Teclado
A visualização da árvore deve fornecer a capacidade de selecionar itens e expandir/colapsar os álos usando o teclado. Isso garante que a navegação atenda aos nossos requisitos de acessibilidade.

##### <a name="tree-view-control"></a>Controle de visualização de árvore
Os controles de árvore do Visual Studio devem seguir a navegação comum do teclado:

- **Seta para cima:** Selecione itens movendo-se para cima da árvore

- **Seta para baixo:** Selecione itens movendo-se para baixo da árvore

- **Seta direita:** Expanda um nó na árvore

- **Seta esquerda:** Desabar um nó na árvore

- **Digite a tecla:** Iniciar, carregar, executar item selecionado

##### <a name="trid-tree-view-and-grid-view"></a>Trípe (vista para a árvore e vista da grade)
Um controle trid é um controle complexo que contém uma visão de árvore dentro de uma grade. Expandir, entrar em colapso e navegar na árvore deve respeitar os mesmos comandos de teclado que uma exibição de árvore, com as seguintes adições:

- **Seta direita:** Expanda um nó. Depois que o nó for expandido, ele deve continuar navegando até a coluna mais próxima à direita. A navegação deve parar no final da linha.

- **Guia:** Navega até a cela mais próxima à direita.  No final da linha, a navegação continua até a próxima linha.

- **Shift + Tab:** Navega até a cela mais próxima à esquerda.  No início da linha, a navegação continua até a célula mais à direita na linha anterior.

![Um controle de trid no Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Um controle de trid no Visual Studio
