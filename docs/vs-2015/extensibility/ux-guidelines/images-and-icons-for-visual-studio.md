---
title: Imagens e ícones
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 843829c56fcbd2f5c558d7c4a8b14a660a431eac
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302416"
---
# <a name="images-and-icons-for-visual-studio"></a>Imagens e ícones para o Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Uso de imagem no Visual Studio
 Antes de criar obras de arte, considere fazer uso das mais de 1.000 imagens na [Biblioteca de Imagens](https://www.microsoft.com/download/details.aspx?id=35825)do Visual Studio .

### <a name="types-of-images"></a>Tipos de imagens

- **Ícones**. Pequenas imagens que aparecem em comandos, hierarquias, modelos e assim por diante. O tamanho do ícone padrão usado no Visual Studio é um PNG 16x16. Ícones produzidos pelo serviço de imagem geram automaticamente o formato XAML para suporte a HDPI.

     **NOTA:** Enquanto as imagens são usadas no sistema de menu, você não deve criar um ícone para cada comando. Consulte [Menus e Comandos para o Visual Studio para](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) ver se seu comando deve obter um ícone.

- **Miniaturas.** Imagens usadas na área de visualização de um diálogo, como o diálogo Novo Projeto.

- **Imagens de diálogo.** Imagens que aparecem em diálogos ou assistentes, seja como gráficos descritivos ou indicadores de mensagem. Use com pouca frequência e somente quando necessário para ilustrar um conceito difícil ou ganhar a atenção do usuário (alerta, aviso).

- **Imagens animadas.** Usado em indicadores de progresso, barras de status e diálogos de operação.

- **Cursores.** Usado para indicar se uma operação é permitida usando o mouse, onde um objeto pode ser descartado, e assim por diante.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>Design de ícones

### <a name="overview"></a>Visão geral
 O Visual Studio usa ícones de estilo moderno, que têm geometria limpa e um saldo 50/50 de positivo/negativo (claro/escuro), e usam metáforas diretas e compreensíveis. Os pontos cruciais de design de ícones giram em torno da clareza, simplificação e contexto.

- **Clareza:** foco na metáfora central que dá a um ícone seu significado e individualidade.

- **Simplificação:** reduza o ícone ao seu significado central – obtenha o tema apenas com os elementos necessários e sem frescuras.

- **Contexto:** considere todos os aspectos do papel de um ícone durante o desenvolvimento do conceito, o que é crucial na hora de decidir quais elementos constituem a metáfora central do ícone.

  Com ícones, há uma série de pontos de design para evitar:

- Não use ícones que signifiquem elementos de IU, exceto quando apropriado. Escolha uma abordagem mais abstrata ou simbólica quando o elemento ui não é comum, evidente nem único.

- Não use demais elementos comuns como documentos, pastas, setas e a lupa. Use esses elementos somente quando essencial para o significado do ícone. Por exemplo, a lupa virada para a direita deve indicar apenas pesquisar, navegar e encontrar.

- Embora alguns elementos de ícones legados mantenham o uso da perspectiva, não crie novos ícones com perspectiva, a menos que o elemento não tenha clareza sem ele.

- Não enfie muita informação em um ícone. Uma imagem simples que pode ser facilmente reconhecida ou aprendida como um símbolo reconhecível é muito mais útil do que uma imagem excessivamente complexa. Um ícone não pode contar toda a história.

### <a name="icon-creation"></a>Criação de ícones

#### <a name="concept-development"></a>Desenvolvimento de conceitos
 Visual Studio tem dentro de sua UI uma grande variedade de tipos de ícones. Considere cuidadosamente o tipo de ícone durante o desenvolvimento. Não use objetos de ui não claros ou incomuns para seus elementos de ícone. Opte pelo simbólico nesses casos, como no ícone Smart Tag. Observe que o significado da tag abstrata à esquerda é mais óbvio do que a versão vaga baseada em UI à direita:

|||
|-|-|
|**Uso correto de imagens simbólicas**|**Uso incorreto de imagens simbólicas**|
|![Ícone de marca inteligente correta](../../extensibility/ux-guidelines/media/0404-01-smarttagcorrect.png "0404-01_SmartTagCorrect")|![Ícone de marca inteligente incorreta](../../extensibility/ux-guidelines/media/0404-02-smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Existem casos em que elementos de IU padrão e facilmente reconhecíveis funcionam bem para ícones. Adicionar janela é um exemplo:

|||
|-|-|
|**Corrigir o elemento de iu em um ícone**|**Elemento de iu incorreto em um ícone**|
|![Corrigir o ícone de adicionar janela](../../extensibility/ux-guidelines/media/0404-03-addwindowcorrect.png "0404-03_AddWindowCorrect")|![Ícone de oportunidade de adicionar incorreta](../../extensibility/ux-guidelines/media/0404-04-addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Não use um documento como elemento base, a menos que seja essencial para o significado do ícone. Sem o elemento de documento no Add Document (abaixo) o significado é perdido, enquanto que com o Atualizar o elemento documento é desnecessário para comunicar o significado.

|||
|-|-|
|**Uso correto do ícone de documento**|**Uso incorreto do ícone de documento**|
|![Ícone de documento correto](../../extensibility/ux-guidelines/media/0404-05-documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Ícone de documento incorreto](../../extensibility/ux-guidelines/media/0404-06-documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 O conceito de "show" deve ser representado pelo ícone que melhor ilustra o que está sendo mostrado, como com o exemplo Mostrar Todos os Arquivos. Uma metáfora de lente pode ser usada para indicar o conceito de "exibição" se necessário, como com o exemplo resource view.

|||
|-|-|
|**"Show"**|**"Ver"**|
|![Ícone do show](../../extensibility/ux-guidelines/media/0404-07-show.png "0404-07_Show")|![Exibir ícone](../../extensibility/ux-guidelines/media/0404-08-view.png "0404-08_View")|

 O ícone de lupa voltado para a direita deve representar apenas pesquisar, encontrar e navegar. A variante voltada para a esquerda com o sinal de mais ou menos deve representar apenas zoom/zoom out.

|||
|-|-|
|**"Pesquisa"**|**"Zoom"**|
|![Ícone de pesquisa](../../extensibility/ux-guidelines/media/0404-09-search.png "0404-09_Search")|![Ícone de zoom](../../extensibility/ux-guidelines/media/0404-10-zoom.png "0404-10_Zoom")|

 Nas visualizações de árvores, não use o ícone da pasta e um modificador. Quando estiver disponível, use apenas o modificador.

|||
|-|-|
|**Ícones corretos de visualização de árvore**|**Ícones de visualização de árvore incorretas**|
|![Ícone de visualização da árvore &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11-treeviewcorrect1.png "0404-11_TreeViewCorrect1") Ícone de ![visualização da árvore &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12-treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Ícone de visualização de árvore &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13-treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ícone de ![visualização incorreta da árvore &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14-treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Detalhes de estilo

#### <a name="layout"></a>Layout
 Empilhar elementos como mostrado para ícones padrão 16x16:

 ![Pilha de layout para ícones 16x16](../../extensibility/ux-guidelines/media/0404-15-layoutstack.png "0404-15_LayoutStack")

 **Pilha de layout para ícones 16x16**

 Os elementos de notificação de status são mais usados como ícones autônomos. Há contextos, no entanto, em que uma notificação deve ser empilhada no elemento base, como com o ícone Task Complete:

 ![Notificações autônomas no Visual Studio](../../extensibility/ux-guidelines/media/0404-16-standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")

 **Ícones de notificação autônoma**

 ![Ícone completo da tarefa](../../extensibility/ux-guidelines/media/0404-17-taskcomplete.png "0404-17_TaskComplete")

 **Ícone completo da tarefa**

 Os ícones do projeto são tipicamente arquivos .ico que contêm vários tamanhos. A maioria dos ícones 16x16 contém os mesmos elementos. As versões 32x32 têm mais detalhes, incluindo o tipo de projeto quando aplicável.

 ![Ícones do projeto no Visual Studio](../../extensibility/ux-guidelines/media/0404-18-iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")

 **Ícones do Projeto da Biblioteca de Controle do Windows VB, 16x16 e 32x32**

 Centrale um ícone dentro de seu quadro de pixels. Se isso não for possível, alinhe o ícone à parte superior e/ou à direita do quadro.

 ![Ícone centrado no quadro pixel](../../extensibility/ux-guidelines/media/0404-19-iconcentered.png "0404-19_IconCentered")

 **Ícone centrado no quadro pixel**

 ![Ícone alinhado ao canto superior direito do quadro pixel](../../extensibility/ux-guidelines/media/0404-20-icontopright.png "0404-20_IconTopRight")

 **Ícone alinhado ao canto superior direito do quadro**

 ![Ícone centrado e alinhado ao topo do quadro pixel](../../extensibility/ux-guidelines/media/0404-21-icontopalign.png "0404-21_IconTopAlign")

 **Ícone centrado e alinhado à parte superior do quadro**

 Para alcançar o alinhamento e o equilíbrio ideais, evite obstruir o elemento base do ícone com glifos de ação. Coloque o glifo perto do canto superior esquerdo do elemento base. Ao adicionar um elemento adicional, considere o alinhamento e o equilíbrio do ícone.

|||
|-|-|
|**Alinhamento e equilíbrio corretos**|**Alinhamento e equilíbrio incorretos**|
|![Correto equilíbrio e alinhamento de ícones](../../extensibility/ux-guidelines/media/0404-22-alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Equilíbrio e alinhamento de ícones incorretos](../../extensibility/ux-guidelines/media/0404-23-alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Certifique-se de paridade de tamanho para ícones que compartilham elementos e são usados em conjuntos. Observe que no emparelhamento incorreto, o círculo e a seta são superdimensionados e não correspondem.

|||
|-|-|
|**Paridade de tamanho correta**|**Paridade de tamanho incorreta**|
|![Tamanho e paridade corretos do ícone](../../extensibility/ux-guidelines/media/0404-24-sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Tamanho e paridade de ícones incorretos](../../extensibility/ux-guidelines/media/0404-25-sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Use linhas consistentes e pesos visuais. Avalie como o ícone que você está construindo se compara a outros ícones usando uma comparação lado a lado. Nunca use todo o quadro 16x16, use 15x15 ou menor. A razão negativo-positivo (escuro para a luz) deve ser de 50/50.

|||
|-|-|
|**Corrigida relação negativo-positivo**|**Relação negativa/positiva incorreta**|
|![Peso visual correto para ícones &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26-visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Peso visual correto para ícones &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27-visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Peso visual correto para ícones &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28-visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Peso visual incorreto para ícones](../../extensibility/ux-guidelines/media/0404-29-visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Use formas simples e comparáveis e ângulos complementares para construir seus elementos sem sacrificar a integridade do elemento. Use ângulos de 45° ou 90° sempre que possível.

 ![Ângulos de ícone corretos](../../extensibility/ux-guidelines/media/0404-30-iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspectiva
 Mantenha o ícone claro e compreensível. Use a perspectiva e uma fonte de luz somente quando necessário. Embora o uso da perspectiva sobre elementos de ícones deve ser evitado, alguns elementos são irreconhecíveis sem ele. Nesses casos, uma perspectiva estilizada comunica a clareza do elemento.

 ![Perspectiva de ponto de&#45;3](../../extensibility/ux-guidelines/media/0404-31-3pointperspective.png "0404-31_3PointPerspective")

 **Perspectiva de 3 pontos**

 ![Perspectiva de 1 ponto de&#45;](../../extensibility/ux-guidelines/media/0404-32-1pointperspective.png "0404-32_1PointPerspective")

 **Perspectiva de 1 ponto**

 A maioria dos elementos deve estar virada ou inclinada para a direita.

 ![Ícones angulados à direita](../../extensibility/ux-guidelines/media/0404-33-angledright.png "0404-33_AngledRight")

 Use fontes de luz somente quando adicionar clareza necessária a um objeto.

|||
|-|-|
|**Fonte de luz correta**|**Fonte de luz incorreta**|
|![Corrigir fontes de luz para ícones](../../extensibility/ux-guidelines/media/0404-34-lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Fontes de luz incorretas para ícones](../../extensibility/ux-guidelines/media/0404-35-lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Use contornos apenas para melhorar a legibilidade ou para comunicar melhor a metáfora. O saldo negativo positivo (luz escura) deve ser 50/50.

|||
|-|-|
|**Uso correto de contornos**|**Uso incorreto de contornos**|
|![Contornos corretos](../../extensibility/ux-guidelines/media/0404-36-outlinescorrect.png "0404-36_OutlinesCorrect")|![Contornos incorretos](../../extensibility/ux-guidelines/media/0404-37-outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Tipos de ícones
 **Os** ícones da barra de comando e shell consistem em não mais do que três dos seguintes elementos: uma base, um modificador, uma ação ou um status.

 ![Ícones da barra de comando e shell](../../extensibility/ux-guidelines/media/0404-38-shellicons.png "0404-38_ShellIcons")

 **Exemplos de ícones de shell e barra de comando**

 **Os** ícones da barra de comando da janela da ferramenta consistem em não mais do que três dos seguintes elementos: uma base, um modificador, uma ação ou um status.

 ![Ícones da barra de comando da janela da ferramenta](../../extensibility/ux-guidelines/media/0404-39-toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")

 **Exemplos de ícones da barra de comando da janela de ferramenta**

 Os ícones **do desambiguator** da visão da árvore consistem em não mais do que três dos seguintes elementos: uma base, um modificador, uma ação ou um status.

 ![Ícones de desambiguator de visão de árvore](../../extensibility/ux-guidelines/media/0404-40-treeviewicons.png "0404-40_TreeViewIcons")

 **Exemplos de ícones de desambiguator de visualização de árvores**

 Existem ícones **de taxonomia de valor baseados** no Estado nos seguintes estados: ativo, ativo desativado e inativo desativado.

 ![Ícones de valor de taxonomia baseados no&#45;do Estado](../../extensibility/ux-guidelines/media/0404-41-statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")

 **Exemplos de ícones de taxonomia de valor baseados no Estado**

 Os ícones do **IntelliSense** consistem em não mais do que três dos seguintes elementos: uma base, um modificador e um status.

 ![Ícones do IntelliSense](../../extensibility/ux-guidelines/media/0404-42-intellisenseicons.png "0404-42_IntelliSenseIcons")

 **Exemplos de ícones do IntelliSense**

 Os ícones **de projeto pequenos (16x16)** não devem ter mais do que dois elementos: uma base e um modificador.

 ![Ícone do projeto 16x16 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-43-16x16project1.png "0404-43_16x16Project1") ![ícone do projeto 16x16 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44-16x16project2.png "0404-44_16x16Project2") ícone do projeto ![16x16 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45-16x16project3.png "0404-45_16x16Project3")

 **Exemplos de ícones de projetos pequenos (16x16)**

 Grandes ícones de **projeto (32x32)** consistem em não mais do que quatro dos seguintes elementos: uma base, um a dois modificadores e uma sobreposição de idioma.

 ![Ícones do projeto 32x32](../../extensibility/ux-guidelines/media/0404-46-32x32project.png "0404-46_32x32Project")

 **Exemplos de grandes ícones de projeto (32x32)**

### <a name="production-details"></a>Detalhes da produção
 Todos os novos elementos de UI devem ser criados usando o Windows Presentation Foundation (WPF) e todos os novos ícones para WPF devem estar no formato PNG de 32 bits. O PNG de 24 bits é um formato legado que não suporta transparência e, portanto, não é recomendado para ícones.

 Salve a resolução em 96 DPI.

#### <a name="file-types"></a>Tipos de arquivo

- **PNG de 32 bits:** o formato preferido para ícones. Um formato de arquivo de compactação de dados sem perdas que pode armazenar uma única imagem rasterizada (pixel). Os arquivos PNG de 32 bits suportam transparência de canal alfa, correção gama e entrelaçamento.

- **BMP de 32 bits:** para controles não-WPF. Também chamado de XP ou de alta cor, o BMP de 32 bits é um formato de imagem RGB/A, uma imagem em cores verdadeiras com uma transparência de canal alfa. O canal alfa é uma camada de transparência designada no Adobe Photoshop que é salva dentro do bitmap como um canal de cores adicional (quarto). Um fundo preto é adicionado durante a produção de arte para todos os arquivos BMP de 32 bits para fornecer uma sugestão visual rápida sobre a profundidade de cor. Este fundo preto representa a área a ser mascarada na UI.

- **ICO de 32 bits:** para ícones do projeto e adicionar item. Todos os arquivos ICO são de cor verdadeira de 32 bits com transparência de canal alfa (RGB/A). Como os arquivos ICO podem armazenar vários tamanhos e profundidades de cores, os ícones do Vista geralmente estão em um formato ICO contendo tamanhos de imagem 16x16, 32x32, 48x48 e 256x256. Para serem exibidos corretamente no Windows Explorer, os arquivos ICO devem ser salvos em profundidades de cores de 24 e 8 bits para cada tamanho de imagem.

- **XAML:** para superfícies de design e adornos windows. Os ícones XAML são arquivos de imagem baseados em vetores que suportam dimensionamento, rotação, arquivamento e transparência. Eles não são comuns no Visual Studio hoje em dia, mas estão se tornando mais populares por causa de sua flexibilidade.

- **SVG**

- **BMP de 24 bits:** para a barra de comando do Visual Studio. Um formato de imagem RGB de cor real, bmp de 24 bits é uma convenção de ícones que cria uma camada de transparência usando magenta (R=255, G=0, B=255) como uma chave de cor para uma camada de transparência de knock-out. Em um BMP de 24 bits, todas as superfícies magenta são exibidas usando a cor de fundo.

- **GIF de 24 bits:** para a barra de comando do Visual Studio. Um formato de imagem RGB de cor real que suporta transparência. Os arquivos GIF são frequentemente usados em artes do Wizard e animações GIF.

### <a name="icon-construction"></a>Construção de ícones
 O menor tamanho de ícone no Visual Studio é 16x16. O maior em uso comum é 32x32. Tenha em mente para não preencher todo o quadro 16x16, 24x24 ou 32x32 ao projetar um ícone. A construção de ícones legíveis e uniformes é essencial para o reconhecimento do usuário. Adere aos seguintes pontos ao construir ícones.

- Os ícones devem ser claros, compreensíveis e consistentes.

- É melhor usar os elementos de notificação de status como ícones únicos e não empilhá-los em cima de um elemento base de ícones. Em certos contextos, a interface do ui pode exigir que o elemento de status seja emparelhado com um elemento base.

- Os ícones do projeto geralmente são arquivos .ico que contêm vários tamanhos. Apenas os ícones 16x16, 24x24 e 32x32 estão sendo atualizados. A maioria dos ícones 16x16 e 24x24 conterá os mesmos elementos. Os ícones 32x32 contêm mais detalhes, incluindo o tipo de linguagem do projeto quando aplicável.

- Para ícones 32x32, os elementos base geralmente têm um peso de linha de 2 pixels. Um peso de linha de 1 ou 2 pixels pode ser usado para elementos de detalhes. Use seu melhor julgamento para determinar qual é mais adequado.

- Tenha pelo menos um espaçamento de 1 pixel entre os elementos para ícones 16x16 e 24x24. Para ícones 32x32, use espaçamento de 2 pixels entre elementos e entre o modificador e o elemento base.

  ![Espaçamento de elementos para ícones 16x16, 24x24 e 32x32](../../extensibility/ux-guidelines/media/0404-47-elementspacing.png "0404-47_ElementSpacing")

  **Espaçamento de elementos para ícones tamanho 16x16, 24x24 e 32x32**

#### <a name="color-and-accessibility"></a>Cor e acessibilidade
 As diretrizes de conformidade do Visual Studio exigem que todos os ícones do produto passem pelos requisitos de acessibilidade para cor e contraste. Isso é conseguido através da inversão de ícones, e quando você está projetando, você deve estar ciente de que eles serão invertidos programáticamente no produto.

 Para obter mais informações sobre como usar a cor nos ícones do Visual Studio, consulte [Usando cores em imagens](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>Usando cores em imagens

### <a name="overview"></a>Visão geral
 Os ícones do Visual Studio são principalmente monocromáticos. A cor é reservada para transmitir informações específicas e nunca para decoração. A cor é usada:

- para indicar uma ação

- para alertar o usuário para uma notificação de status

- para designar a filiação linguística

- para diferenciar itens dentro do IntelliSense

### <a name="accessibility"></a>Acessibilidade
 As diretrizes de conformidade do Visual Studio exigem que todos os ícones verificados no produto passem pelos requisitos de acessibilidade para cor e contraste. As cores na paleta de linguagem visual foram testadas e atendem a esses requisitos.

#### <a name="color-inversion-for-dark-themes"></a>Inversão de cores para temas escuros
 Para fazer com que os ícones apareçam com a razão de contraste correta no tema escuro do Visual Studio, uma inversão é aplicada programáticamente. As cores deste guia foram escolhidas em parte para que se invertam corretamente. Restrinja o uso de cor a esta paleta, ou obterá resultados imprevisíveis quando a inversão for aplicada.

 ![Exemplos de ícones cujas cores foram invertidas](../../extensibility/ux-guidelines/media/0405-01-darkthemeinversion.png "0405-01_DarkThemeInversion")

 **Exemplos de ícones que tiveram suas cores invertidas**

### <a name="base-palette"></a>Paleta de base
 Todos os ícones padrão contêm três cores básicas. Os ícones não contêm gradientes ou sombras projetadas, com uma ou duas exceções para ícones de ferramentas 3D.

|Uso|Nome|Valor (Tema da luz)|Swatch|Exemplo|
|-----------|----------|---------------------------|------------|-------------|
|Fundo/Escuro|VS BG|424242 / 66,66,66|![Swatch 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|![Exemplo de paleta base](../../extensibility/ux-guidelines/media/0405-02-basepaletteexample.png "0405-02_BasePaletteExample")|
|Primeiro plano/Luz|VS FG|F0EFF1 / 240.239.241|![Swatch F0EFF1](../../extensibility/ux-guidelines/media/0405-f0eff1.png "0405_F0EFF1")||
|Contorno|VS Out|F6F6F6 / 246.246.246|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")||

 Além das cores base, cada ícone pode conter uma cor adicional da paleta estendida.

### <a name="extended-palette"></a>Paleta estendida

#### <a name="action-modifiers"></a>Modificadores de ação
 As quatro cores abaixo indicam os tipos de ações exigidas pelos modificadores de ação:

|Uso|Nome|Valor (todos os temas)|Swatch|
|-----------|----------|--------------------------|------------|
|Positivo|VS Ação Verde|388A34 / 56.138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Negativo|VS Ação Vermelha|A1260D / 161,38,13|![Swatch A1260D](../../extensibility/ux-guidelines/media/0405-a1260d.png "0405_A1260D")|
|Neutro|VS Ação Azul|00539C / 0,83.156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|Criar/Criar/Novo|VS Ação Laranja|C27D1A / 194.156,26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Exemplos
 O verde é usado para modificadores de ação positivos como "Adicionar", "Executar", "Jogar" e "Validar".

|||||
|-|-|-|-|
|![Executar ícone](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun") **Executar**|![Executar o ícone de consulta](../../extensibility/ux-guidelines/media/0405-04-executequery.png "0405-04_ExecuteQuery") Executar **consulta**|![Reproduzir todos os passos ícone](../../extensibility/ux-guidelines/media/0405-05-playallsteps.png "0405-05_PlayAllSteps") **Jogar todos os passos**|![Adicionar ícone de controle](../../extensibility/ux-guidelines/media/0405-06-addcontrol.png "0405-06_AddControl") **Adicionar controle**|

 Vermelho é usado para modificadores de ação negativas como "Excluir", "Parar", "Cancelar" e "Fechar".

|||||
|-|-|-|-|
|![Excluir ícone de relacionamento](../../extensibility/ux-guidelines/media/0405-07-deleterelationship.png "0405-07_DeleteRelationship") **Excluir relacionamento**|![Excluir ícone da coluna](../../extensibility/ux-guidelines/media/0405-08-deletecolumn.png "0405-08_DeleteColumn") **Excluir coluna**|![Parar o ícone de consulta](../../extensibility/ux-guidelines/media/0405-09-stopquery.png "0405-09_StopQuery") Stop **Query**|![Ícone off-line de conexão](../../extensibility/ux-guidelines/media/0405-10-connectionoffline.png "0405-10_ConnectionOffline") **Conexão Offline**|

 O azul é aplicado a modificadores de ação neutros mais comumente representados como setas, como "Aberto", "Próximo", "Anterior", "Importação" e "Exportação".

|||||
|-|-|-|-|
|![Ir para o ícone de campo](../../extensibility/ux-guidelines/media/0405-11-gotofield.png "0405-11_GoToField") Ir para **Campo**|![Verificação em lote&#45;no ícone](../../extensibility/ux-guidelines/media/0405-12-batchedcheckin.png "0405-12_BatchedCheckIn") **Check-In em lote**|![Ícone do editor de endereços](../../extensibility/ux-guidelines/media/0405-13-addresseditor.png "0405-13_AddressEditor") **Editor de endereços**|![Ícone do editor da associação](../../extensibility/ux-guidelines/media/0405-14-associationeditor.png "0405-14_AssociationEditor") Editor da **Associação**|

 O ouro escuro é usado principalmente para o modificador "Novo".

|||||
|-|-|-|-|
|![Novo ícone do projeto](../../extensibility/ux-guidelines/media/0405-15-newproject.png "0405-15_NewProject") **Novo Projeto**|![Criar novo ícone de gráfico](../../extensibility/ux-guidelines/media/0405-16-createnewgraph.png "0405-16_CreateNewGraph") Criar novo **gráfico**|![Novo ícone de teste da unidade](../../extensibility/ux-guidelines/media/0405-17-newunittest.png "0405-17_NewUnitTest") Novo Teste da **Unidade**|![Novo ícone do item da lista](../../extensibility/ux-guidelines/media/0405-18-newlistitem.png "0405-18_NewListItem") **Novo Item de lista**|

#### <a name="special-cases"></a>Casos especiais
 Em casos especiais, um modificador de ação colorido pode ser usado independentemente como um ícone autônomo. A cor usada para o ícone reflete as ações com as que o ícone está associado. Este uso é limitado a um pequeno subconjunto de ícones, incluindo:

||||||
|-|-|-|-|-|
|![Executar ícone](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun") **Executar**|![Ícone parar](../../extensibility/ux-guidelines/media/0405-19-stop.png "0405-19_Stop") **Parar**|![Excluir ícone](../../extensibility/ux-guidelines/media/0405-20-delete.png "0405-20_Delete") **Excluir**|![Salvar ícone](../../extensibility/ux-guidelines/media/0405-21-save.png "0405-21_Save") **Salvar**|![Navegar de volta ícone](../../extensibility/ux-guidelines/media/0405-22-navigateback.png "0405-22_NavigateBack") **navegar de volta**|

### <a name="code-hierarchy-palette"></a>Paleta de hierarquia de código

#### <a name="folder"></a>Pasta

|Uso|Nome|Valor (todos os temas)|Swatch|Exemplo|
|-----------|----------|--------------------------|------------|-------------|
|Pastas|Pasta|DCB67A / 220.182.122|![Swatch DCB67A](../../extensibility/ux-guidelines/media/0405-dcb67a.png "0405_DCB67A")|![Ícone de cor da pasta](../../extensibility/ux-guidelines/media/0405-23-foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Linguagens do Visual Studio
 Cada uma das linguagens ou plataformas comuns disponíveis no Visual Studio tem uma cor associada. Essas cores são usadas no ícone base ou nos modificadores de idioma que aparecem no canto superior direito dos ícones compostos.

|Uso|Nome|Valor (todos os temas)|Swatch|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Azul|0095D7 / 0.149.215|![Swatch 0095D7](../../extensibility/ux-guidelines/media/0405-0096d7.png "0405_0096D7")|
|C++|CPP Roxo|9B4F96 / 155,79,150|![Swatch 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|C#|CS Green (VS Action Green)|388A34 / 56.138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|CSS|Vermelho CSS|BD1E2D / 189,30,45|![Relógio BD1E2D](../../extensibility/ux-guidelines/media/0405-bd1e2d.png "0405_BD1E2D")|
|F#|FS Roxo|672878 / 103,40,120|![Swatch 672878](../../extensibility/ux-guidelines/media/0405-672878.png "0405_672878")|
|JavaScript|Laranja JS|F16421 / 241.100,33|![Swatch F16421](../../extensibility/ux-guidelines/media/0405-f16421.png "0405_F16421")|
|VB|VB Blue (VS Action Blue)|00539C / 0,83.156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|TypeScript|Laranja TS|E04C06 / 224,76,6|![Swatch E04C06](../../extensibility/ux-guidelines/media/0405-e04c06.png "0405_E04C06")|
|Python|PI Verde|879636 / 135,150,54|![Swatch 879636](../../extensibility/ux-guidelines/media/0405-879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Exemplos de ícones com modificadores de idioma

|||||||
|-|-|-|-|-|-|
|![Ícone básico visual](../../extensibility/ux-guidelines/media/0405-25-vb.png "0405-25_VB") **VB**|![C&#35; ícone](../../extensibility/ux-guidelines/media/0405-26-csharp.png "0405-26_CSharp") **C#**|![Ícone c&#43;&#43; ](../../extensibility/ux-guidelines/media/0405-27-cplusplus.png "0405-27_CPlusPlus") **C++**|![F ícone&#35;](../../extensibility/ux-guidelines/media/0405-28-fsharp.png "0405-28_FSharp") **F#**|![JavaScript ícone](../../extensibility/ux-guidelines/media/0405-29-javascript.png "0405-29_JavaScript") **JavaScript**|![Python ícone](../../extensibility/ux-guidelines/media/0405-30-python.png "0405-30_Python") **Python**|
|![Ícone HTML](../../extensibility/ux-guidelines/media/0405-31-html.png "0405-31_HTML") **HTML**|![Ícone WPF](../../extensibility/ux-guidelines/media/0405-32-wpf.png "0405-32_WPF") **WPF**|![Ícone ASP](../../extensibility/ux-guidelines/media/0405-33-asp.png "0405-33_ASP") **ASP**|![Ícone CSS](../../extensibility/ux-guidelines/media/0405-34-css.png "0405-34_CSS") **CSS**|![TypeScript, ícone do TypeScript](../../extensibility/ux-guidelines/media/0405-35-typescript.png "0405-35_TypeScript") **TypeScript**||

#### <a name="intellisense"></a>IntelliSense
 Os ícones do IntelliSense usam uma paleta de cores exclusiva. Essas cores são usadas para ajudar os usuários a distinguir rapidamente entre os diferentes itens da lista pop-up do IntelliSense.

|Uso|Nome|Valor (todos os temas)|Swatch|
|-----------|----------|--------------------------|------------|
|Classe, Evento|VS Ação Laranja|C27D1A / 194.125,26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|
|Método de extensão, método, módulo, delegado|VS Ação Roxa|652D90 / 101,45,144|![Swatch 652D90](../../extensibility/ux-guidelines/media/0405-652d90.png "0405_652D90")|
|Campo, Item enum, Macro, Estrutura, Tipo de Valor da União, Operador, Interface|VS Ação Azul|00539C / 0,83.156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|Objeto|VS Ação Verde|388A34 / 56.138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Constante, exceção, item de enum, mapa, item do mapa, namespace, modelo, definição de tipo|Fundo (VS BG)|424242 / 66,66,66|![Swatch 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Exemplos de ícones do IntelliSense

||||||
|-|-|-|-|-|
|![Classe ícone da classe IntelliSense](../../extensibility/ux-guidelines/media/0405-36-intellisenseclass.png "0405-36_IntelliSenseClass") **Class**|![Ícone do evento privado IntelliSense](../../extensibility/ux-guidelines/media/0405-37-intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent") **Evento Privado**|![Ícone delegado da IntelliSense](../../extensibility/ux-guidelines/media/0405-38-intellisensedelegate.png "0405-38_IntelliSenseDelegate") **Delegado**|![Ícone do método IntelliSense](../../extensibility/ux-guidelines/media/0405-39-intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend") **Amigo do método**|![Campo do ícone de](../../extensibility/ux-guidelines/media/0405-40-field.png "0405-40_Field") **campo**|
|![Ícone de item enum protegido da IntelliSense](../../extensibility/ux-guidelines/media/0405-41-intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem") **Protected Enum Item**|**Objeto** ![do ícone do objeto IntelliSense](../../extensibility/ux-guidelines/media/0405-42-intellisenseobject.png "0405-42_IntelliSenseObject")|![Modelo de ícone do modelo IntelliSense](../../extensibility/ux-guidelines/media/0405-43-intellisensetemplate.png "0405-43_IntelliSenseTemplate") **Template**|![Ícone de atalho de exceção do IntelliSense](../../extensibility/ux-guidelines/media/0405-44-intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut") **Exception Shortcut**||

### <a name="notifications"></a>Notificações
 Notificações no Visual Studio são usadas para indicar status. A paleta de notificações usa as quatro cores a seguir, bem como as opções de preenchimento em primeiro plano preto ou branco, para definir notificações com os seguintes níveis de status.

|Uso|Nome|Valor (todos os temas)|Swatch|
|-----------|----------|--------------------------|------------|
|Status: neutro|Notificações Azuis (VS Azul)|1BA1E2 / 27.161.226|![Swatch 1BA1E2](../../extensibility/ux-guidelines/media/0405-1ba1e2.png "0405_1BA1E2")|
|Estado: positivo|Verde de notificação (VS Verde)|339933 / 51,153,51|![Swatch 339933](../../extensibility/ux-guidelines/media/0405-339933.png "0405_339933")|
|Status: negativo|Vermelho de notificação (VS Vermelho)|E51400 / 229,20,0|![Swatch E51400](../../extensibility/ux-guidelines/media/0405-e51400.png "0405_E51400")|
|Status: aviso|Aviso Amarelo (VS Laranja)|FFCC00 / 255.204,0|![Swatch FFCC00](../../extensibility/ux-guidelines/media/0405-ffcc00.png "0405_FFCC00")|
|Preenchimento em primeiro plano|Preto de notificação (preto)|000000 / 0,0,0|![&#35;de swatch](../../extensibility/ux-guidelines/media/0405-000000.png "0405_000000")|
|Preenchimento em primeiro plano|Notificações Brancas (Brancas)|FFFFFF / 255.255.255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Exemplos de ícones de notificação

|||||
|-|-|-|-|
|![Alerta de ícone de](../../extensibility/ux-guidelines/media/0405-45-alert.png "0405-45_Alert") **alerta**|![Ícone de aviso](../../extensibility/ux-guidelines/media/0405-48-warning.png "0405-48_Warning") **Aviso**|![Ícone completo](../../extensibility/ux-guidelines/media/0405-46-complete.png "0405-46_Complete") **Completo**|![Ícone parar](../../extensibility/ux-guidelines/media/0405-47-stop.png "0405-47_Stop") **Parar**|

### <a name="visual-studio-online"></a>Visual Studio Online
 Em geral, o Visual Studio Online consiste em recursos hospedados em um navegador. A cor varia em ambientes diferentes, mas o estilo permanece o mesmo.

|Agrupar|Uso|Nome|Valor (todos os temas)|Swatch|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Segundo plano|TFSO BG|656565/ 101, 101, 101|![Swatch 656565](../../extensibility/ux-guidelines/media/0405-656565.png "0405_656565")|
|TFS|Contorno|TFSO OUT|FFFFFF / 255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|Napa|Segundo plano|Branco|FFFFFF / 255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|Mônaco|Segundo plano|Branco|FFFFFF / 255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|Segundo plano|Branco|FFFFFF / 255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|Normal|F12 Grey_Primary|555555 / 85, 85, 85|![Swatch 555555](../../extensibility/ux-guidelines/media/0405-555555.png "0405_555555")|
|F12|Passar o mouse|F12 Blue_Hover|2279BF / 34.121.191|![Swatch 2279BF](../../extensibility/ux-guidelines/media/0405-2279bf.png "0405_2279BF")|
|F12|Desabilitado|F12 LtGrey_Disabled|ABABAC / 171.171.172|![Swatch ABABAC](../../extensibility/ux-guidelines/media/0405-ababac.png "0405_ABABAC")|
|F12|Fundo de sobrever|Hover bg|D9EBF7 / 217.235.247|![Swatch D9EBF7](../../extensibility/ux-guidelines/media/0405-d9ebf7.png "0405_D9EBF7")|
|F12|Fundo pressionado|Pressionado bg|B2D7F0 / 178.215.240|![Swatch B2D7F0](../../extensibility/ux-guidelines/media/0405-b2d7f0.png "0405_B2D7F0")|
|F12|Contorno|VS OUT|F6F6F6 / 246.246.246|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")|
|F12|Informações|Informações|00BCF2 / 0.188.242|![Swatch 00BCF2](../../extensibility/ux-guidelines/media/0405-00bcf2.png "0405_00BCF2")|
|F12|Aviso|Aviso|F28300 / 242.131,0|![Swatch F28300](../../extensibility/ux-guidelines/media/0405-f28300.png "0405_F28300")|
|F12|Erro / Negativo|Error_Negative|E81123 / 232,17,35|![Swatch E81123](../../extensibility/ux-guidelines/media/0405-e81123.png "0405_E81123")|
|F12|Iniciar / Positivo|Start_Positive|009E49 / 0.158,73|![Swatch 009E49](../../extensibility/ux-guidelines/media/0405-009e49.png "0405_009E49")|
|F12|Tipo de quebra|Tipo de quebra|9B4F96 / 155,79,150|![Swatch 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|F12|Marca de evento|Marca de evento|A51F00 / 165,31,0|![Swatch A51F00](../../extensibility/ux-guidelines/media/0405-a51f00.png "0405_A51F00")|
|F12|Marca de usuário|Marca de usuário|F16220 / 241,98,32|![Swatch F16220](../../extensibility/ux-guidelines/media/0405-f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Exemplos de ícones do Visual Studio Online

|TFS Online||||
|----------------|-|-|-|
|![TfS Online team ícone](../../extensibility/ux-guidelines/media/0405-49-tfsonlineteam.png "0405-49_TFSOnlineTeam") **de equipe**|![Informações do ícone de informações do TFS](../../extensibility/ux-guidelines/media/0405-50-tfsinformation.png "0405-50_TFSInformation") **Informações**|![Ícone de história do TFS](../../extensibility/ux-guidelines/media/0405-51-tfshistory.png "0405-51_TFSHistory") **História**|![Ramo da filial TFS](../../extensibility/ux-guidelines/media/0405-52-tfsbranch.png "0405-52_TFSBranch") **Branch**|

|Napa||||
|----------|-|-|-|
|![Conteúdo do ícone de conteúdo napa](../../extensibility/ux-guidelines/media/0405-53-napacontent.png "0405-53_NapaContent") **Content**|![Ícone de correio de escritório napa](../../extensibility/ux-guidelines/media/0405-54-napaofficemail.png "0405-54_NapaOfficeMail") **Office Mail**|![Ícone do Napa SharePoint](../../extensibility/ux-guidelines/media/0405-55-napasharepoint.png "0405-55_NapaSharePoint") **SharePoint**|![Napa task pane ícone](../../extensibility/ux-guidelines/media/0405-56-napataskpane.png "0405-56_NapaTaskPane") **Painel de tarefas**|

|Mônaco||||
|------------|-|-|-|
|![Monaco arquiva arquivos](../../extensibility/ux-guidelines/media/0405-57-monacofiles.png "0405-57_MonacoFiles") **Files**|![Ícone de Mônaco Git](../../extensibility/ux-guidelines/media/0405-58-monacogit.png "0405-58_MonacoGit") **Git**|![Ícone de pesquisa de Mônaco](../../extensibility/ux-guidelines/media/0405-59-monacosearch.png "0405-59_MonacoSearch") **Pesquisa**|![Ícone de texto de Mônaco](../../extensibility/ux-guidelines/media/0405-60-monacotext.png "0405-60_MonacoText") **Texto**|

|F12||||
|---------|-|-|-|
|![F12 ícone de código bonito](../../extensibility/ux-guidelines/media/0405-61-f12prettycode.png "0405-61_F12PrettyCode") Pretty **Code**|![Ícone de aviso do F12](../../extensibility/ux-guidelines/media/0405-62-f12warning.png "0405-62_F12Warning") **Aviso**|![Ícone de Emulação f12](../../extensibility/ux-guidelines/media/0405-63-f12emulate.png "0405-63_F12Emulate") **Emulate**|
