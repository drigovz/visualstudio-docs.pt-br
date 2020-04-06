---
title: Layout para Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698405"
---
# <a name="layout-for-visual-studio"></a>Layout para Visual Studio
A maioria dos diálogos do Visual Studio são [layout de diálogo utilitário,](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)que são os diálogos não temáticos que seguem os princípios padrão [de layout de diálogo do Windows Desktop](/windows/desktop/uxguide/win-dialog-box). À medida que o Visual Studio se move para atualizar sua ui, alguns dos diálogos mais proeminentes têm um novo design que os estabelece como experiências de definição de produtos. Estelayout [de diálogo temático](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) tem uma aparência temática.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a>Layout de diálogo utilitário

- Todos os controles dentro de uma caixa de diálogo de utilidade devem começar na parte superior/esquerda e fluir para baixo.

- Nunca centralizar controles em um diálogo para preencher uma grande área.

- Use a fonte do ambiente para todos os textos de diálogo. Ao escrever uma especificação visual, especifique a fonte do ambiente em vez de selecionar uma fonte e tamanho específicos. Veja [a fonte do ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Use espaçamento de controle consistente e colocação para apoiar o objetivo de qualidade no artesanato.

- Diálogos podem se tornar mais complexos a partir de um número maior de controles, uma justaposição única de controles, ou ambos. Para essas situações complexas, permita espaço adequado entre os agrupamentos de controle para dar ao usuário um fluxo lógico para analisar.

### <a name="utility-dialog-layout-examples"></a>Exemplos de layout de diálogo de utilidade
 Todas as dimensões são expressas como pixels.

 ![Diálogo espaçamento para rótulos acima de controles](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Figura 08.01-a: Diretrizes de espaçamento para diálogos de utilidade com rótulos acima de controles**

 ![Diálogo espaçamento para rótulos à esquerda dos controles](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Figura 08.01-b: Diretrizes de espaçamento para diálogos de utilidade com etiquetas à esquerda dos controles**

### <a name="layout-details"></a>Detalhes do layout

#### <a name="margins"></a>Margens

- Todos os diálogos devem ter uma borda de 12 pixels em todas as bordas.

- As margens dentro de um quadro de grupo devem ser de 9 pixels da borda do quadro.

- As margens dentro de um controle de guia devem ser de 6 pixels da borda do controle da guia.

#### <a name="command-buttons"></a>Botões de comando

- Os botões de comando operam no quadro de diálogo, não no conteúdo. Eles devem ser colocados no canto inferior direito e devem ter espaço variável suficiente acima para definir os botões distintamente separados.

- Se houver botões horizontais que operam dentro da caixa de diálogo, a configuração do botão de comando alternativo é uma pilha vertical no canto superior direito. Veja [os botões de comando Interior](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) abaixo.

- O espaço à esquerda dos botões de comando (inferior esquerdo/centro da caixa de diálogo) é considerado parte da "banda" dos controles de operação de diálogo. A única coisa que deve se intrometer nesse espaço é um link de Ajuda que é relevante para a tarefa ou diálogo geral.

- Os botões de comando devem ser de 75x23 pixels.

- Os botões de comando devem ter 6 pixels de diferença.

  ![Alinhamento básico do botão](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Figura 08.01-c: Alinhamento básico do botão**

#### <a name="labels"></a>Rótulos

- Alinhem todas as etiquetas.

- Para rótulos que se sentam acima de um controle, eles devem alinhar-se precisamente com o controle abaixo dele e a parte inferior da etiqueta deve ser de 5 pixels acima da parte superior do outro controle (por exemplo, uma caixa de combinação).

- Para etiquetas que se sentam à esquerda dos controles, a largura mínima entre a etiqueta e o controle de entrada é de 10 pixels. Uma segunda coluna implícita deve ser estabelecida para alinhar as caixas de texto, caixas de combinação ou outros controles.

- Rótulos são caso de sentença e são seguidos por um cólon. Ver [estilo texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Distância entre controles
 A pilha controla razoavelmente. Não há uma diretriz absoluta para o espaçamento entre os controles empilhados. O aperto entre os controles pode variar ligeiramente entre os diálogos. O espaçamento recomendado é de 20 pixels para pares de controle/etiqueta vertical e 9 pixels para pares de controle horizontal/etiqueta. O espaçamento mínimo de controle para pares horizontais é de 6 pixels.

 ![Distância recomendada entre controles](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Figura 08.01-d: Recomendações para distância entre controles**

#### <a name="control-indentation"></a>Recuo de controle
 Quando os controles estiverem aninhados, alinhe os controles internos horizontalmente com a borda esquerda do controle acima, geralmente a etiqueta.

 ![Alinhamento de controle aninhado](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Figura 08.01-e: Alinhamento de controle aninhado**

#### <a name="control-width"></a>Largura de controle
 A largura de uma caixa de texto ou outros controles semelhantes não deve ser maior do que a entrada média para o campo. A palavra média em inglês é de cinco caracteres. Por exemplo, uma caixa de texto que exija um nome de caminho longo deve ser tão longa quanto o layout horizontal permitir, enquanto uma gota para nomes de plataforma deve ser apenas um comprimento que permite a entrada mais longa.

#### <a name="helper-text"></a>Texto auxiliar

- Uma caixa de diálogo pode exibir texto auxiliar que fornece mais informações sobre o propósito da caixa de diálogo. Isso normalmente fica no topo e pode ser de 1 a 2 frases.

- O comprimento da linha deve ser uma largura confortável para o usuário analisar e ler. Um diálogo médio não deve ter mais de 550 pixels de largura.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a>Botões de comando interior
 Em diálogos mais complexos, um controle interno pode ter seus próprios botões relacionados, o que pode afetar onde os botões de confirmação da caixa de diálogo estão localizados.

- Use um alinhamento vertical (coluna) de botões internos quando **OK**/**Cancelar** estiver horizontalmente orientado no canto inferior direito.

- Use um alinhamento horizontal (linha) de botões internos quando **OK**/**Cancelar** estiver orientado verticalmente no canto superior direito. Esta situação é menos comum.

- O tamanho do botão interno deve atingir o tamanho padrão do botão de 75x23 pixels, correspondendo ao tamanho dos botões **OK**/**Cancel** quando possível. Se uma etiqueta de botão fizer com que o botão exceda o tamanho padrão do botão, os outros botões nesse conjunto devem se alinhar com esse tamanho maior.

  ![Botões horizontais OK e Cancel](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Figura 08.01-f: Botões de interior vertical com OK horizontal/Cancelamento**

  ![Botões verticais OK e Cancel](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Figura 08.01-g: Botões internos horizontais com OK/Cancelamento verticais**

#### <a name="browse-button"></a>[Procurar...] Botão
 **[Procurar...]** botões que seguem uma caixa de texto devem soletrar "Procurar..." na íntegra, incluindo a elipse. Se o espaço estiver apertado ou houver vários botões **[Procurar...]** na tela, o botão pode ser reduzido apenas à elipse.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a>Layout de diálogo temático
 Diálogos temáticos no Visual Studio têm uma aparência mais leve e oferecem mais espaço em branco. A tipografia proporciona mais ênfase e interesse, oferecendo mais espaçamento de linha aberta e uma variação de tamanhos e pesos da fonte. Sempre que possível, as barras cromadas e de título foram reduzidas ou removidas. O layout dessas diálogos deve seguir este padrão básico:

1. O pano de fundo do diálogo é branco.

2. Há uma borda de regra de 1 pixel em um cinza de valor médio.

3. O título de diálogo não está mais em uma barra de título, mas fornece interesse visual e ênfase em um tamanho de ponto maior. (Consulte a seção tamanho da fonte no [estilo Texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4. Os rótulos juntamente com texto adicional, como uma descrição, devem ser **fonte de ambiente + negrito**.

5. As colunas interiores são separadas por uma regra de 1 pixel em cinza claro.

6. Os links padrão não têm sublinhado. Os estados hover e pressionados têm uma mudança de cor mais sublinhado.

7. Os botões de confirmação (como **OK**/**Cancel)** sentam-se no canto inferior direito.

### <a name="themed-dialog-layout-examples"></a>Exemplos de layout de diálogo temático
 ![Layout de diálogo temático](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Figura 08.01-h: Diálogo temático**

 ![Dimensões de diálogo temáticas](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Figura 08.01-i: Diálogo temático - Dimensões**

 ![Fontes de diálogo temáticas](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Figura 08.01-j: Diálogo temático - Fontes**

 ![Cores de diálogo temáticas](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Figura 08.01-k: Diálogo temático - Cores**

## <a name="see-also"></a>Confira também
- [Padrões de aplicativo para Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Controles (Windows)](/windows/desktop/uxguide/controls)
- [Caixas de diálogo (Windows)](/windows/desktop/uxguide/win-dialog-box)
