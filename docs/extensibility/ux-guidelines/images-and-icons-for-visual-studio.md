---
title: Imagens e ícones do Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e449fb30bd95319a46d1db50da63778f6800a70
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409250"
---
# <a name="images-and-icons-for-visual-studio"></a>Imagens e ícones do Visual Studio
## <a name="BKMK_ImageUseInVisualStudio"></a>Uso de imagem no Visual Studio
 Antes de criar o trabalho artístico, considere usar as mais de 1.000 imagens na [biblioteca de imagens do Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Tipos de imagens

- **Ícones**. Imagens pequenas que aparecem em comandos, hierarquias, modelos e assim por diante. O tamanho do ícone padrão usado no Visual Studio é um PNG de 16x16. Os ícones produzidos pelo serviço de imagem geram automaticamente o formato XAML para suporte HDPI.

    > [!NOTE]
    > Embora as imagens sejam usadas no sistema de menus, você não deve criar um ícone para cada comando. Consulte [menus e comandos para o Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) para ver se o comando deve obter um ícone.

- **Miniaturas.** Imagens usadas na área de visualização de uma caixa de diálogo, como a caixa de diálogo novo projeto.

- **Imagens da caixa de diálogo.** Imagens que aparecem em caixas de diálogo ou assistentes, como elementos gráficos descritivos ou indicadores de mensagem. Use com pouca frequência e somente quando necessário para ilustrar um conceito difícil ou obter a atenção do usuário (alerta, aviso).

- **Imagens animadas.** Usado em indicadores de progresso, barras de status e caixas de diálogo de operação.

- **Cursores.** Usado para indicar se uma operação é permitida usando o mouse, onde um objeto pode ser descartado e assim por diante.

## <a name="BKMK_IconDesign"></a>Design de ícone

### <a name="overview"></a>Visão geral
 O Visual Studio usa ícones de estilo moderno, que têm uma geometria limpa e um equilíbrio de 50/50 de positivo/negativo (claro/escuro) e usam metáforas diretas e compreensíveis. Ícones cruciais de design Points Center em relação à clareza, simplificação e contexto.

- **Clareza:** concentre-se na metáfora principal que dá a um ícone seu significado e sua individualidade.

- **Simplificação:** reduza o ícone para o significado principal-obtenha o tema entre apenas os elementos necessários e nenhum sofisticações.

- **Contexto:** considere todos os aspectos da função de um ícone durante o desenvolvimento de conceito, que é crucial ao decidir quais elementos constituem a metáfora principal do ícone.

  Com ícones, há vários pontos de design a serem evitados:

- Não use ícones que significam elementos da interface do usuário, exceto quando apropriado. Escolha uma abordagem mais abstrata ou simbólica quando o elemento da interface do usuário não for comum, evidente nem exclusivo.

- Não sobrecarregar elementos comuns, como documentos, pastas, setas e a lupa. Use esses elementos somente quando for essencial para o significado do ícone. Por exemplo, a lupa voltada para a direita deve indicar somente Pesquisar, procurar e localizar.

- Embora alguns elementos de ícone herdados mantenham o uso da perspectiva, não crie novos ícones com a perspectiva, a menos que o elemento não tenha clareza sem ele.

- Não CRAM muitas informações em um ícone. Uma imagem simples que pode ser facilmente reconhecida ou aprendida como um símbolo reconhecível é muito mais útil do que uma imagem excessivamente complexa. Um ícone não pode contar toda a história.

### <a name="icon-creation"></a>Criação de ícone

#### <a name="concept-development"></a>Desenvolvimento de conceito
 O Visual Studio tem em sua interface do usuário uma ampla variedade de tipos de ícones. Considere cuidadosamente o tipo de ícone durante o desenvolvimento. Não use objetos de interface do usuário não claros ou não comuns para seus elementos Icon. Opte pelo simbólico nesses casos, como com o ícone de marca inteligente. Observe que o significado da marca abstrata à esquerda é mais óbvio do que a versão vaga, baseada na interface do usuário, à direita:

|||
|-|-|
|**Uso correto de imagens simbólicas**|**Uso incorreto de imagens simbólicas**|
|![Corrigir o ícone de marca inteligente](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Ícone de marca inteligente incorreto](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Há instâncias em que elementos de interface do usuário padrão e facilmente reconhecíveis funcionam bem para ícones. Adicionar janela é um exemplo:

|||
|-|-|
|**Elemento de interface do usuário correto em um ícone**|**Elemento de interface do usuário incorreto em um ícone**|
|![Corrigir ícone de adicionar janela](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Ícone de adição de janela incorreto](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Não use um documento como elemento base, a menos que seja essencial para o significado do ícone. Sem o elemento Document no documento de adição (abaixo), o significado é perdido, ao passo que com a atualização do elemento Document é desnecessário para comunicar o significado.

|||
|-|-|
|**Corrigir o uso do ícone de documento**|**Uso incorreto do ícone de documento**|
|![Ícone corrigir documento](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Ícone de documento incorreto](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 O conceito de "Mostrar" deve ser representado pelo ícone que melhor ilustra o que está sendo mostrado, como com o exemplo de mostrar todos os arquivos. Uma metáfora de lente pode ser usada para indicar o conceito de "exibição", se necessário, como com o exemplo de Modo de Exibição de Recursos.

|||
|-|-|
|**Mostrar**|**Exibição**|
|![Mostrar ícone](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Ícone de exibição](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 O ícone de lupa para a direita deve representar apenas Pesquisar, localizar e procurar. A variante voltada para a esquerda com o sinal de adição ou de subtração deve representar apenas ampliar/reduzir.

|||
|-|-|
|**Procurando**|**Aplicar**|
|![Ícone de pesquisa](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Ícone de zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 Em exibições de árvore, não use o ícone de pasta e um modificador. Quando disponível, use apenas o modificador.

|||
|-|-|
|**Ícones corretos de exibição de árvore**|**Ícones de exibição de árvore incorretos**|
|![Correção da exibição de &#40;árvore&#41; 1](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ícone de ![exibição &#40;de&#41; árvore correto ícone 2](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Exibição de árvore incorreta&#41; ícone &#40;1](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") modo de exibição de ![árvore incorreto ícone &#40;2&#41; ](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Detalhes do estilo

#### <a name="layout"></a>{1&gt;Layout&lt;1}
 Elementos de pilha, conforme mostrado nos ícones de 16x16 padrão:

 ![Pilha de layout para ícones 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Pilha de layout para ícones 16x16

 Os elementos de notificação de status são mais bem usados como ícones autônomos. Há contextos, no entanto, em que uma notificação deve ser empilhada no elemento base, como com o ícone tarefa concluída:

 ![Notificações autônomas no Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Ícones de notificação autônomos

 ![Ícone de tarefa concluída](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Ícone de tarefa concluída

 Os ícones de projeto são normalmente arquivos. ico que contêm vários tamanhos. A maioria dos ícones de 16x16 contém os mesmos elementos. As versões de 32x32 têm mais detalhes, incluindo o tipo de projeto quando aplicável.

 ![Ícones de projeto no Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Ícones de projeto de biblioteca de controle do Windows do VB, 16x16 e 32x32

 Centralizar um ícone dentro de seu quadro de pixel. Se isso não for possível, alinhe o ícone à parte superior e/ou à direita do quadro.

 ![Ícone centralizado dentro do quadro de pixel](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Ícone centralizado dentro do quadro de pixel

 ![Ícone alinhado à parte superior direita do quadro do pixel](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Ícone alinhado à parte superior direita do quadro

 ![Ícone centralizado e alinhado à parte superior do quadro do pixel](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Ícone centralizado e alinhado à parte superior do quadro

 Para obter o alinhamento e o equilíbrio ideais, evite obstruir o elemento base do ícone com glifos de ação. Coloque o glifo próximo à parte superior esquerda do elemento base. Ao adicionar um elemento adicional, considere o alinhamento e o equilíbrio do ícone.

|||
|-|-|
|**Corrigir alinhamento e saldo**|**Alinhamento e saldo incorretos**|
|![Corrigir o equilíbrio e o alinhamento dos ícones](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Saldo e alinhamento de ícone incorretos](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Garanta a paridade de tamanho para ícones que compartilham elementos e são usados em conjuntos. Observe que, no emparelhamento incorreto, o círculo e a seta estão superdimensionados e não correspondem.

|||
|-|-|
|**Paridade de tamanho correta**|**Paridade de tamanho incorreta**|
|![Tamanho e paridade corretos do ícone](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Tamanho e paridade de ícone incorretos](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Use linhas consistentes e pesos visuais. Avalie como o ícone que você está criando se compara a outros ícones usando uma comparação lado a lado. Nunca use o quadro 16x16 inteiro, use 15x15 ou menor. A proporção de negativo para positivo (escuro-para-claro) deve ser 50/50.

|||
|-|-|
|**Corrigir a proporção de negativo para positivo**|**Taxa incorreta de negativo para positivo**|
|![Corrigir o peso Visual para &#40;os ícones 1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Corrigir o peso Visual para &#40;os ícones 2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Corrigir o peso visual dos &#40;ícones 3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Peso Visual incorreto para ícones](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Use formas simples e comparáveis e ângulos complementares para criar seus elementos sem sacrificar a integridade do elemento. Use ângulos de 45 ° ou 90 ° onde for possível.

 ![Corrigir ângulos do ícone](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspectiva
 Mantenha o ícone claro e compreensível. Use a perspectiva e uma fonte de luz somente quando necessário. Embora o uso da perspectiva em elementos Icon deva ser evitado, alguns elementos não podem ser reconhecidos sem ele. Nesses casos, uma perspectiva estilizada comunica a clareza do elemento.

 ![perspectiva de três pontos](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />perspectiva de três pontos

 ![perspectiva de um ponto](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />perspectiva de um ponto

 A maioria dos elementos deve ser oposta ou angular à direita:

 ![Ícones angulares à direita](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Use fontes de luz somente quando adicionar a clareza necessária a um objeto.

|||
|-|-|
|**Fonte de luz correta**|**Fonte de luz incorreta**|
|![Corrigir fontes de luz para ícones](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Fontes de luz incorretas para ícones](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Use contornos apenas para melhorar a legibilidade ou para comunicar melhor a metáfora. O saldo negativo positivo (escuro-claro) deve ser 50/50.

|||
|-|-|
|**Corrigir o uso de contornos**|**Uso incorreto de contornos**|
|![Contornos corretos](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Contornos incorretos](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Tipos de ícone
 Os ícones de **shell e de barra de comandos** consistem em não mais do que três dos seguintes elementos: uma base, um modificador, uma ação ou um status.

 ![Exemplos de ícones de shell e de barra de comandos](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Exemplos de ícones de shell e de barra de comandos

 Os ícones da **barra de comandos da janela de ferramentas** consistem em não mais do que três dos seguintes elementos: uma base, um modificador, uma ação ou um status.

 ![Exemplos de ícones da barra de comandos da janela de ferramentas](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Exemplos de ícones da barra de comandos da janela de ferramentas

 Os ícones do **desambiguador de exibição de árvore** consistem em não mais do que três dos seguintes elementos: uma base, um modificador, uma ação ou um status.

 ![Exemplos de ícones de desambiguador de exibição de árvore](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Exemplos de ícones de desambiguador de exibição de árvore

 Os ícones de **taxonomia de valor baseado em estado** existem nos seguintes Estados: ativo, ativo desabilitado e inativo desabilitado.

 ![Exemplos de ícones de taxonomia de valor baseado em estado](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Exemplos de ícones de taxonomia de valor baseado em estado

 Os ícones do **IntelliSense** consistem em não mais do que três dos seguintes elementos: uma base, um modificador e um status.

 ![Exemplos de ícones do IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Exemplos de ícones do IntelliSense

 Ícones de **projetos pequenos (16x16)** não devem ter mais do que dois elementos: uma base e um modificador.

 ![Exemplos de ícones de projeto pequenos (16x16)](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![ícone &#40;de projeto&#41; 16x16 2](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![ícone &#40;de&#41; projeto 16x16 3](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Exemplos de ícones de projetos pequenos (16x16)

 Ícones de **projeto grandes (32x32)** consistem em não mais do que quatro dos seguintes elementos: uma base, um a dois modificadores e uma sobreposição de idioma.

 ![Exemplos de ícones de projeto grandes (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Exemplos de ícones de projeto grandes (32x32)

### <a name="production-details"></a>Detalhes da produção
 Todos os novos elementos da interface do usuário devem ser criados usando Windows Presentation Foundation (WPF) e todos os novos ícones para o WPF devem estar no formato PNG de 32 bits. O PNG de 24 bits é um formato herdado que não dá suporte à transparência e, portanto, não é recomendado para ícones.

 Salve a resolução em 96 DPI.

#### <a name="file-types"></a>Tipos de arquivo

- **png de 32 bits:** o formato preferencial para ícones. Um formato de arquivo de compactação de dados sem perdas que pode armazenar uma única imagem rasterizada (pixel). os arquivos PNG de 32 bits dão suporte a transparência de canal alfa, correção gama e entrelaçamento.

- **bmp de 32 bits:** para controles que não são do WPF. Também chamado de XP ou High Color, o BMP de 32 bits é um formato de imagem RGB/A, uma imagem true-color com transparência de canal alfa. O canal alfa é uma camada de transparência designada no Adobe Photoshop que é salva no bitmap como um canal de cores adicional (quarto). Um plano de fundo preto é adicionado durante a produção do trabalho artístico a todos os arquivos BMP de 32 bits para fornecer uma indicação visual rápida sobre a intensidade de cor. Este plano de fundo preto representa a área a ser mascarada na interface do usuário.

- **32-bit ico:** para ícones de projeto e Adicionar item. Todos os arquivos ICO são cor true de 32 bits com transparência de canal alfa (RGB/A). Como os arquivos ICO podem armazenar vários tamanhos e profundidades de cores, os ícones do vista geralmente estão em um formato ICO contendo tamanhos de imagem 16x16, 32x32, 48x48 e 256x256. Para exibir corretamente no Windows Explorer, os arquivos ICO devem ser salvos em profundidade de cores de 24 e 8 bits para cada tamanho de imagem.

- **XAML:** para superfícies de design e adornos do Windows. Os ícones XAML são arquivos de imagem baseados em vetor que dão suporte ao dimensionamento, rotação, arquivamento e transparência. Eles não são comuns no Visual Studio hoje, mas estão se tornando mais populares devido à sua flexibilidade.

- **ESCALÁVEIS**

- **bmp de 24 bits:** para a barra de comandos do Visual Studio. Um formato de imagem RGB true-color, BMP de 24 bits, é uma Convenção de ícones que cria uma camada de transparência usando magenta (R = 255, G = 0, B = 255) como uma chave de cor para uma camada de transparência vazada. Em um BMP de 24 bits, todas as superfícies magenta são exibidas usando a cor do plano de fundo.

- **GIF de 24 bits:** para a barra de comandos do Visual Studio. Um formato de imagem RGB True-Color que dá suporte à transparência. Os arquivos GIF costumam ser usados em animações de arte do assistente e GIF.

### <a name="icon-construction"></a>Construção de ícone
 O menor tamanho de ícone no Visual Studio é 16x16. O maior em comum uso é 32x32. Lembre-se de não preencher todo o quadro 16x16, 24x24 ou 32x32 ao criar um ícone. Legível, a construção de ícones uniformes é essencial para o reconhecimento do usuário. Siga os seguintes pontos ao criar ícones.

- Os ícones devem ser claros, compreensíveis e consistentes.

- É melhor usar os elementos de notificação de status como ícones únicos e não para empilhá-los sobre um elemento de base de ícone. Em determinados contextos, a interface do usuário pode exigir que o elemento de status seja emparelhado com um elemento base.

- Os ícones de projeto geralmente são arquivos. ico que contêm vários tamanhos. Somente os ícones 16x16, 24x24 e 32x32 estão sendo atualizados. A maioria dos ícones de 16x16 e 24x24 conterá os mesmos elementos. Os ícones de 32x32 contêm mais detalhes, incluindo o tipo de linguagem do projeto quando aplicável.

- Para ícones de 32x32, os elementos base geralmente têm uma espessura de linha de 2 pixels. Uma espessura de linha de 1 ou 2 pixels pode ser usada para elementos de detalhes. Use o melhor julgamento para determinar qual é mais adequado.

- Ter pelo menos um espaçamento de 1 pixel entre elementos para ícones de 16x16 e 24x24. Para ícones de 32x32, use o espaçamento de 2 pixels entre os elementos e entre o modificador e o elemento base.

  ![Espaçamento de elementos para ícones com tamanho de 16x16, 24x24 e 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Espaçamento de elementos para ícones com tamanho de 16x16, 24x24 e 32x32

#### <a name="color-and-accessibility"></a>Cor e acessibilidade
 As diretrizes de conformidade do Visual Studio exigem que todos os ícones do produto passem pelos requisitos de acessibilidade para cores e contraste. Isso é obtido por meio do ícone inversão e, quando você está projetando, você deve estar ciente de que eles serão invertidos programaticamente no produto.

 Para obter mais informações sobre como usar cores em ícones do Visual Studio, consulte [usando cores em imagens](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="BKMK_UsingColorInImages"></a>Usando cores em imagens

### <a name="overview"></a>Visão geral
 Os ícones no Visual Studio são basicamente monodesvios. A cor é reservada para transmitir informações específicas e nunca para decoração. A cor é usada:

- para indicar uma ação

- para alertar o usuário sobre uma notificação de status

- para designar a afiliação de idioma

- para diferenciar itens no IntelliSense

### <a name="accessibility"></a>Acessibilidade
 As diretrizes de conformidade do Visual Studio exigem que todos os ícones verificados no produto passem os requisitos de acessibilidade para cor e contraste. As cores na paleta de linguagem visual foram testadas e atendem a esses requisitos.

#### <a name="color-inversion-for-dark-themes"></a>Inversão de cor para temas escuros
 Para fazer com que os ícones apareçam com a taxa de contraste correta no tema escuro do Visual Studio, uma inversão é aplicada programaticamente. As cores deste guia foram escolhidas em parte para que elas invertam corretamente. Restrinja o uso da cor a esta paleta ou você obterá resultados imprevisíveis quando a inversão for aplicada.

 ![Exemplos de ícones que tiveram suas cores invertidas](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Exemplos de ícones que tiveram suas cores invertidas

### <a name="base-palette"></a>Paleta de base
 Todos os ícones padrão contêm três cores de base. Os ícones não contêm gradientes ou sombras projetadas, com uma ou duas exceções para ícones de ferramenta 3D.

|Uso|{1&gt;Nome&lt;1}|Valor (tema claro)|Essas|{1&gt;Exemplo&lt;1}|
|-----------|----------|---------------------------|------------|-------------|
|Plano de fundo/escuro|VS BG|424242 / 66,66,66|![Amostra 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Exemplo de paleta de base](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Primeiro plano/luz|VS FG|F0EFF1 / 240,239,241|![F0EFF1 de amostra](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Contorno|VS out|F6F6F6 / 246,246,246|![F6F6F6 de amostra](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Além das cores base, cada ícone pode conter uma cor adicional da paleta estendida.

### <a name="extended-palette"></a>Paleta estendida

#### <a name="action-modifiers"></a>Modificadores de ação
 As quatro cores abaixo indicam os tipos de ações exigidas pelos modificadores de ação:

|Uso|{1&gt;Nome&lt;1}|Valor (todos os temas)|Essas|
|-----------|----------|--------------------------|------------|
|Positivo|Ação VS verde|388A34 / 56,138,52|![388A34 de amostra](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negativo|Ação VS vermelho|A1260D/161, 38, 13|![A1260D de amostra](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutro|Azul de ação VS|00539C/0, 83156|![00539C de amostra](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Criar/novo|Ação do VS laranja|C27D1A/194156, 26|![C27D1A de amostra](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Exemplos
 O verde é usado para modificadores de ação positivos, como "Adicionar", "executar", "reproduzir" e "validar".

|||||
|-|-|-|-|
|![Ícone de execução](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Executar|![Ícone executar consulta](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")<br />Executar Consulta|![Ícone reproduzir todas as etapas](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")<br />Executar todas as etapas|![Adicionar ícone de controle](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")<br />Adicionar controle|

 O vermelho é usado para modificadores de ação negativas, como "excluir", "parar", "Cancelar" e "fechar".

|||||
|-|-|-|-|
|![Ícone Excluir relação](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")<br />Excluir Relação|![Ícone Excluir coluna](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")<br />Excluir Coluna|![Ícone de consulta de parada](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")<br />Parar consulta|![Ícone de conexão offline](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")<br />Conexão offline|

 O azul é aplicado aos modificadores de ação neutros mais comumente representados como setas, como "abrir", "Avançar", "anterior", "importar" e "exportar".

|||||
|-|-|-|-|
|![Ir para o ícone de campo](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")<br />Ir para o campo|![Ícone de check&#45;-in em lote](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")<br />Check-in em lote|![Ícone do editor de endereços](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")<br />Editor de endereço|![Ícone do editor de associação](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")<br />Editor de associação|

 O Gold escuro é usado principalmente para o modificador "New".

|||||
|-|-|-|-|
|![Ícone de novo projeto](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")<br />Novo Projeto|![Ícone criar novo grafo](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")<br />Criar novo grafo|![Ícone de novo teste de unidade](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")<br />Novo teste de unidade|![Ícone de novo item de lista](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")<br />Novo item de lista|

#### <a name="special-cases"></a>Casos especiais
 Em casos especiais, um modificador de ação colorida pode ser usado independentemente como um ícone autônomo. A cor usada para o ícone reflete as ações com as quais o ícone está associado. Esse uso é limitado a um pequeno subconjunto de ícones, incluindo:

||||||
|-|-|-|-|-|
|![Ícone de execução](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Executar|![Ícone parar](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")<br />Stop|![Ícone excluir](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")<br />Excluir|![Ícone salvar](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")<br />Salvar|![Ícone navegar para trás](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")<br />Navegação Regressiva|

### <a name="code-hierarchy-palette"></a>Paleta de hierarquia de código

#### <a name="folder"></a>Folder

|Uso|{1&gt;Nome&lt;1}|Valor (todos os temas)|Essas|{1&gt;Exemplo&lt;1}|
|-----------|----------|--------------------------|------------|-------------|
|Folders|Folder|DCB67A / 220,182,122|![DCB67A de amostra](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Ícone de cor da pasta](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Linguagens do Visual Studio
 Cada um dos idiomas ou plataformas comuns disponíveis no Visual Studio tem uma cor associada. Essas cores são usadas no ícone base ou em modificadores de idioma que aparecem no canto superior direito dos ícones compostos.

|Uso|{1&gt;Nome&lt;1}|Valor (todos os temas)|Essas|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|HTML ASP WPF azul|0095D7/0149.215|![0095D7 de amostra](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP roxo|9B4F96 / 155,79,150|![9B4F96 de amostra](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS verde (VS ação verde)|388A34 / 56,138,52|![388A34 de amostra](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|{1&gt;CSS&lt;1}|CSS vermelho|BD1E2D / 189,30,45|![BD1E2D de amostra](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|Roxo de FS|672878 / 103,40,120|![Amostra 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|Laranja do JS|F16421/241100, 33|![F16421 de amostra](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB azul (VS Action azul)|00539C/0, 83156|![00539C de amostra](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|Orange do TS|E04C06 / 224,76,6|![E04C06 de amostra](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|AJ por verde|879636 / 135,150,54|![Amostra 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Exemplos de ícones com modificadores de idioma

|||||||
|-|-|-|-|-|-|
|![Ícone de Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")<br />VB|![Ícone&#35; de C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")<br />C#|![Ícone&#43; &#43; de C](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")<br />C++|![Ícone&#35; de F](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")<br />F#|![Ícone de JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")<br />JavaScript|![Ícone do Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")<br />Python|
|![Ícone HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![Ícone do WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![Ícone ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![Ícone de CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />{1&gt;CSS&lt;1}|![Ícone do TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 Os ícones do IntelliSense usam uma paleta de cores exclusiva. Essas cores são usadas para ajudar os usuários a distinguir rapidamente entre os diferentes itens na lista de pop-ups do IntelliSense.

|Uso|{1&gt;Nome&lt;1}|Valor (todos os temas)|Essas|
|-----------|----------|--------------------------|------------|
|Classe, evento|Ação do VS laranja|C27D1A/194125, 26|![C27D1A de amostra](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Método de extensão, método, módulo, delegado|Ação VS roxa|652D90/101, 45144|![652D90 de amostra](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Campo, item de enumeração, macro, estrutura, tipo de valor Union, operador, interface|Azul de ação VS|00539C/0, 83156|![00539C de amostra](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Objeto|Ação VS verde|388A34 / 56,138,52|![388A34 de amostra](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Constante, exceção, item de enumeração, mapa, item de mapa, namespace, modelo, definição de tipo|Plano de fundo (VS BG)|424242 / 66,66,66|![Amostra 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Exemplos de ícones do IntelliSense

||||||
|-|-|-|-|-|
|![Ícone de classe IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")<br />Classe|![Ícone de evento privado do IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")<br />Evento particular|![Ícone de delegado do IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")<br />Delegado|![Ícone de amigo do método IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")<br />Método Friend|![Ícone de campo](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")<br />Campo|
|![Ícone de item de enum protegido por IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")<br />Item de enum protegido|![Ícone de objeto IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")<br />Objeto|![Ícone do modelo IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")<br />Modelo|![Ícone de atalho de exceção do IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")<br />Atalho de exceção||

### <a name="notifications"></a>Notificações
 As notificações no Visual Studio são usadas para indicar o status. A paleta de notificação usa as quatro cores a seguir, bem como opções de preenchimento de primeiro plano preto ou branco, para definir notificações com os seguintes níveis de status.

|Uso|{1&gt;Nome&lt;1}|Valor (todos os temas)|Essas|
|-----------|----------|--------------------------|------------|
|Status: neutro|Notificação azul (VS. azul)|1BA1E2/27.161.226|![1BA1E2 de amostra](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Status: positivo|Notificação verde (VS verde)|339933 / 51,153,51|![Amostra 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Status: negativo|Notificação vermelha (VS vermelho)|E51400/229, 20, 0|![E51400 de amostra](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Status: aviso|Notificação amarela (VS laranja)|FFCC00/255204, 0|![FFCC00 de amostra](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Preenchimento de primeiro plano|Notificação preta (preta)|000000 / 0,0,0|![000000 &#35;de amostra](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Preenchimento de primeiro plano|Notificação branca (branca)|FFFFFF / 255,255,255|![FFFFFF de amostra](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Exemplos de ícones de notificação

|||||
|-|-|-|-|
|![Ícone de alerta](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")<br />Alert|![Ícone de aviso](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")<br />Aviso|![Ícone concluir](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")<br />Concluído|![Ícone parar](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")<br />Stop|

### <a name="visual-studio-online"></a>Visual Studio Online
 Em geral, o Visual Studio online consiste em recursos hospedados em um navegador. A cor varia em ambientes diferentes, mas o estilo permanece o mesmo.

|Grupo|Uso|{1&gt;Nome&lt;1}|Valor (todos os temas)|Essas|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Informações preliminares|BG TFSO|656565/ 101, 101, 101|![Amostra 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|Contorno|TFSO OUT|FFFFFF / 255, 255, 255|![FFFFFF de amostra](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Napa|Informações preliminares|Branco|FFFFFF / 255, 255, 255|![FFFFFF de amostra](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Mônaco|Informações preliminares|Branco|FFFFFF / 255, 255, 255|![FFFFFF de amostra](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|{1&gt;F12&lt;1}|Informações preliminares|Branco|FFFFFF / 255, 255, 255|![FFFFFF de amostra](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|{1&gt;F12&lt;1}|Normal|Grey_Primary F12|555555 / 85, 85, 85|![Amostra 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|{1&gt;F12&lt;1}|Hover|Blue_Hover F12|2279BF/34.121.191|![2279BF de amostra](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|{1&gt;F12&lt;1}|Desabilitado|F12 LtGrey_Disabled|ABABAC/171.171.172|![ABABAC de amostra](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|{1&gt;F12&lt;1}|Plano de fundo em foco|Focalizar BG|D9EBF7 / 217,235,247|![D9EBF7 de amostra](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|{1&gt;F12&lt;1}|Plano de fundo pressionado|BG pressionado|B2D7F0 / 178,215,240|![B2D7F0 de amostra](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|{1&gt;F12&lt;1}|Contorno|VS OUT|F6F6F6 / 246,246,246|![F6F6F6 de amostra](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|{1&gt;F12&lt;1}|{1&gt;Informações&lt;1}|{1&gt;Informações&lt;1}|00BCF2/0188.242|![00BCF2 de amostra](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|{1&gt;F12&lt;1}|Aviso|Aviso|F28300 / 242,131,0|![F28300 de amostra](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|{1&gt;F12&lt;1}|Erro/negativo|Error_Negative|E81123/232, 17, 35|![E81123 de amostra](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|{1&gt;F12&lt;1}|Iniciar/positivo|Start_Positive|009E49 / 0,158,73|![009E49 de amostra](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|{1&gt;F12&lt;1}|Tipo de interrupção|Tipo de interrupção|9B4F96 / 155,79,150|![9B4F96 de amostra](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|{1&gt;F12&lt;1}|Marca de evento|Marca de evento|A51F00 / 165,31,0|![A51F00 de amostra](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|{1&gt;F12&lt;1}|Marca do usuário|Marca do usuário|F16220/241, 98, 32|![F16220 de amostra](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Exemplos de ícones do Visual Studio online

|TFS online||||
|----------------|-|-|-|
|![Ícone da equipe do TFS online](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405-49_TFSOnlineTeam")<br />Equipe online|![Ícone de informações do TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50_TFSInformation")<br />{1&gt;Informações&lt;1}|![Ícone de histórico do TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory")<br />Histórico|![Ícone de ramificação do TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405-52_TFSBranch")<br />Ramificação|

|Napa||||
|----------|-|-|-|
|![Ícone de conteúdo do Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent")<br />Conteúdo|![Ícone de email do Napa Office](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405-54_NapaOfficeMail")<br />Email do Office|![Ícone do SharePoint do Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405-55_NapaSharePoint")<br />SharePoint|![Ícone do painel de tarefas Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405-56_NapaTaskPane")<br />Painel de Tarefas|

|Mônaco||||
|------------|-|-|-|
|![Ícone de arquivos Mônaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405-57_MonacoFiles")<br />Arquivos|![Ícone de Mônaco git](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405-58_MonacoGit")<br />Git|![Ícone de pesquisa de Mônaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405-59_MonacoSearch")<br />Pesquisar|![Ícone de texto Mônaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405-60_MonacoText")<br />Texto|

|{1&gt;F12&lt;1}|||
|---------|-|-|
|![Ícone de código para F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405-61_F12PrettyCode")<br />Código Pretty|![Ícone de aviso F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405-62_F12Warning")<br />Aviso|![Ícone de emulação F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405-63_F12Emulate")<br />Emular|