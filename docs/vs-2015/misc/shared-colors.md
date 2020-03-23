---
title: Cores compartilhadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: brgeorge
ms.openlocfilehash: 421ff85831bb611b655de2bc35f01423b61921a2
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302402"
---
# <a name="shared-colors"></a>Cores compartilhadas
Inserir introdução aqui.  
  
## <a name="shared-colors"></a>Cores compartilhadas  
 Quando você estiver projetando interface do usuário que usa elementos comuns do Visual Studio shell, ou você gostaria que seu elemento de interface fosse consistente com recursos semelhantes, use nomes de token existentes em arquivos de definição de pacote para escolher e atribuir cores. Isso garante que sua iu de usuário permaneça consistente com o ambiente geral do Visual Studio e que atualize automaticamente quando os temas forem adicionados ou atualizados.  
  
 Este artigo descreve elementos comuns de IU e os nomes de token que eles usam, que você pode referenciar ao construir iu semelhante. Para obter informações específicas sobre como acessar esses tokens de cores, consulte [O Serviço VSColor](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Certifique-se de usar os nomes de token corretamente:  
  
- **Use nomes de token com base na função, não na cor em si.** As cores comuns compartilhadas são associadas a elementos de interface específicos e destinam-se apenas a ser usadas para as mesmas características ou similares. Por exemplo, não reutilize a cor de uma caixa de combinação pressionada para uma animação de progresso giratório só porque você gosta da cor. As funções da caixa de combinação e da animação são diferentes, e se a cor associada à caixa de combinação mudar, pode não ser mais uma cor apropriada para o seu elemento de animação. O uso consistente de cores ajuda a orientar seus usuários e evitar confusão.  
  
- **Use as cores de fundo e texto na combinação correta.** As cores de fundo que se destinam a ser usadas com texto terão uma cor de texto associada. Não use cores de texto diferentes das especificadas para esse plano de fundo. Se não houver uma cor de texto associada, não use essa cor de fundo para qualquer superfície na qual você espera exibir texto. Outras combinações de cores de texto e de fundo podem resultar em uma interface ilegível.  
  
- **Use cores de controle adequadas para sua localização.** Em certos estados, alguns controles do Visual Studio não possuem cores separadas de borda e fundo. Em vez disso, eles pegam essas cores das superfícies atrás deles. Certifique-se de que você sempre usa os nomes de token apropriados para o local onde você está colocando o controle.  
  
> [!IMPORTANT]
> Não use tokens encontrados nas categorias "Iniciar página" ou "Cider"!  
  
### <a name="command-structures"></a>Estruturas de comando  
  
#### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Menus  
 Os menus podem ocorrer em vários lugares dentro do Visual Studio 2013: a barra de menu principal, incorporada em janelas de documentos ou ferramentas, ou no clique com o botão direito do mouse em vários locais ao longo do IDE. Implementações de menus associados a outros elementos de IU são discutidas na seção para o respectivo elemento. Você deve sempre usar a implementação padrão do menu fornecida pelo ambiente Visual Studio. No entanto, em alguns casos raros, você pode não ter acesso aos menus padrão do Visual Studio. Nessas situações, use os seguintes nomes de token para garantir que sua iu é consistente com outros menus no Visual Studio.  
  
 ![Menus linha vermelha](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")  
  
Usar...  
- sempre que você precisar criar um menu personalizado.  
  
- quando você tem um novo componente de ida e volta que deseja combinar com os menus do Visual Studio.  
  
Não use...  
a cor de fundo sozinho. Use sempre a combinação de plano de fundo/primeiro plano conforme especificado.  
  
##### <a name="menu-title"></a>Título do menu  
 Os títulos do menu consistem em um plano de fundo, uma borda e o texto do título, bem como um glifo opcional, geralmente quando o menu é encontrado em uma barra de comando.  
  
 ![Linha vermelha do título do menu](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")  
  
Usar...  
sempre que você estiver criando um título de menu personalizado.  
  
Não use...  
- para qualquer coisa que você não quer sempre corresponder ao título do menu.  
  
- em qualquer combinação de plano de fundo/primeiro plano que não seja especificada.  
  
  **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Padrão do título do menu](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Título do menu**|Segundo plano|Nenhum|  
|![Padrão do título do menu](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Título do menu**|Primeiro plano (Texto)|`Environment.CommandBarTextActive`|  
|![Título do menu com padrão glifo](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Título do menu com glifo**|Primeiro plano (Glifo)|`Environment.CommandBarMenuGlyph`|  
|![Título do menu com padrão glifo](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Título do menu com glifo**|Borda|Nenhum|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Título do menu em hover](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Título do menu**|Segundo plano|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Título do menu em hover](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Título do menu**|Primeiro plano (Texto)|`Environment.CommandBarTextHover`|  
|![Título do menu com glifo no hover](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Título do menu com glifo**|Primeiro plano (Glifo)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Título do menu com glifo no hover](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Título do menu com glifo**|Borda|`Environment.CommandBarBorder`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Título do menu pressionado](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Título do menu**|Segundo plano|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Título do menu pressionado](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Título do menu**|Primeiro plano (Texto)|`Environment.CommandBarTextActive`|  
|![Título do menu com glifo pressionado](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Título do menu com glifo**|Primeiro plano (Glifo)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Título do menu com glifo pressionado](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Título do menu com glifo**|Borda|`Environment.CommandBarMenuBorder`<br /><br /> Só os lados esquerdo, superior e direito.|  
  
 **Desativado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Título do menu com glifo desativado](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Título do menu com glifo**|Segundo plano|Nenhum|  
|![Título do menu com glifo desativado](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Título do menu com glifo**|Primeiro plano (Texto)|`Environment.CommandBarTextInactive`|  
|![Título do menu com glifo desativado](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Título do menu com glifo**|Primeiro plano (Glifo)|`Environment.CommandBarTextInactive`|  
|![Título do menu com glifo desativado](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Título do menu com glifo**|Borda|Nenhum|  
  
##### <a name="menu"></a>Menu  
 Um item de menu individual consiste no texto do menu e um ícone opcional, caixa de seleção ou glifo de menu submenu. Seu plano de fundo e cor de texto mudam no hover. Este token de cor é um par de plano de fundo/primeiro plano.  
  
 ![Itens do menu em linha vermelha](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")  
  
 Usar...  
 para qualquer lista de suspensos que seja lançada a partir de uma barra de menu ou barra de comando.  
  
Não use...  
- para qualquer lista de parada que ocorra em outro contexto.  

- em qualquer combinação de plano de fundo/primeiro plano que não seja especificada.  
  
  **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Padrão do menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Segundo plano|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Padrão do menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Primeiro plano (Texto)|`Environment.CommandBarTextActive`|  
|![Padrão do menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Primeiro plano (Glifo do submenu)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Padrão do menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Borda|`Environment.CommandBarMenuBorder`|  
|![Padrão do menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Histórico do canal de ícones|`Environment.CommandBarMenuIconBackground`|  
|![Padrão do menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Separador|`Environment.CommandBarMenuSeparator`|  
|![Padrão do menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Shadow|`Environment.DropShadowBackground`|  
|![Menu verificado](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Verificado**|Marca de seleção|`Environment.CommandBarCheckBox`|  
|![Menu verificado](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Verificado**|Verifique o plano de fundo da marca|`Environment.CommandBarSelectedIcon`|  
|![Menu selecionado](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Selecionado**|Histórico de ícones|`Environment.CommandBarSelected`|  
|![Menu selecionado](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Selecionado**|Fronteira do ícone|`Environment.CommandBarSelectedBorder`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![O menu paira](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Item de menu**|Segundo plano|`Environment.CommandBarMenuItemMouseOver`|  
|![O menu paira](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Item de menu**|Primeiro plano (Texto)|`Environment.CommandBarMenuItemMouseOver`|  
|![O menu paira](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Item de menu**|Primeiro plano (Glifo do submenu)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![Menu hover verificado](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Verificado**|Marca de seleção|`Environment.CommandBarCheckBoxMouseOver`|  
|![Menu hover verificado](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Verificado**|Verifique o plano de fundo da marca|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Menu hover selecionado](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Selecionado**|Histórico de ícones|`Environment.CommandBarHoverOverSelected`|  
|![Menu hover selecionado](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Selecionado**|Fronteira do ícone|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Desativado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menu desativado](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Item de menu|Primeiro plano (Texto)|`Environment.CommandBarTextInactive`|  
|![Menu desativado](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Item de menu|Primeiro plano (Glifo do submenu)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menu desativado verificado](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Verificado|Marca de seleção|`Environment.CommandBarCheckBoxDisabled`|  
|![Menu desativado verificado](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Verificado|Verifique o plano de fundo da marca|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Barra de comandos  
 A barra de comando pode aparecer em vários lugares dentro do Visual Studio IDE, mais notavelmente na prateleira de comando e embutida em janelas de ferramentas ou documentos.  
  
 Em geral, use sempre a implementação padrão da barra de comando fornecida pelo ambiente Visual Studio. O uso do mecanismo padrão garante que todos os detalhes visuais apareçam corretamente e que os elementos interativos se comportarão consistentemente com outros controles da barra de comando do Visual Studio. No entanto, se for necessário para você construir sua própria barra de comando, certifique-se de estilizá-la corretamente usando os seguintes nomes de token.  
  
 ![Barra de comando linha vermelha](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![Linha vermelha do botão de transbordamento](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 Usar...  
 em lugares onde você precisa de uma barra de comando incorporada, mas não pode usar a implementação padrão da barra de comando do Visual Studio.  
  
Não use...  
- para elementos de IA que não são semelhantes a uma barra de comando.  

- para componentes da barra de comando que não sejam aqueles para os quais os nomes de token são especificados.  
  
##### <a name="command-bar-group"></a>Grupo de barras de comando  
 Um grupo de barras de comando consiste em um conjunto relacionado de controles de barra de comando e pode conter qualquer número de botões, botões divididos, menus suspensos, caixas de combinação ou menus. As cores para esses controles são reguladas por nomes de tokens separados e são discutidas individualmente em outros lugares neste guia. Uma linha separadora é usada para dividir um grupo de barras de comando em subgrupos relacionados.  
  
 ![Linha vermelha do grupo de barras de comando](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 Usar...  
 em lugares onde você precisa de uma barra de comando incorporada, mas não pode usar a implementação padrão da barra de comando do Visual Studio.  
  
Não use...  
- para elementos de IA que não são semelhantes a uma barra de comando.  

- para componentes da barra de comando que não sejam aqueles para os quais os nomes de token são especificados.  
  
  **Inadimplência** (sem outros estados)  
  
|Elemento|Nome do token: Category.color|  
|-------------|--------------------------------|  
|Segundo plano|`Environment.CommandBarGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|Borda|`Environment.CommandBarToolBarBorder`|  
|Identificador de arrastar|`Environment.CommandBarDragHandle`|  
|Separador|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Ícones de comando  
 ![Ícone de comando linha vermelha](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![Ícone de comando linha vermelha](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 Usar...  
 para quaisquer botões que serão colocados em uma barra de comando.  
  
Não use...  
- para controles que têm seus próprios nomes de tokens.  

- em qualquer combinação de plano de fundo/primeiro plano que não seja especificada.  
  
  **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Padrão do ícone de comando](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Padrão**|Segundo plano|N/A (herda do fundo da barra de comando)|  
|![Padrão do ícone de comando](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Padrão**|Primeiro plano (Texto)|`Environment.CommandBarTextActive`|  
|![Padrão do ícone de comando](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Padrão**|Borda|N/D|  
|![Padrão de ícone de comando selecionado](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Selecionado**|Segundo plano|`Environment.CommandBarSelected`|  
|![Padrão de ícone de comando selecionado](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Selecionado**|Primeiro plano (Texto)|`Environment.CommandBarTextSelected`|  
|![Padrão de ícone de comando selecionado](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Selecionado**|Borda|`Environment.CommandBarSelectedBorder`|  
  
 **Hover e teclado focado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hover ícone de comando](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Padrão em pairam**|Segundo plano|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Hover ícone de comando](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Padrão em pairam**|Primeiro plano (Texto)|`Environment.CommandBarTextHover`|  
|![Hover ícone de comando](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Padrão em pairam**|Borda|`Environment.CommandBarBorder`|  
|![Hover ícone de comando selecionado](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Selecionado em pairam**|Segundo plano|`Environment.CommandBarHoverOverSelected`|  
|![Hover ícone de comando selecionado](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Selecionado em pairam**|Primeiro plano (Texto)|`Environment.CommandBarTextHoverOverSelected`|  
|![Hover ícone de comando selecionado](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Selecionado em pairam**|Borda|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ícone de comando pressionado](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Ícone de comando pressionado**|Segundo plano|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Ícone de comando pressionado](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Ícone de comando pressionado**|Primeiro plano (Texto)|`Environment.CommandBarTextMouseDown`|  
|![Ícone de comando pressionado](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Ícone de comando pressionado**|Borda|`Environment.CommandBarBorder`|  
  
 **Desativado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ícone de comando desativado](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Ícone de comando desativado**|Segundo plano|N/A (herda do fundo da barra de comando)|  
|![Ícone de comando desativado](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Ícone de comando desativado**|Primeiro plano (Texto)|`Environment.CommandBarTextInactive`|  
|![Ícone de comando desativado](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Ícone de comando desativado**|Borda|N/D|  
  
##### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a>Caixa de combinação  
  
> [!IMPORTANT]
> As caixas de combo são semelhantes às gotas, mas incluem uma região de texto editável. Se a sua parada não incluir uma região de texto editável, use os tokens de cor encontrados em [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown).  
  
 ![Linha vermelha da caixa de combo](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")  
  
Usar...  
- ao construir caixas de combinação personalizadas.  

- ao criar um controle de barra de comando semelhante a uma caixa de combinação.  

Não use...  
- para qualquer coisa que você não quer sempre corresponder a ui barra de comando.  

- quando você tem acesso a uma caixa de combinação estilizada.  
  
  **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada da caixa combo](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Campo de entrada**|Segundo plano|`Environment.ComboBoxBackground`|  
|![Campo de entrada da caixa combo](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Campo de entrada**|Primeiro plano (Texto)|`Environment.ComboBoxText`|  
|![Campo de entrada da caixa combo](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Campo de entrada**|Borda|`Environment.ComboBoxBorder`|  
|![Campo de entrada da caixa combo](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Campo de entrada**|Separador|Sem separador|  
|![Caixa de combinação botão de abaixado&#45;](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Botão de drop-down**|Segundo plano|N/A (herda)|  
|![Caixa de combinação botão de abaixado&#45;](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Botão de drop-down**|Primeiro plano (Glifo)|`Environment.ComboBoxGlyph`|  
|![Caixa de combinação&#47;lista de&#45;para baixo](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Lista de paradas**|Segundo plano|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Caixa de combinação&#47;lista de&#45;para baixo](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Lista de paradas**|Primeiro plano (Texto)|`Environment.ComboBoxItemText`|  
|![Caixa de combinação&#47;lista de&#45;para baixo](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Lista de paradas**|Borda|`Environment.ComboBoxPopupBorder`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada da caixa de combinação no hover](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Campo de entrada**|Segundo plano|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Campo de entrada da caixa de combinação no hover](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Campo de entrada**|Primeiro plano (Texto)|`Environment.ComboBoxMouseOverText`|  
|![Campo de entrada da caixa de combinação no hover](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Campo de entrada**|Borda|`Environment.ComboBoxMouseOverBorder`|  
|![Campo de entrada da caixa de combinação no hover](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Campo de entrada**|Separador|`Environment.ComboBoxMouseOverSeparator`|  
|![Caixa de combinação&#47;baixar&#45;botão no hover](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Botão de drop-down**|Segundo plano|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Caixa de combinação&#47;baixar&#45;botão no hover](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Botão de drop-down**|Primeiro plano (Glifo)|`Environment.ComboBoxMouseOverGlyph`|  
|![Caixa de combinação&#47;cair&#45;lista no hover](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Lista de paradas**|Plano de fundo (item do menu)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Caixa de combinação&#47;cair&#45;lista no hover](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Lista de paradas**|Primeiro plano (Texto)|`Environment.ComboBoxItemMouseOverText`|  
|![Caixa de combinação&#47;cair&#45;lista no hover](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Lista de paradas**|Borda (item do menu)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Focalizado**  
  
|Componente|Elemento|Nome do token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada de caixa combo focado](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Campo de entrada**|Segundo plano|`Environment.ComboBoxFocusedBackground`|  
|![Campo de entrada de caixa combo focado](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Campo de entrada**|Primeiro plano (Texto)|`Environment.ComboBoxFocusedText`|  
|![Campo de entrada de caixa combo focado](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Campo de entrada**|Borda|`Environment.ComboBoxFocusedBorder`|  
|![Campo de entrada de caixa combo focado](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Campo de entrada**|Separador|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Caixa de combinação&#47;botão de queda&#45;para baixo focado](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Botão de drop-down**|Segundo plano|`Environment.ComboBoxFocusedButtonBackground`|  
|![Caixa de combinação&#47;botão de queda&#45;para baixo focado](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Botão de drop-down**|Primeiro plano (Glifo)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada da caixa combo pressionado](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Campo de entrada**|Segundo plano|`Environment.ComboBoxMouseDownBackground`|  
|![Campo de entrada da caixa combo pressionado](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Campo de entrada**|Primeiro plano (Texto)|`Environment.ComboBoxMouseDownText`|  
|![Campo de entrada da caixa combo pressionado](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Campo de entrada**|Borda|`Environment.ComboBoxMouseDownBorder`|  
|![Campo de entrada da caixa combo pressionado](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Campo de entrada**|Separador|`Environment.ComboBoxMouseDownSeparator`|  
|![Caixa de combinação&#47;botão de queda de&#45;pressionado](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Botão de drop-down**|Segundo plano|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Caixa de combinação&#47;botão de queda de&#45;pressionado](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Botão de drop-down**|Primeiro plano (Glifo)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Desativado**  
  
|Componente|Elemento|Nome do token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada da caixa combo desativado](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Campo de entrada**|Segundo plano|`Environment.ComboBoxDisabledBackground`|  
|![Campo de entrada da caixa combo desativado](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Campo de entrada**|Primeiro plano (Texto)|`Environment.ComboBoxDisabledText`|  
|![Campo de entrada da caixa combo desativado](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Campo de entrada**|Borda|`Environment.ComboBoxDisabledBorder`|  
|![Campo de entrada da caixa combo desativado](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Campo de entrada**|Separador|Sem separador|  
|![Caixa de combinação&#47;botão de queda&#45;desativado](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Botão de drop-down**|Segundo plano|Nenhum|  
|![Caixa de combinação&#47;botão de queda&#45;desativado](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Botão de drop-down**|Primeiro plano (Glifo)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a>Drop-down  
  
> [!IMPORTANT]
> As drop-downs são semelhantes às caixas de combinação, mas não possuem regiões de texto editáveis. Se a sua parada inclui uma região de texto editável, use os tokens de cor encontrados na [caixa Combo](../misc/shared-colors.md#BKMK_CommandComboBox).  
  
 ![Queda&#45;linha vermelha](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")  
  
 Usar...  
 quando você está criando controles de lista baixa personalizados.  
  
Não use...  
- para qualquer coisa que não seja semelhante a uma lista de paradas.  

- para caixas de combinação ou botões divididos.  
  
  **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Queda&#45;campo de seleção](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Campo de seleção**|Segundo plano|`Environment.DropDownBackground`|  
|![Queda&#45;campo de seleção](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Campo de seleção**|Primeiro plano (Texto)|`DropDownText`|  
|![Queda&#45;campo de seleção](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Campo de seleção**|Borda|`DropDownBorder`|  
|![Queda&#45;campo de seleção](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Campo de seleção**|Separador|Sem separador|  
|![Botão de abaixar&#45;](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Botão de drop-down**|Segundo plano|Nenhum|  
|![Botão de abaixar&#45;](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Botão de drop-down**|Primeiro plano (Glifo)|`Environment.DropDownGlyph`|  
|![Lista de&#45;de baixa](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Lista de paradas**|Segundo plano|`Environment.DropDownPopupBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Lista de&#45;de baixa](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Lista de paradas**|Primeiro plano (Texto)|`Environment.ComboBoxItemText`|  
|![Lista de&#45;de baixa](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Lista de paradas**|Borda|`Environment.DropDownPopupBorder`|  
|![Lista de&#45;de baixa](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Lista de paradas**|Shadow|`Environment.DropShadowBackground`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Solte&#45;campo de seleção no hover](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Campo de seleção**|Segundo plano|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Solte&#45;campo de seleção no hover](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Campo de seleção**|Primeiro plano (Texto)|`Environment.DropDownMouseOverText`|  
|![Solte&#45;campo de seleção no hover](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Campo de seleção**|Borda|`Environment.DropDownMouseOverBorder`|  
|![Solte&#45;campo de seleção no hover](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Campo de seleção**|Separador|`Environment.DropDownButtonMouseOverSeparator`|  
|![Baixe&#45;botão de desligar no hover](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Botão de drop-down**|Segundo plano|`Environment.DropDownButtonMouseOverBackground`|  
|![Baixe&#45;botão de desligar no hover](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Botão de drop-down**|Primeiro plano (Glifo)|`Environment.DropDownMouseOverGlyph`|  
|![Verda&#45;lista no hover](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Lista de paradas**|Plano de fundo (item do menu)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Verda&#45;lista no hover](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Lista de paradas**|Primeiro plano (Texto)|`Environment.ComboBoxItemMouseOverText`|  
|![Verda&#45;lista no hover](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Lista de paradas**|Borda (item do menu)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;campo de seleção pressionado](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Campo de seleção**|Segundo plano|`Environment.DropDownMouseDownBackground`|  
|![Drop&#45;campo de seleção pressionado](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Campo de seleção**|Primeiro plano (Texto)|`Environment.DropDownMouseDownText`|  
|![Drop&#45;campo de seleção pressionado](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Campo de seleção**|Borda|`Environment.DropDownMouseDownBorder`|  
|![Drop&#45;campo de seleção pressionado](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Campo de seleção**|Separador|`Environment.DropDownButtonMouseDownSeparator`|  
|![Botão de baixar&#45;pressionado](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Botão de drop-down**|Segundo plano|`Environment.DropDownButtonMouseDownBackground`|  
|![Botão de baixar&#45;pressionado](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Botão de drop-down**|Primeiro plano (Glifo)|`Environment.DropDownMouseDownGlyph`|  
  
 **Desativado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Dester&#45;campo de seleção desativado](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Segundo plano|`Environment.DropDownDisabledBackground`|  
|![Dester&#45;campo de seleção desativado](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Primeiro plano (Texto)|`Environment.DropDownDisabledText`|  
|![Dester&#45;campo de seleção desativado](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Borda|`Environment.DropDownDisabledBorder`|  
|![Dester&#45;campo de seleção desativado](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Separador|Sem separador|  
|![Baixar&#45;botão desativado](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Segundo plano|N/D|  
|![Baixar&#45;botão desativado](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Primeiro plano (Glifo)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Botão de divisão  
 Os botões divididos compartilham muitos nomes de tokens com outros controles da barra de comando, como botões, menus e texto da barra de comando. Todas as ações necessárias e nomes de token de botão de baixa são repetidos aqui por conveniência. Listas de parada de botões divididos são implementações de [menus](../misc/shared-colors.md#BKMK_CommandMenus)de barra de comando .  
  
 ![Linha vermelha do botão de divisão](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 Usar...  
 quando você está construindo um botão de divisão personalizado.  
  
Não use...  
- para outros tipos de botões.  

- em qualquer combinação de plano de fundo/primeiro plano que não seja especificada.  
  
  **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão de divisão](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Botão de divisão (padrão)**|Segundo plano|Nenhum|  
|![Botão de divisão](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Botão de divisão (padrão)**|Primeiro plano (Texto)|`Environment.CommandBarTextActive`|  
|![Botão de divisão](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Botão de divisão (padrão)**|Primeiro plano (Glifo)|`Environment.CommandBarSplitButtonGlyph`|  
|![Botão de divisão](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Botão de divisão (padrão)**|Borda|N/D|  
|![Botão de divisão](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Botão de divisão (padrão)**|Separador|N/D|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão de divisão no hover](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Botão de divisão (em pairar)**|Segundo plano|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Botão de divisão no hover](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Botão de divisão (em pairar)**|Primeiro plano (Texto)|`Environment.CommandBarTextHover`|  
|![Botão de divisão no hover](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Botão de divisão (em pairar)**|Primeiro plano (Glifo)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Botão de divisão no hover](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Botão de divisão (em pairar)**|Borda|`Environment.CommandBarBorder`|  
|![Botão de divisão no hover](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Botão de divisão (em pairar)**|Separador|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão de divisão pressionado](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Botão de divisão (pressionado)**|Segundo plano|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Botão de divisão pressionado](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Botão de divisão (pressionado)**|Primeiro plano (Texto)|`Environment.CommandBarTextMouseDown`|  
|![Botão de divisão pressionado](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Botão de divisão (pressionado)**|Primeiro plano (Glifo)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Botão de divisão pressionado](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Botão de divisão (pressionado)**|Borda|`Environment.CommandBarBorder`|  
|![Botão de divisão pressionado](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Botão de divisão (pressionado)**|Separador|N/D|  
  
 **Desativado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão de divisão desativado](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Botão de divisão (desativado)**|Segundo plano|N/D|  
|![Botão de divisão desativado](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Botão de divisão (desativado)**|Primeiro plano (Texto)|`Environment.ComboBoxItemTextInactive`|  
|![Botão de divisão desativado](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Botão de divisão (desativado)**|Primeiro plano (Glifo)|`Environment.CommandBarTextInactive`|  
|![Botão de divisão desativado](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Botão de divisão (desativado)**|Borda|N/D|  
|![Botão de divisão desativado](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Botão de divisão (desativado)**|Separador|N/D|  
  
##### <a name="more-options-and-overflow-buttons"></a>Botões 'Mais opções' e 'Estouro'  
 O botão "Mais opções" é usado quando um grupo de barras de comando é personalizável adicionando ou removendo botões relacionados da barra de comando. O botão "Estouro" aparece quando uma barra de comando é truncada devido à falta de espaço horizontal, e no clique mostra um menu contendo os botões da barra de comando que não podem ser exibidos. As cores desses dois botões são controladas pelo mesmo conjunto de nomes de tokens.  
  
 ![Mais opções em linha vermelha](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 Usar...  
 para botões personalizados 'Mais opções' ou 'Estouro'.  
  
 Não use...  
 para botões que não têm funcionalidade semelhante a um botão 'Mais opções' ou 'Estouro'.  
  
 **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Mais opções](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Mais opções**|Segundo plano|`Environment.CommandBarOptionsBackground`|  
|![Mais opções](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Mais opções**|Primeiro plano (Glifo)|`Environment.CommandBarOptionsGlyph`|  
|![Botão de estouro](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Estouro**|Segundo plano|`Environment.CommandBarOptionsBackground`|  
|![Botão de estouro](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Estouro**|Primeiro plano (Glifo)|`Environment.CommandBarOptionsGlyph`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Mais opções em hover](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Mais opções**|Segundo plano|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Mais opções em hover](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Mais opções**|Primeiro plano (Glifo)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Estouro no pairar](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Estouro**|Segundo plano|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Estouro no pairar](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Estouro**|Primeiro plano (Glifo)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Mais opções pressionadas](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Mais opções**|Segundo plano|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Mais opções pressionadas](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Mais opções**|Primeiro plano (Glifo)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Estouro pressionado](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Estouro**|Segundo plano|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Estouro pressionado](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Estouro**|Primeiro plano (Glifo)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Janelas de documentos  
 Não há necessidade de replicar janelas de documentos, porque elas são fornecidas pelo ambiente visual studio. No entanto, você pode decidir que deseja aproveitar as cores usadas nas janelas de documentos para que sua ida e vida também pareça consistente com esta parte do ambiente do Visual Studio.  
  
 Ao usar tokens de cor da janela do documento, você deve ter cuidado para usá-los apenas para elementos semelhantes, e sempre em pares. Se você não fizer isso, você terá resultados inesperados em sua ui.  
  
#### <a name="document-window-frame"></a>Quadro da janela do documento  
 Janelas de documento podem ser encaixadas no IDE ou flutuando como uma janela separada. Quando uma janela de documento está flutuando fora do IDE, ela ainda fica em um documento bem, e tem cores de fundo, borda, texto e guia que são as mesmas de quando faz parte do IDE. No entanto, o documento fica dentro de um quadro que tem seu próprio plano de fundo, borda e cores de texto. Quando as janelas da ferramenta estão encaixadas bem no documento, elas herdam o comportamento e a cor de suas guias a partir de nomes de tokens de janelas de documento.  
  
 ![Linha vermelha da janela do documento ancorado](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **Janela de documento ancorado**  
  
 ![Janela de documento flutuante em linha vermelha](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **Janela de documento flutuante**  
  
 Usar...  
 em qualquer lugar que você está criando ui que você deseja corresponder à janela do documento.  
  
 Não use...  
 para qualquer ui que você não deseja mudar automaticamente se o shell tiver uma atualização de tema.  
  
 **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|Documento: ancorado ou flutuante|Segundo plano|Depende do tipo de documento|  
|Documento: ancorado ou flutuante|Primeiro plano (Texto)|Depende do tipo de documento|  
|Documento: ancorado ou flutuante|Borda|`Environment.ToolWindowBorder`|  
|![Quadro focado](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Quadro: flutuante, focado**|Segundo plano|`Environment.ToolWindowFloatingFrame`|  
|![Quadro focado](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Quadro: flutuante, focado**|Primeiro plano (Texto)|`Environment.ToolWindowFloatingFrame`|  
|![Quadro focado](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Quadro: flutuante, focado**|Primeiro plano (Glifo)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Quadro focado](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Quadro: flutuante, focado**|Borda|`Environment.MainWindowActiveDefaultBorder`|  
|![Quadro focado](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Quadro: flutuante, focado**|Borda (Glifo)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Definido como transparente|  
|![Quadro desfocado](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Quadro: flutuante, desfocado**|Segundo plano|`Environment.ToolWindowFloatingFrameInactive`|  
|![Quadro desfocado](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Quadro: flutuante, desfocado**|Primeiro plano (Texto)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Quadro desfocado](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Quadro: flutuante, desfocado**|Primeiro plano (Glifo)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Quadro desfocado](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Quadro: flutuante, desfocado**|Borda|`Environment.MainWindowInactiveBorder`|  
|![Quadro desfocado](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Quadro: flutuante, desfocado**|Borda (Glifo)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Definido como transparente|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Quadro focado em pairar](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Quadro: flutuante, focado**|Fundo (Glifo)|`Environment.RaftedWindowButtonHoverActive`|  
|![Quadro focado em pairar](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Quadro: flutuante, focado**|Primeiro plano (Glifo)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Quadro focado em pairar](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Quadro: flutuante, focado**|Borda (Glifo)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Quadro desfocado no hover](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Quadro: flutuante, desfocado**|Fundo (Glifo)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Quadro desfocado no hover](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Quadro: flutuante, desfocado**|Primeiro plano (Glifo)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Quadro desfocado no hover](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Quadro: flutuante, desfocado**|Borda (Glifo)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Quadro focado pressionado](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Quadro: flutuante, focado**|Fundo (Glifo)|`Environment.RaftedWindowButtonDown`|  
|![Quadro focado pressionado](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Quadro: flutuante, focado**|Primeiro plano (Glifo)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Quadro focado pressionado](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Quadro: flutuante, focado**|Borda (Glifo)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Guias de documento  
 As guias de documento ficam no canal da guia para indicar quais documentos estão abertos no momento, juntamente com qual deles é o documento selecionado ou ativo atual. As janelas da ferramenta também podem ser encaixadas no canal da guia de documentos se o usuário as colocar lá. Nesta situação, eles usam as mesmas cores de guia que janelas de documento. Se você estiver criando a ui que deseja sempre corresponder às cores da janela do documento (incluindo atualizações de temas ou se novos temas forem instalados), faça referência a esses tokens de cor.  
  
 ![Linha vermelha da guia do documento](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")  
  
 Usar...  
 em qualquer lugar que você esteja criando ui que você deseja combinar guias de documentos e pegar automaticamente atualizações temáticas ou novas cores temáticas.  
  
 Não use...  
 para qualquer ui que você não queira alterar automaticamente quando o shell tiver uma atualização de tema.  
  
##### <a name="open-document-tabs"></a>Abrir guias de documentos  
 Cada documento aberto tem uma guia no canal da guia de documentos que exibe seu nome. Os documentos podem ser selecionados ou abertos em segundo plano, e suas guias refletem esses estados:  
  
- A guia selecionada representa bem o documento exibido no documento. Uma guia selecionada tem uma borda de documento que se estende pela borda superior do documento.  
  
- Guias de fundo são as guias de documento que não são a guia selecionada no momento. Uma vez clicados, eles se tornam a guia selecionada e adquirem todas as cores de fundo, borda e texto desses nomes de token.  
  
  ![Linha vermelha da guia de documento aberto](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
  Usar...  
  quando você está criando guias personalizadas de documentos.  
  
  Não use...  
  - para guias provisórias (visualização).  
  
- para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema.  
  
##### <a name="selected-tab"></a>Guia selecionada  
 **Focalizado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Focado em guias selecionadas](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Guia de documento selecionada, focada**|Segundo plano|`Environment.FileTabSelectedGradientTop`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Focado em guias selecionadas](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Guia de documento selecionada, focada**|Primeiro plano (Texto)|`Environment.FileTabSelectedText`|  
|![Focado em guias selecionadas](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Guia de documento selecionada, focada**|Borda|`Environment.FileTabSelectedBorder`<br /><br /> Definir para a mesma cor que o fundo.|  
|![Focado em guias selecionadas](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Guia de documento selecionada, focada**|Fronteira do documento|`Environment.FileTabDocumentBorderBackground`|  
  
 **Sem foco**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Guia selecionada desfocada](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Guia de documento selecionado, desfocado**|Segundo plano|`Environment.FileTabInactiveGradientTop`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Guia selecionada desfocada](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Guia de documento selecionado, desfocado**|Primeiro plano (Texto)|`Environment.FileTabInactiveText`|  
|![Guia selecionada desfocada](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Guia de documento selecionado, desfocado**|Borda|`Environment.FileTabInactiveBorder`<br /><br /> Definir para a mesma cor que o fundo.|  
|![Guia selecionada desfocada](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Guia de documento selecionado, desfocado**|Fronteira do documento|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Guia de fundo  
 **Padrão**  
  
|Componente|Elemento|Nome do token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Guia de fundo](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Padrão da guia de fundo**|Segundo plano|`Environment.FileTabBackground`|  
|![Guia de fundo](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Padrão da guia de fundo**|Primeiro plano (Texto)|`Environment.FileTabText`|  
|![Guia de fundo](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Padrão da guia de fundo**|Borda|`Environment.FileTabBorder`<br /><br /> Definir para a mesma cor que o fundo.|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Guia de fundo no hover](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Guia de fundo no hover**|Segundo plano|`Environment.FileTabHotGradientTop`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Guia de fundo no hover](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Guia de fundo no hover**|Primeiro plano (Texto)|`Environment.FileTabHotText`|  
|![Guia de fundo no hover](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Guia de fundo no hover**|Borda|`Environment.FileTabHotBorder`<br /><br /> Definir para a mesma cor que o fundo.|  
  
##### <a name="preview-tab"></a>Guia de visualização  
 A guia de visualização aparece no lado direito do canal da guia do documento quando o usuário clica em um item na janela da ferramenta Solution Explorer. Ele funciona como uma visualização do documento e também dá ao usuário a opção de manter o documento aberto no lado esquerdo do canal da guia do documento. Apenas uma guia de visualização aberta pode ser aberta de cada vez. As guias de visualização têm tanto o plano de fundo quanto os estados selecionados, como guias abertas, e podem ser focadas ou desfocadas em seu estado ativo.  
  
 ![Linha vermelha da guia de visualização](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")  
  
 Usar...  
 em qualquer lugar que você está criando visualização provisória e deseja que algum elemento corresponda à cor da guia de visualização atual.  
  
Não use...  
- para qualquer tipo de documento ou guia que não seja provisória (visualização).  

- para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema.  
  
  **Guia de visualização selecionada: Focado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Foco na guia de visualização](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Guia de visualização focada**|Segundo plano|`Environment.FileTabProvisionalSelectedActive`|  
|![Foco na guia de visualização](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Guia de visualização focada**|Primeiro plano (Texto)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Foco na guia de visualização](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Guia de visualização focada**|Borda|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Definir para a mesma cor que o fundo.|  
|![Foco na guia de visualização](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Guia de visualização focada**|Fronteira do documento|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Guia de visualização selecionada: Desfocada**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Guia de visualização desfocada](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Guia de visualização desfocada**|Segundo plano|`Environment.FileTabProvisionalSelectedInactive`|  
|![Guia de visualização desfocada](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Guia de visualização desfocada**|Primeiro plano (Texto)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Guia de visualização desfocada](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Guia de visualização desfocada**|Borda|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Guia de visualização desfocada](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Guia de visualização desfocada**|Fronteira do documento|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Guia de visualização de fundo: Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Visualizar guia de fundo](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Inserindo a guia de fundo da guia**|Segundo plano|`Environment.FileTabProvisionalInactive`|  
|![Visualizar guia de fundo](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Inserindo a guia de fundo da guia**|Primeiro plano (Texto)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Visualizar guia de fundo](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Inserindo a guia de fundo da guia**|Borda|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Definir para a mesma cor que o fundo.|  
  
 **Guia de visualização de fundo: Hover**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Visualizar guia de fundo no hover](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Visualizar guia de fundo da guia no hover**|Segundo plano|`Environment.FileTabProvisionalHover`|  
|![Visualizar guia de fundo no hover](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Visualizar guia de fundo da guia no hover**|Primeiro plano (Texto)|`Environment.FileTabProvisionalHoverForeground`|  
|![Visualizar guia de fundo no hover](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Visualizar guia de fundo da guia no hover**|Borda|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Definir para a mesma cor que o fundo.|  
  
##### <a name="document-overflow-button"></a>Botão de estouro de documento  
 O botão de estouro de documento está presente se houver um ou mais documentos abertos, independentemente de haver espaço vertical na configuração atual para caber todas as guias do documento. O menu suspenso de estouro de estouro de documento, que é controlado pelas cores **CommandBarMenu** (ver [Menus),](../misc/shared-colors.md#BKMK_CommandMenus)exibe uma lista de todos os documentos abertos, visíveis e ocultos, e o glifo de transbordamento altera dependendo se todos os documentos abertos são exibidos no canal da guia.  
  
 ![Linha vermelha de transbordamento](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")  
  
Usar...  
quando você está criando um botão de estouro de documento personalizado.  

Não use...  
- para iU que não é semelhante a um botão de estouro.  

- para botões de estouro da barra de comando.  
  
  **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Estouro](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Botão de estouro de documento**|Segundo plano|`Environment.DocWellOverflowButtonBackground`|  
|![Estouro](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Botão de estouro de documento**|Primeiro plano (Glifo)|`Environment.DocWellOverflowButtonGlyph`|  
|![Estouro](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Botão de estouro de documento**|Borda|N/D|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Estouro no pairar](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Botão de estouro de documento em pairar**|Segundo plano|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Estouro no pairar](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Botão de estouro de documento em pairar**|Primeiro plano (Glifo)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Estouro no pairar](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Botão de estouro de documento em pairar**|Borda|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Estouro pressionado](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Botão de estouro do documento pressionado**|Segundo plano|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Estouro pressionado](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Botão de estouro do documento pressionado**|Primeiro plano (Glifo)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Estouro pressionado](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Botão de estouro do documento pressionado**|Borda|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Janelas da ferramenta  
 Não há necessidade de replicar janelas de ferramentas, porque elas são fornecidas pelo ambiente visual studio. No entanto, você pode decidir que deseja aproveitar as cores usadas nas janelas das ferramentas para que sua ida e vida também pareça consistente com esta parte do ambiente do Visual Studio.  
  
 ![Linha vermelha da janela da ferramenta](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 Usar...  
 em qualquer lugar que você está criando ui que você deseja combinar janelas de ferramentas.  
  
 Não use...  
 para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema.  
  
#### <a name="tool-window-frame"></a>Quadro da janela da ferramenta  
 Janelas de ferramentas no Visual Studio são usadas para muitas tarefas diferentes, e podem existir em um dos vários estados diferentes. Se uma janela de ferramenta estiver aberta, ela pode ser atribuída a qualquer um dos quatro lados da área do documento. As janelas de ferramentas também podem flutuar fora do IDE, o que permite que eles sejam reposicionados em qualquer lugar dentro da tela do usuário. Janelas flutuantes sempre se sentam em cima do IDE. Finalmente, as janelas das ferramentas podem ser encaixadas como janelas de documentos e aparecer como uma guia no documento bem. Janelas de ferramentas que foram encaixadas como janelas de documentos são coloridas em parte usando nomes de token de janela de documento.  
  
 ![Linha vermelha da janela da ferramenta](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 Usar...  
 em qualquer lugar que você está criando ui que você deseja combinar janelas de ferramentas.  
  
 Não use...  
 para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema.  
  
 **Encaixado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Janela da ferramenta encaixada](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Segundo plano|`Environment.ToolWindowBackground`|  
|![Janela da ferramenta encaixada](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Borda|`Environment.ToolWindowBorder`|  
  
 **Flutuante: focado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Foco na janela da ferramenta](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Segundo plano|`Environment.ToolWindowBackground`|  
|![Foco na janela da ferramenta](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Borda|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Flutuante: desfocado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Janela da ferramenta desfocada](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Segundo plano|`Environment.ToolWindowBackground`|  
|![Janela da ferramenta desfocada](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Borda|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Barra de título da janela da ferramenta  
 A fronteira da barra de título não é uma verdadeira fronteira, mas uma linha grossa do outro lado da barra de título. Ele não tem um nome simbólico para seu estado desfocado.  
  
 ![Linha vermelha da barra do título da janela da ferramenta](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 Usar...  
 em qualquer lugar que você está criando ui que você deseja combinar janelas de ferramentas.  
  
 Não use...  
 para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema.  
  
 **Focalizado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra de título focada](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Barra de título focada**|Segundo plano|`Environment.TitleBarActiveGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Barra de título focada](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Barra de título focada**|Primeiro plano (Texto)|`Environment.TitleBarActiveText`|  
|![Barra de título focada](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Barra de título focada**|Borda|`Environment.TitleBarActiveBorder`<br /><br /> Definir para a mesma cor que o fundo.|  
|![Barra de título focada](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Barra de título focada**|Identificador de arrastar|`Environment.TitleBarDragHandleActive`|  
  
 **Sem foco**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra de título desfocada](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Barra de título desfocada**|Segundo plano|`Environment.TitleBarInactiveGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Barra de título desfocada](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Barra de título desfocada**|Primeiro plano (Texto)|`Environment.TitleBarInactiveText`|  
|![Barra de título desfocada](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Barra de título desfocada**|Borda|N/D|  
|![Barra de título desfocada](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Barra de título desfocada**|Identificador de arrastar|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Botões da barra de título  
 ![Linha vermelha do botão da barra de título](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 Usar...  
 para botões que aparecem em UI que usa tokens de cor das barras de título da janela da ferramenta.  
  
Não use...  
- para botões que aparecem em outros locais.  

- em qualquer combinação de plano de fundo/primeiro plano que não seja especificada.  
  
  **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão da barra de título focado](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focalizado**|Segundo plano|N/D|  
|![Botão da barra de título focado](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focalizado**|Primeiro plano (Glifo)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Botão da barra de título focado](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focalizado**|Borda|N/D|  
|![Botão da barra de título desfocado](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Sem foco**|Segundo plano|N/D|  
|![Botão da barra de título desfocado](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Sem foco**|Primeiro plano (Glifo)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Botão da barra de título desfocado](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Sem foco**|Borda|N/D|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão da barra de título focado em hover](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focalizado**|Segundo plano|`Environment.ToolWindowButtonHoverActive`|  
|![Botão da barra de título focado em hover](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focalizado**|Primeiro plano (Glifo)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Botão da barra de título focado em hover](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focalizado**|Borda|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Botão da barra de título desfocado no hover](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Sem foco**|Segundo plano|`Environment.ToolWindowButtonHoverInactive`|  
|![Botão da barra de título desfocado no hover](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Sem foco**|Primeiro plano (Glifo)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Botão da barra de título desfocado no hover](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Sem foco**|Borda|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão da barra de título focado e pressionado](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focalizado**|Segundo plano|`Environment.ToolWindowButtonDown`|  
|![Botão da barra de título focado e pressionado](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focalizado**|Primeiro plano (Glifo)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Botão da barra de título focado e pressionado](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focalizado**|Borda|`Environment.ToolWindowButtonDownBorder`|  
|![Botão da barra de título desfocado e pressionado](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Sem foco**|Segundo plano|`Environment.ToolWindowButtonDown`|  
|![Botão da barra de título desfocado e pressionado](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Sem foco**|Primeiro plano (Glifo)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Botão da barra de título desfocado e pressionado](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Sem foco**|Borda|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Guias de janela de ferramenta  
 ![Linha vermelha da guia da janela da ferramenta](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 Usar...  
 em qualquer lugar que você está criando ui que você deseja combinar janelas de ferramentas.  
  
 Não use...  
 para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema.  
  
 **Guia selecionada**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Focado na guia da janela da ferramenta](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Guia de janela de ferramenta selecionada e focada**|Segundo plano|`Environment.ToolWindowTabSelectedTab`|  
|![Focado na guia da janela da ferramenta](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Guia de janela de ferramenta selecionada e focada**|Primeiro plano (Texto)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Focado na guia da janela da ferramenta](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Guia de janela de ferramenta selecionada e focada**|Borda|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Definir para a mesma cor que o fundo.|  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Guia da janela da ferramenta desfocada](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Guia de janela de ferramenta selecionada e desfocada**|Segundo plano|`Environment.ToolWindowTabSelectedTab`|  
|![Guia da janela da ferramenta desfocada](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Guia de janela de ferramenta selecionada e desfocada**|Primeiro plano (Texto)|`Environment.ToolWindowTabSelectedText`|  
|![Guia da janela da ferramenta desfocada](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Guia de janela de ferramenta selecionada e desfocada**|Borda|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Definir para a mesma cor que o fundo.|  
  
 **Guia de fundo**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Guia de fundo da janela da ferramenta](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Guia da janela da ferramenta de fundo**|Segundo plano|`Environment.ToolWindowTabGradientBegin`<br /><br /> O gradiente pára definido para o mesmo valor de cor no Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> O gradiente pára definido para o mesmo valor de cor no Visual Studio 2013.|  
|![Guia de fundo da janela da ferramenta](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Guia da janela da ferramenta de fundo**|Primeiro plano (Texto)|`Environment.ToolWindowTabText`|  
|![Guia de fundo da janela da ferramenta](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Guia da janela da ferramenta de fundo**|Borda|`Environment.ToolWindowTabBorder`|  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Guia de fundo da janela da ferramenta em hover](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Guia da janela da ferramenta de fundo no hover**|Segundo plano|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> O gradiente pára definido para o mesmo valor de cor no Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> O gradiente pára definido para o mesmo valor de cor no Visual Studio 2013.|  
|![Guia de fundo da janela da ferramenta em hover](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Guia da janela da ferramenta de fundo no hover**|Primeiro plano (Texto)|`Environment.ToolWindowTabMouseOverText`|  
|![Guia de fundo da janela da ferramenta em hover](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Guia da janela da ferramenta de fundo no hover**|Borda|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Definir para a mesma cor que o fundo.|  
  
#### <a name="auto-hide-tabs"></a>Guias de ocultação automática  
 ![Auto&#45;escondem linha vermelha](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")  
  
 Usar...  
 em qualquer lugar que você está criando ui que você deseja combinar guias de janela de ferramenta automaticamente ocultas.  
  
 Não use...  
 para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema.  
  
 **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Guia de ocultação de&#45;automática](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Guia padrão de ocultação automática**|Segundo plano|`Environment.AutoHideTabBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Guia de ocultação de&#45;automática](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Guia padrão de ocultação automática**|Primeiro plano (Texto)|`Environment.AutoHideTabText`|  
|![Guia de ocultação de&#45;automática](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Guia padrão de ocultação automática**|Borda|`Environment.AutoHideTabBorder`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Auto&#45;ocultar guia no hover](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Guia de ocultação automática no hover**|Segundo plano|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Auto&#45;ocultar guia no hover](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Guia de ocultação automática no hover**|Primeiro plano (Texto)|`Environment.AutoHideTabMouseOverText`|  
|![Auto&#45;ocultar guia no hover](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Guia de ocultação automática no hover**|Borda|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Controles compartilhados comuns  
 Quando você usa uma barra de comando padrão do Visual Studio em seu recurso, você terá acesso a controles shell estilizados, e não deve remodelar esses controles comuns. No entanto, se você precisar construir uma barra de comando personalizada, talvez seja necessário construir controles personalizados também. Nesse caso, certifique-se de usar os nomes de token corretos para cada um dos seguintes controles para que sua iu é consistente com o resto do Visual Studio.  
  
#### <a name="search-box"></a>Caixa de pesquisa  
 Sempre que possível, use o controle de pesquisa comum fornecido pelo ambiente visual studio. As cores da caixa de pesquisa são encontradas na categoria "SearchControl" no arquivo **ShellColors.pkgdef,** que contém nomes de tokens para o campo de entrada, botão de ação, botão suspenso e menu suspenso.  
  
 Uma caixa de pesquisa pode ser um dos vários estados, alguns dos quais são mutuamente exclusivos:  
  
- "Focado" ou "desfocado" refere-se a se o cursor está ou não na caixa de texto.  
  
- "Ativo" ou "inativo" refere-se a saber se o usuário insenou uma consulta de pesquisa na caixa de texto.  
  
- "Hover" significa que o usuário passou rato sobre a caixa de pesquisa com o mouse (este estado substitui todos os outros estados).  
  
- "Desativado" significa que a funcionalidade de pesquisa está desativada para o contexto atual.  
  
  ![Linha vermelha da caixa de pesquisa](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")  
  
  Usar...  
  quando você está projetando uma caixa de pesquisa personalizada.  
  
  Não use...  
  - para qualquer coisa que não seja uma caixa de pesquisa.  
  
- para qualquer coisa que você não quer sempre corresponder à ui caixa de pesquisa.  
  
  **Focalizado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada de pesquisa focado](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Campo de entrada**|Segundo plano|`SearchControl.FocusedBackground`|  
|![Campo de entrada de pesquisa focado](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Campo de entrada**|Primeiro plano (Texto)|`SearchControl.FocusedBackground`|  
|![Campo de entrada de pesquisa focado](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Campo de entrada**|Borda|`SearchControl.FocusedBorder`|  
|![Campo de entrada de pesquisa focado](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Campo de entrada**|Separador|`SearchControl.FocusedDropDownSeparator`|  
|![Botão de ação de pesquisa focado](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Botão de ação**|Segundo plano|Nenhum|  
|![Botão de ação de pesquisa focado](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Botão de ação**|Primeiro plano (Glyph de pesquisa)|`SearchControl.SearchGlyph`|  
|![Botão de ação de pesquisa focado](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Botão de ação**|Primeiro plano (Pare o glifo)|`SearchControl.StopGlyph`|  
|![Botão de ação de pesquisa focado](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Botão de ação**|Primeiro plano (Limpar glifo)|`SearchControl.ClearGlyph`|  
|![Botão de ação de pesquisa focado](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Botão de ação**|Borda|N/D|  
|![Pesquisa drop&#45;botão para baixo focado](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Botão de drop-down**|Segundo plano|`SearchControl.FocusedDropDownButton`|  
|![Pesquisa drop&#45;botão para baixo focado](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Botão de drop-down**|Primeiro plano (Glifo)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Pesquisa drop&#45;botão para baixo focado](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Botão de drop-down**|Borda|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Sem foco**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada de pesquisa desfocado](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Campo de entrada ativo**|Segundo plano|`SearchControl.SearchActiveBackground`|  
|![Campo de entrada de pesquisa desfocado](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Campo de entrada ativo**|Primeiro plano (Texto)|`SearchControl.SearchActiveBackground`|  
|![Campo de entrada de pesquisa desfocado](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Campo de entrada ativo**|Borda|`SearchControl.UnfocusedBorder`|  
|![Campo de entrada de pesquisa desfocado](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Campo de entrada ativo**|Separador|`SearchControl.DropDownSeparator`|  
|![Campo de entrada de pesquisa desfocado e inativo](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Campo de entrada inativo**|Segundo plano|`SearchControl.Unfocused`|  
|![Campo de entrada de pesquisa desfocado e inativo](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Campo de entrada inativo**|Primeiro plano (Texto)|`SearchControl.Unfocused`|  
|![Campo de entrada de pesquisa desfocado e inativo](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Campo de entrada inativo**|Borda|`SearchControl.UnfocusedBorder`|  
|![Campo de entrada de pesquisa desfocado e inativo](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Campo de entrada inativo**|Separador|`SearchControl.DropDownSeparator`|  
|![Botão de ação de pesquisa desfocado](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Botão de ação**|Segundo plano|N/D|  
|![Botão de ação de pesquisa desfocado](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Botão de ação**|Primeiro plano (Glyph de pesquisa)|`SearchControl.SearchGlyph`|  
|![Botão de ação de pesquisa desfocado](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Botão de ação**|Primeiro plano (Pare o glifo)|`SearchControl.StopGlyph`|  
|![Botão de ação de pesquisa desfocado](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Botão de ação**|Primeiro plano (Limpar glifo)|`SearchControl.ClearGlyph`|  
|![Botão de ação de pesquisa desfocado](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Botão de ação**|Borda|N/D|  
|![Pesquisar botão de saque&#45;desfocado](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Botão de drop-down**|Segundo plano|`SearchControl.UnfocusedDropDownButton`|  
|![Pesquisar botão de saque&#45;desfocado](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Botão de drop-down**|Primeiro plano (Glifo)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Pesquisar botão de saque&#45;desfocado](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Botão de drop-down**|Borda|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão de ação de pesquisa pressionado](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Botão de ação**|Segundo plano|`SearchControl.ActionButtonMouseDown`|  
|![Botão de ação de pesquisa pressionado](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Botão de ação**|Primeiro plano (Glifo)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Botão de ação de pesquisa pressionado](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Botão de ação**|Borda|`SearchControl.ActionButtonMouseDownBorder`|  
|![Pesquisa botão de queda&#45;pressionado](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Botão de drop-down**|Segundo plano|`SearchControl.MouseDownDropDownButton`|  
|![Pesquisa botão de queda&#45;pressionado](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Botão de drop-down**|Primeiro plano (Glifo)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Pesquisa botão de queda&#45;pressionado](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Botão de drop-down**|Borda|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Destaque (somente texto)**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Destaque do campo de entrada de pesquisa](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Campo de entrada com texto destacado**|Segundo plano|`SearchControl.Selection`|  
|![Destaque do campo de entrada de pesquisa](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Campo de entrada com texto destacado**|Primeiro plano (Texto)|`SearchControl.FocusedBackground`|  
|![Destaque do campo de entrada de pesquisa](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Campo de entrada com texto destacado**|Borda|Nenhum|  
|![Destaque do campo de entrada de pesquisa](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Campo de entrada com texto destacado**|Separador|`SearchControl.FocusedDropDownSeparator`|  
  
 **Desativado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada de pesquisa desativado](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Campo de entrada**|Segundo plano|`SearchControl.Disabled`|  
|![Campo de entrada de pesquisa desativado](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Campo de entrada**|Primeiro plano (Texto)|`SearchControl.Disabled`|  
|![Campo de entrada de pesquisa desativado](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Campo de entrada**|Borda|`SearchControl.DisabledBorder`|  
|![Campo de entrada de pesquisa desativado](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Campo de entrada**|Separador|`SearchControl.DropDownSeparator`|  
|![Botão de ação de pesquisa desativado](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Botão de ação**|Segundo plano|Nenhum|  
|![Botão de ação de pesquisa desativado](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Botão de ação**|Primeiro plano (Glifo)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Botão de ação de pesquisa desativado](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Botão de ação**|Borda|Nenhum|  
|![Pesquisa soltar botão&#45;desativado](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Botão de drop-down**|Segundo plano|Nenhum|  
|![Pesquisa soltar botão&#45;desativado](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Botão de drop-down**|Primeiro plano (Glifo)|`SearchControl.DisabledDownButtonGlyph`|  
|![Pesquisa soltar botão&#45;desativado](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Botão de drop-down**|Borda|Nenhum|  
  
##### <a name="search-drop-down-lists"></a>Pesquisar listas de paradas  
 O menu suspenso da caixa de pesquisa tem o potencial de ser um pouco mais complexo do que outros menus suspensos no Visual Studio. As seções "pesquisas sugeridas" e "opções de pesquisa" podem aparecer sozinhas ou juntas no menu e cada uma é colorida separadamente. Uma linha também separa essas duas seções quando elas aparecem juntas e uma borda cerca todo o menu suspenso.  
  
 ![Queda de pesquisa&#45;para baixo linha vermelha](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
Usar...  
- quando você está criando uma lista de sossede de pesquisa personalizada.  

- os nomes de token corretos para os componentes corretos da lista.  

Não use...  
- para listas de saque que aparecem em outros contextos.  

- em qualquer combinação de plano de fundo/primeiro plano que não seja especificada.  
  
  **Inadimplência (sem outros estados)**  
  
|Elemento|Nome do token: Category.color|  
|-------------|--------------------------------|  
|Borda|`SearchControl.PopupBorder`|  
|Separador|`SearchControl.PopupSectionHeaderSeparator`|  
|Shadow|`Environment.DropShadowBackground`|  
  
 **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pesquisa sugerida](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Pesquisas sugeridas**|Segundo plano|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Pesquisa sugerida](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Pesquisas sugeridas**|Primeiro plano (Texto)|`SearchControl.PopupItemText`|  
|![Caixa de seleção de pesquisa](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opções de pesquisa (caixa de seleção)**|Segundo plano|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Opções de pesquisa](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opções de pesquisa (link)**|Segundo plano|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Caixa de seleção de pesquisa](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opções de pesquisa (caixa de seleção)**|Primeiro plano (Texto da caixa de seleção)|`SearchControl.PopupCheckboxText`|  
|![Opções de pesquisa](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opções de pesquisa (link)**|Primeiro plano (Texto da caixa de seleção)|`SearchControl.PopupCheckboxText`|  
|![Caixa de seleção de pesquisa](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opções de pesquisa (caixa de seleção)**|Primeiro plano (texto de link)|`SearchControl.PopupButtonText`|  
|![Opções de pesquisa](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opções de pesquisa (link)**|Primeiro plano (texto de link)|`SearchControl.PopupButtonText`|  
|![Caixa de seleção de pesquisa](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opções de pesquisa (caixa de seleção)**|Fundo do cabeçalho|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Opções de pesquisa](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opções de pesquisa (link)**|Fundo do cabeçalho|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Caixa de seleção de pesquisa](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opções de pesquisa (caixa de seleção)**|Primeiro plano (texto de cabeçalho)|`SearchControl.PopupSectionHeaderText`|  
|![Opções de pesquisa](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opções de pesquisa (link)**|Primeiro plano (texto de cabeçalho)|`SearchControl.PopupSectionHeaderText`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pesquisa sugerida no hover](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Pesquisas sugeridas**|Segundo plano|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Pesquisa sugerida no hover](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Pesquisas sugeridas**|Primeiro plano (Texto)|`SearchControl.PopupMouseOverItemText`|  
|![Pesquisa sugerida no hover](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Pesquisas sugeridas**|Borda|`SearchControl.PopupControlMouseOverBorder`|  
|![Caixa de seleção de pesquisa em hover](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Pesquisas sugeridas (caixa de seleção)**|Segundo plano|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Opções de pesquisa no hover](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opções de pesquisa**|Segundo plano|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Caixa de seleção de pesquisa em hover](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Pesquisas sugeridas (caixa de seleção)**|Primeiro plano (Texto da caixa de seleção)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Opções de pesquisa no hover](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opções de pesquisa**|Primeiro plano (Texto da caixa de seleção)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Caixa de seleção de pesquisa em hover](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Pesquisas sugeridas (caixa de seleção)**|Primeiro plano (texto de link)|`SearchControl.PopupButtonMouseDownText`|  
|![Opções de pesquisa no hover](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opções de pesquisa**|Primeiro plano (texto de link)|`SearchControl.PopupButtonMouseDownText`|  
|![Caixa de seleção de pesquisa em hover](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Pesquisas sugeridas (caixa de seleção)**|Borda|`SearchControl.PopupControlMouseOverBorder`|  
|![Opções de pesquisa no hover](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opções de pesquisa**|Borda|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pesquisa sugerida pressionada](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Pesquisas sugeridas (caixa de seleção)**|Versá-lo em segundo plano|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Opções de pesquisa pressionadas](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opções de pesquisa**|Versá-lo em segundo plano|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Pesquisa sugerida pressionada](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Pesquisas sugeridas (caixa de seleção)**|Versá-lo em segundo plano|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Opções de pesquisa pressionadas](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opções de pesquisa**|Versá-lo em segundo plano|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Pesquisa sugerida pressionada](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Pesquisas sugeridas (caixa de seleção)**|Primeiro plano (Texto da caixa de seleção)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Opções de pesquisa pressionadas](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opções de pesquisa**|Primeiro plano (Texto da caixa de seleção)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Pesquisa sugerida pressionada](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Pesquisas sugeridas (caixa de seleção)**|Fundo de link|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Opções de pesquisa pressionadas](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opções de pesquisa**|Fundo de link|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Embora não seja usado em iu temática moderna, existem paradas de gradiente e valores para este fundo.|  
|![Pesquisa sugerida pressionada](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Pesquisas sugeridas (caixa de seleção)**|Primeiro plano (texto de link)|`SearchControl.PopupButtonMouseDownText`|  
|![Opções de pesquisa pressionadas](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opções de pesquisa**|Primeiro plano (texto de link)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Hyperlink  
 O hiperlink é um controle que não tem um par de primeiro plano/fundo. Em todos os casos, use a cor do hiperlink em primeiro plano, que aparecerá corretamente em fundos escuros, cinzas e brancos. Se você não usar o token de cor para o controle de hiperlink, você verá a cor padrão do sistema para "pressionado", que piscará em vermelho. Esse é o sinal de que o controle não está usando o token de cor do ambiente correto.  
  
 ![Linha vermelha hyperlink](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 Usar...  
 quando você precisa criar um hiperlink personalizado.  
  
 Não use...  
 para qualquer coisa que não seja um hiperlink.  
  
 **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Padrão de hiperlink](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")|Primeiro plano (Texto)|`Environment.PanelHyperlink`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hiperlink em hover](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")|Primeiro plano (Texto)|`Environment.PanelHyperlinkHover`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hiperlink pressionado](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")|Primeiro plano (Texto)|`Environment.PanelHyperlinkPressed`|  
  
 **Desativado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hiperlink desativado](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")|Primeiro plano (Texto)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Barra  
 As barras de infosão são usadas para fornecer mais informações sobre um determinado contexto e sempre aparecem no topo de uma janela de documento ou janela de ferramenta.  
  
 ![Linha vermelha infobar](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")  
  
 Usar...  
 ao criar infobarras personalizados.  
  
 Não use...  
 para elementos de IA que não são semelhantes a uma barra de informações.  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Barra**|Segundo plano|`Environment.InfoBackground`|  
|![Barra](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Barra**|Primeiro plano (Texto)|`Environment.InfoText`|  
|![Barra](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Barra**|Borda|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Barra de rolagem  
 As barras de rolagem são estilizadas pelo ambiente visual studio e não precisarão ser temáticas. No entanto, você pode decidir que deseja aproveitar as cores usadas nas barras de rolagem para que sua iu de ida e vida sempre pareça consistente com esta parte do ambiente do Visual Studio.  
  
 ![Linha vermelha da barra de rolagem](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 Usar...  
 quando você está criando ui que você deseja combinar scrollbars Visual Studio.  
  
 Não use...  
 para qualquer coisa que você não quer sempre corresponder scrollbar UI.  
  
 **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra de rolagem](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Scrollbar**|Scrollbar|`Environment.ScrollBarBackground`|  
|![Barra de rolagem](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Scrollbar**|Primeiro plano (Polegar)|`Environment.ScrollBarThumbBackground`|  
|![Seta da barra de rolagem](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Seta de rolagem**|Segundo plano|`Environment.ScrollBarArrowBackground`<br /><br /> Defina para a mesma cor da barra de rolagem.|  
|![Seta da barra de rolagem](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Seta de rolagem**|Primeiro plano (Glifo)|`Environment.ScrollBarArrowGlyph`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra de rolagem em hover](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Scrollbar**|Scrollbar|`Environment.ScrollBarBackground`|  
|![Barra de rolagem em hover](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Scrollbar**|Primeiro plano (Polegar)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![Seta da barra de rolagem no hover](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Seta de rolagem**|Segundo plano|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Defina para a mesma cor da barra de rolagem.|  
|![Seta da barra de rolagem no hover](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Seta de rolagem**|Primeiro plano (Glifo)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra de rolagem pressionada](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Scrollbar**|Scrollbar|`Environment.ScrollBarBackground`|  
|![Barra de rolagem pressionada](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Scrollbar**|Primeiro plano (Polegar)|`Environment.ScrollBarThumbPressedBackground`|  
|![Seta da barra de rolagem pressionada](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Seta de rolagem**|Segundo plano|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Definir para a mesma cor que a barra de rolagem.|  
|![Seta da barra de rolagem pressionada](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Seta de rolagem**|Primeiro plano (Glifo)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="tree-view"></a><a name="BKMK_TreeView"></a>Vista da árvore  
 Várias janelas de ferramentas, incluindo o Solution Explorer, Server Explorer e Class View, implementam um esquema organizacional hierárquico cujas cores são controladas por nomes de cores na categoria TreeView. Todos os itens em uma visualização de árvore têm cores de fundo e texto. Os itens que possuem elementos infantis aninhados também têm glifos que indicam se o item é expandido ou colapsado.  
  
 ![Linha vermelha da vista da árvore](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")  
  
 Usar...  
 em qualquer lugar que você precisa para implementar uma visão organizacional hierárquica.  
  
Não use...  
- para qualquer coisa que não seja semelhante a uma visão de árvore.  

- em qualquer combinação de plano de fundo/primeiro plano que não seja especificada.  
  
  **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vista da árvore](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Segundo plano|`TreeView.Background`|  
|![Vista da árvore](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Primeiro plano (Texto)|`TreeView.Background`|  
|![Vista da árvore](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Primeiro plano (Glifo)|`TreeView.Glyph`|  
|![Vista da árvore](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Borda|Nenhum|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vista da árvore no pairar](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Segundo plano|`TreeView.Background`|  
|![Vista da árvore no pairar](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Primeiro plano (Texto)|`TreeView.Background`|  
|![Vista da árvore no pairar](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Primeiro plano (Glifo)|`TreeView.GlyphMouseOver`|  
|![Vista da árvore no pairar](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Borda|Nenhum|  
  
 **Arraste**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Arrastão de vista de árvore](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Segundo plano|`TreeView.DragOverItem`|  
|![Arrastão de vista de árvore](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Primeiro plano (Texto)|`TreeView.DragOverItem`|  
|![Arrastão de vista de árvore](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Primeiro plano (Glifo)|`TreeView.DragOverItemGlyph`|  
|![Arrastão de vista de árvore](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Borda|Nenhum|  
  
 **Selecionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Visão da árvore focada](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focalizado**|Segundo plano|`TreeView.SelectedItemActive`|  
|![Visão da árvore focada](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focalizado**|Primeiro plano (Texto)|`TreeView.SelectedItemActive`|  
|![Visão da árvore focada](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focalizado**|Primeiro plano (Glifo)|`TreeView.SelectedItemActiveGlyph`|  
|![Visão da árvore focada](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focalizado**|Borda|`TreeView.FocusVisualBorder`|  
|![Vista da árvore desfocada](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Sem foco**|Segundo plano|`TreeView.SelectedItemInactive`|  
|![Vista da árvore desfocada](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Sem foco**|Primeiro plano (Texto)|`TreeView.SelectedItemInactive`|  
|![Vista da árvore desfocada](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Sem foco**|Primeiro plano (Glifo)|`TreeView.SelectedItemInactiveGlyph`|  
|![Vista da árvore desfocada](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Sem foco**|Borda|Nenhum|  
  
 **Passar o tempo sobre selecionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vista da árvore focada em pairar](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focalizado**|Segundo plano|`TreeView.SelectedItemActive`|  
|![Vista da árvore focada em pairar](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focalizado**|Primeiro plano (Texto)|`TreeView.SelectedItemActive`|  
|![Vista da árvore focada em pairar](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focalizado**|Primeiro plano (Glifo)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Vista da árvore focada em pairar](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focalizado**|Borda|Nenhum`TreeView.FocusVisualBorder`|  
|![Vista da árvore desfocada no pairar](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Sem foco**|Segundo plano|`TreeView.SelectedItemInactive`|  
|![Vista da árvore desfocada no pairar](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Sem foco**|Primeiro plano (Texto)|`TreeView.SelectedItemInactive`|  
|![Vista da árvore desfocada no pairar](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Sem foco**|Primeiro plano (Glifo)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Vista da árvore desfocada no pairar](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Sem foco**|Borda|Nenhum|  
  
#### <a name="button-controls"></a>Controles de botão  
 ![Linha vermelha do controle de botão](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 Usar...  
 para botões no documento bem que você deseja integrar com os temas do Visual Studio (Luz, Escuro, Azul ou um tema de alto contraste do sistema).  
  
 Não use...  
 para botões que serão exibidos em um plano de fundo personalizado que não faz parte de um tema do Visual Studio.  
  
 **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Botão|`CommonControls.Button`|  
|![Botão](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Borda do botão|`CommonControls.ButtonBorder`|  
  
 **Desativado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão desativado](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Botão|`CommonControls.ButtonDisabled`|  
|![Botão desativado](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Borda do botão|`CommonControls.ButtonBorderDisabled`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão em pairar](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Botão|`CommonControls.ButtonHover`|  
|![Botão em pairar](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Borda do botão|`CommonControls.ButtonBorderHover`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão pressionado](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Botão|`CommonControls.ButtonPressed`|  
|![Botão pressionado](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Borda do botão|`CommonControls.ButtonBorderPressed`|  
  
 **Focalizado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botão focado](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Botão|`CommonControls.ButtonFocused`|  
|![Botão focado](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Borda do botão|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Controles da caixa de seleção  
 ![Linha vermelha da caixa de seleção](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")  
  
 Usar...  
 para controles de caixa de seleção contidos dentro do documento bem.  
  
 Não use...  
 para qualquer ui que não seja um controle de caixa de seleção.  
  
 **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Caixa de seleção](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Segundo plano|`CommonControls.CheckBoxBackground`|  
|![Caixa de seleção](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Borda|`CommonControls.CheckBoxBorder`|  
|![Caixa de seleção](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Texto|`CommonControls.CheckBoxText`|  
|![Caixa de seleção](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Glifo|`CommonControls.CheckBoxGlyph`|  
  
 **Desativado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Caixa de seleção desativada](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Segundo plano|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Caixa de seleção desativada](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Borda|`CommonControls.CheckBoxBorderDisabled`|  
|![Caixa de seleção desativada](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Texto|`CommonControls.CheckBoxTextDisabled`|  
|![Caixa de seleção desativada](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Glifo|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Caixa de seleção em hover](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Segundo plano|`CommonControls.CheckBoxBackgroundHover`|  
|![Caixa de seleção em hover](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Borda|`CommonControls.CheckBoxBorderHover`|  
|![Caixa de seleção em hover](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Texto|`CommonControls.CheckBoxTextHover`|  
|![Caixa de seleção em hover](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Glifo|`CommonControls.CheckBoxGlyphHover`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Caixa de seleção pressionada](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Segundo plano|`CommonControls.CheckBoxBackgroundPressed`|  
|![Caixa de seleção pressionada](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Borda|`CommonControls.CheckBoxBorderPressed`|  
|![Caixa de seleção pressionada](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Texto|`CommonControls.CheckBoxTextPressed`|  
|![Caixa de seleção pressionada](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Glifo|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Focalizado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Caixa de seleção focada](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Segundo plano|`CommonControls.CheckBoxBackgroundFocused`|  
|![Caixa de seleção focada](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Borda|`CommonControls.CheckBoxBorderFocused`|  
|![Caixa de seleção focada](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Texto|`CommonControls.CheckBoxTextFocused`|  
|![Caixa de seleção focada](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Glifo|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Controles de caixa de gota/combo  
 ![Queda&#45;para baixo&#47;caixa de combinação linha vermelha](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
Usar...  
para drop-downs e caixas de combinação que fazem parte do documento bem.  

Não use...  
- para qualquer ui que não seja uma caixa de parada ou combo.  

- para uma [caixa Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown) ou [Combo](../misc/shared-colors.md#BKMK_CommandComboBox) na barra de comando.  
  
  **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;para baixo caixa de combinação de&#47;](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Segundo plano|`CommonControls.ComboBoxBackground`|  
|![Drop&#45;para baixo caixa de combinação de&#47;](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Borda|`CommonControls.ComboBoxBorder`|  
|![Drop&#45;para baixo caixa de combinação de&#47;](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Texto|`CommonControls.ComboBoxText`|  
|![Drop&#45;para baixo caixa de combinação de&#47;](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Separador|`CommonControls.ComboBoxSeparator`|  
|![Drop&#45;para baixo caixa de combinação de&#47;](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Glifo|`CommonControls.ComboBoxGlyph`|  
|![Drop&#45;para baixo caixa de combinação de&#47;](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Fundo glifos|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Desativado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Queda&#45;para baixo caixa de combo de&#47;desativada](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Segundo plano|`CommonControls.ComboBoxBackgroundDisabled`|  
|![Queda&#45;para baixo caixa de combo de&#47;desativada](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Borda|`CommonControls.ComboBoxBorderDisabled`|  
|![Queda&#45;para baixo caixa de combo de&#47;desativada](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Texto|`CommonControls.ComboBoxTextDisabled`|  
|![Queda&#45;para baixo caixa de combo de&#47;desativada](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Separador|`CommonControls.ComboBoxSeparatorDisabled`|  
|![Queda&#45;para baixo caixa de combo de&#47;desativada](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Glifo|`CommonControls.ComboBoxGlyphDisabled`|  
|![Queda&#45;para baixo caixa de combo de&#47;desativada](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Fundo glifos|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Baixe&#45;caixa de combo de&#47;no hover](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Segundo plano|`CommonControls.ComboBoxBackgroundHover`|  
|![Baixe&#45;caixa de combo de&#47;no hover](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Borda|`CommonControls.ComboBoxBorderHover`|  
|![Baixe&#45;caixa de combo de&#47;no hover](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Texto|`CommonControls.ComboBoxTextHover`|  
|![Baixe&#45;caixa de combo de&#47;no hover](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Separador|`CommonControls.ComboBoxSeparatorHover`|  
|![Baixe&#45;caixa de combo de&#47;no hover](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Glifo|`CommonControls.ComboBoxGlyphHover`|  
|![Baixe&#45;caixa de combo de&#47;no hover](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Fundo glifos|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;down&#47;caixa de combinação pressionada](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Segundo plano|`CommonControls.ComboBoxBackgroundPressed`|  
|![Drop&#45;down&#47;caixa de combinação pressionada](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Borda|`CommonControls.ComboBoxBorderPressed`|  
|![Drop&#45;down&#47;caixa de combinação pressionada](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Texto|`CommonControls.ComboBoxTextPressed`|  
|![Drop&#45;down&#47;caixa de combinação pressionada](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Separador|`CommonControls.ComboBoxSeparatorPressed`|  
|![Drop&#45;down&#47;caixa de combinação pressionada](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Glifo|`CommonControls.ComboBoxGlyphPressed`|  
|![Drop&#45;down&#47;caixa de combinação pressionada](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Fundo glifos|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Focalizado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;down&#47;caixa de combinação focada](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Segundo plano|`CommonControls.ComboBoxBackgroundFocused`|  
|![Drop&#45;down&#47;caixa de combinação focada](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Borda|`CommonControls.ComboBoxBorderFocused`|  
|![Drop&#45;down&#47;caixa de combinação focada](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Texto|`CommonControls.ComboBoxTextFocused`|  
|![Drop&#45;down&#47;caixa de combinação focada](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Separador|`CommonControls.ComboBoxSeparatorFocused`|  
|![Drop&#45;down&#47;caixa de combinação focada](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Glifo|`CommonControls.ComboBoxGlyphFocused`|  
|![Drop&#45;down&#47;caixa de combinação focada](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Fundo glifos|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Seleção de entrada de texto**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Baixar&#45;entrada de texto da caixa de combo&#47;](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")|Realçar|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Pressionado – Exibição de item de lista**  
  
|Componente|Elemento|Nome do token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Segundo plano|`CommonControls.ComboBoxListBackground`|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Segundo plano|`CommonControls.ComboBoxListBackgroundHover`|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Segundo plano|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Segundo plano|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Borda|`CommonControls.ComboBoxListBorder`|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Borda|`CommonControls.ComboBoxListBorderHover`|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Borda|`CommonControls.ComboBoxListBorderPressed`|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Borda|`CommonControls.ComboBoxListBorderFocused`|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Texto do item|`CommonControls.ComboBoxListItemText`|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Texto do item|`CommonControls.ComboBoxListItemTextHover`|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Texto do item|`CommonControls.ComboBoxListItemTextPressed`|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Texto do item|`CommonControls.ComboBoxListItemTextFocused`|  
|![Baixar&#45;exibição da lista de caixas combo de&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Sombra de fundo|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Controles de dados tabulares (grade)  
 Os controles de dados tabulares, também conhecidos como controles de grade, são controles comuns para o Visual Studio que podem ser usados para apresentar grandes quantidades de dados em várias colunas. Os controles de dados tabulares padrão podem ser encontrados em vários lugares dentro do Visual Studio: a janela da ferramenta Lista de erros, os relatórios do IntelliTrace e a exibição de pilha de memória, entre outros. Use sempre os controles de dados tabulares padrão fornecidos. Em alguns casos raros, você pode não ter acesso aos controles de dados tabulares padrão. Nessas situações, use os seguintes nomes de tokenpara garantir que sua iu é consistente com outros controles de dados tabulares no Visual Studio.  
  
 ![Controle de grade &#40;de dados tabulares&#41; linha vermelha](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 Usar...  
 para controles tabulares ou de grade.  
  
 Não use...  
 para qualquer ui que não seja um controle tabular ou de grade.  
  
##### <a name="column-headers"></a>Cabeçalhos da coluna  
 Os cabeçalhos da coluna consistem em um plano de fundo, uma borda, o texto do título e um glifo opcional geralmente usado quando uma grade é classificada por essa coluna.  
  
|Estado|Elemento|Nome do token: Category.color|  
|-----------|-------------|--------------------------------|  
|Padrão|Segundo plano|`Header.Default`|  
|Padrão|Primeiro plano (Texto)|`Environment.CommandBarTextActive`|  
|Padrão|Primeiro plano (Glifo)|`Header.Glyph`|  
|Padrão|Borda|`Header.SeparatorLine`|  
|Passar o mouse|Segundo plano|`Header.MouseOver`|  
|Passar o mouse|Primeiro plano (Texto)|`Environment.CommandBarTextHover`|  
|Passar o mouse|Primeiro plano (Glifo)|`Header.MouseOverGlyph`|  
|Passar o mouse|Borda|`Header.SeparatorLine`|  
|Pressionado|Segundo plano|`CommonControls.CheckBoxBackgroundPressed`|  
|Pressionado|Primeiro plano (Texto)|`CommonControls.CheckBoxBorderPressed`|  
|Pressionado|Primeiro plano (Glifo)|`CommonControls.CheckBoxTextPressed`|  
|Pressionado|Borda|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Listar itens de exibição  
 Os itens de exibição da lista consistem em um plano de fundo e no conteúdo. O conteúdo pode ser texto, um ícone ou ambos.  
  
|Estado|Elemento|Nome do token: Category.color|  
|-----------|-------------|--------------------------------|  
|Padrão|Segundo plano|Transparente|  
|Padrão|Primeiro plano (Texto)|`Environment.CommandBarTextActive`|  
|Padrão|Borda|Nenhum|  
|Selecionado (ativo)|Segundo plano|`TreeView.SelectedItemActive`|  
|Selecionado (ativo)|Primeiro plano (Texto)|`TreeView.SelectedItemActiveText`|  
|Selecionado (ativo)|Borda|Nenhum|  
|Selecionado (inativo)|Segundo plano|`TreeView.SelectedItemInactive`|  
|Selecionado (inativo)|Primeiro plano (Texto)|`TreeView.SelectedItemInactiveText`|  
|Selecionado (inativo)|Borda|Nenhum|  
  
### <a name="manifest-designer"></a>Designer de manifesto  
 O Manifest Designer foi projetado como uma maneira de facilitar a edição do arquivo manifesto nos projetos windows 8 e Windows Phone 8. Embora não haja uma estrutura compartilhada disponível para consumo, pode ser apropriado para você combinar o layout de design e as cores das guias de orientação/navegação e da estrutura geral. Para obter mais informações sobre detalhes do layout, consulte [Layout para Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Linha vermelha do Manifest Designer](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
Usar...  
- para designers que são semelhantes ao Manifest Designer.  

- no lugar de usar controles comuns de guia na parte superior de um editor dentro do documento bem.  

Não use...  
- se você tiver mais de seis guias.  

- para qualquer ui que não esteja estruturada como o Manifest Designer.  
  
|Estado|Componente|Elemento|Nome do token: Category.color|  
|-----------|---------------|-------------|--------------------------------|  
|Padrão (selecionado)|Tab|Segundo plano|`ManifestDesigner.TabActive`|  
|Padrão (selecionado)|Tab|Borda|Nenhum|  
|Padrão (selecionado)|Painel de descrição|Segundo plano|`ManifestDesigner.DescriptionPane`|  
|Padrão (selecionado)|Página de conteúdo|Segundo plano|`ManifestDesigner.Background`|  
|Padrão (selecionado)|Página de conteúdo|Texto auxiliar de diálogo|`ManifestDesigner.WatermarkText`<br /><br /> Este nome de token não corresponde à sua função.|  
|Não selecionados|Tab|Segundo plano|`ManifestDesigner.Tab.Inactive`|  
|Passar o mouse|Tab|Segundo plano|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Marcação  
 O Visual Studio suporta a marcação, que permite que um usuário declare palavras-chave pesquisáveis para fins de rastreamento. Por exemplo, gerentes de projeto e desenvolvedores podem usar o Team Foundation Server (TFS) para marcar itens de trabalho. As tabelas abaixo dão nomes de cores tanto para a tag em si quanto para o glifo "ícone de fechamento" que aparece em hover e estados selecionados.  
  
 ![Linha vermelha de marcação](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")  
  
 Usar...  
 para a UI que suporta a marcação.  
  
 Não use...  
 para qualquer outro tipo de ui.  
  
#### <a name="tag"></a>Marca  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Padrão**|Segundo plano|`Tag.Background`|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Padrão**|Primeiro plano (Texto)|`Tag.Background`|  
|![Tag on hover](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Passar o mouse**|Segundo plano|`Tag.HoverBackground`|  
|![Tag on hover](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Passar o mouse**|Primeiro plano (Texto)|`Tag.HoverBackgroundText`|  
|![Tag pressionado](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Pressionado**|Segundo plano|`Tag.PressedBackground`|  
|![Tag pressionado](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Pressionado**|Primeiro plano (Texto)|`Tag.PressedBackgroundText`|  
|![Tag selecionada](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Selecionado**|Segundo plano|`Tag.SelectedBackground`|  
|![Tag selecionada](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Selecionado**|Primeiro plano (Texto)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Glifo (ícone de fechamento)  
 **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Gifo &#40;&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Padrão (padrão de tag)**|Segundo plano|N/D|  
|![Gifo &#40;&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Padrão (padrão de tag)**|Primeiro plano (Glifo)|`Tag.TagHoverGlyph`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Marque &#40;&#41; de glifo no hover](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Hover (padrão de tag)**|Segundo plano|`Tag.TagHoverGlyphHoverBackground`|  
|![Marque &#40;&#41; de glifo no hover](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Hover (padrão de tag)**|Primeiro plano (Glifo)|`Tag.TagHoverGlyphHover`|  
|![Marque &#40;&#41; de glifo no hover](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Hover (padrão de tag)**|Borda|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag &#40;glifo&#41; pressionado](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Pressionado (padrão da tag)**|Segundo plano|`Tag.TagHoverGlyphPressedBackground`|  
|![Tag &#40;glifo&#41; pressionado](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Pressionado (padrão da tag)**|Primeiro plano (Glifo)|`Tag.TagHoverGlyphPressed`|  
|![Tag &#40;glifo&#41; pressionado](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Pressionado (padrão da tag)**|Borda|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Padrão de tag selecionado/glifo**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag selecionada](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Padrão (tag selecionado)**|Segundo plano|N/D|  
|![Tag selecionada](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Padrão (tag selecionado)**|Primeiro plano (Glifo)|`Tag.TagSelectedGlyph`|  
  
 **Tag selected/gliph hover**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag selecionada no hover](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Hover (tag selecionado)**|Segundo plano|`Tag.TagSelectedGlyphHoverBackground`|  
|![Tag selecionada no hover](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Hover (tag selecionado)**|Primeiro plano (Glifo)|`Tag.TagSelectedGlyphHover`|  
|![Tag selecionada no hover](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Hover (tag selecionado)**|Borda|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Tag selecionada/glifo pressionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag selecionada pressionada](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Pressionado (tag selecionado)**|Segundo plano|`Tag.TagSelectedGlyphPressedBackground`|  
|![Tag selecionada pressionada](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Pressionado (tag selecionado)**|Primeiro plano (Glifo)|`Tag.TagSelectedGlyphPressed`|  
|![Tag selecionada pressionada](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Pressionado (tag selecionado)**|Borda|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Shell  
  
#### <a name="background"></a>Segundo plano  
 O plano de fundo do ambiente consiste em duas camadas. A camada inferior é uma cor sólida que cobre todo o IDE. A camada superior se encaixa a prateleira de comando e entre os canais de ocultação automática da janela da ferramenta nas bordas esquerda e direita do IDE. A partir do Visual Studio 2013, as camadas de fundo superior e inferior são definidas para a mesma cor nos temas Luz e Escuro.  
  
 ![Linha vermelha de fundo shell](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 Usar...  
 para lugares que você deseja combinar com o fundo do ambiente do Visual Studio.  
  
Não use...  
- como um preenchimento para lugares que não são superfícies de fundo.  

- como um fundo no qual você deseja colocar elementos em primeiro plano.  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|Camada inferior|Segundo plano|`Environment.EnvironmentBackground`|  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|Camada superior|Segundo plano<br /><br /> *O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Camada superior|Segundo plano<br /><br /> *O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Camada superior|Segundo plano<br /><br /> *O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Camada superior|Segundo plano<br /><br /> *O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Prateleira de comando  
 Dois conjuntos de nomes de token são usados para os fundos da prateleira de comando: um conjunto para onde a barra de menu situa e outro para onde as barras de comando se sentam. Um grupo de barras de comando individual tem seus próprios valores de cor de fundo, que são discutidos com mais detalhes na seção "barra de comando". O texto da barra de menu e da barra de comando é discutido nas seções menu e barra de comando, respectivamente.  
  
 ![Linha vermelha da prateleira de comando](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")  
  
Usar...  
- para áreas onde você coloca menus ou barras de ferramentas.  

- com a combinação correta de nome de token de plano de fundo/ primeiro plano.  
  
  Não use...  
  para áreas que não são semelhantes a uma prateleira de comando.  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|Barra de menus|Segundo plano<br /><br /> *O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Barra de menus|Segundo plano<br /><br /> *O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Barra de menus|Segundo plano<br /><br /> *O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Barra de comandos|Segundo plano<br /><br /> *O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Barra de comandos|Segundo plano<br /><br /> *O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Barra de comandos|Segundo plano<br /><br /> *O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Caixa de Ferramentas  
 A caixa de ferramentas é uma das janelas de ferramentas comuns que é mais usada no Visual Studio. É essencialmente um controle de árvore com um tema especial e estilo aplicado.  
  
 ![Linha vermelha da caixa de ferramentas](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")  
  
 Usar...  
 quando você está projetando uma janela de ferramenta que você deseja ser sempre consistente com a caixa de ferramentas shell.  
  
 Não use...  
 para qualquer coisa que não seja semelhante à ui da caixa de ferramentas, ou se você não tem certeza se sua iu do ui terá problemas se as cores da caixa de ferramentas shell mudarem.  
  
 **Padrão**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nó pai da caixa de ferramentas](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nó pai**|Segundo plano|`Environment.ToolboxContent`<br /><br /> Títulos<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Itens individuais, ou janela inteira se não houver controles disponíveis|  
|![Nó de criança caixa de ferramentas](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Nó infantil**|Segundo plano|`Environment.ToolboxContent`<br /><br /> Títulos<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Itens individuais, ou janela inteira se não houver controles disponíveis|  
|![Nó pai da caixa de ferramentas](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nó pai**|Borda|Nenhum|  
|![Nó de criança caixa de ferramentas](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Nó infantil**|Borda|Nenhum|  
|![Nó pai da caixa de ferramentas](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nó pai**|Primeiro plano (Glifo)|`Environment.ToolboxContent`|  
|![Nó de criança caixa de ferramentas](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Nó infantil**|Primeiro plano (Glifo)|`Environment.ToolboxContent`|  
|![Nó pai da caixa de ferramentas](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nó pai**|Primeiro plano (Texto)|`Environment.ToolboxContent`|  
|![Nó de criança caixa de ferramentas](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Nó infantil**|Primeiro plano (Texto)|`Environment.ToolboxContent`|  
  
 **Passar o mouse**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nó de criança caixa de ferramentas no hover](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Caixa de ferramentas paira sobre nó de criança**|Segundo plano|`Environment.ToolboxContentMouseOver`<br /><br /> Apenas itens individuais|  
|![Nó de criança caixa de ferramentas no hover](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Caixa de ferramentas paira sobre nó de criança**|Borda|Nenhum|  
|![Nó de criança caixa de ferramentas no hover](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Caixa de ferramentas paira sobre nó de criança**|Primeiro plano (Texto)|`Environment.ToolboxContentMouseOver`<br /><br /> Apenas itens individuais|  
  
 **Selecionado**  
  
|Componente|Elemento|Nome do token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nó pai da caixa de ferramentas focado](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Nó pai focado**|Segundo plano|`TreeView.SelectedItemActive`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó de criança da caixa de ferramentas focado](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Nó infantil focado**|Segundo plano|`TreeView.SelectedItemActive`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó pai da caixa de ferramentas focado](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Nó pai focado**|Borda|`TreeView.FocusVisualBorder`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó de criança da caixa de ferramentas focado](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Nó infantil focado**|Borda|`TreeView.FocusVisualBorder`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó pai da caixa de ferramentas focado](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Nó pai focado**|Primeiro plano (Glifo)|`TreeView.SelectedItemActive`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó de criança da caixa de ferramentas focado](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Nó infantil focado**|Primeiro plano (Glifo)|`TreeView.SelectedItemActive`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó pai da caixa de ferramentas focado](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Nó pai focado**|Primeiro plano (Texto)|`TreeView.SelectedItemActive`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó de criança da caixa de ferramentas focado](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Nó infantil focado**|Primeiro plano (Texto)|`TreeView.SelectedItemActive`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó pai da caixa de ferramentas desfocado](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nó pai desfocado**|Segundo plano|`TreeView.SelectedItemInactive`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó de criança caixa de ferramentas desfocado](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nó infantil desfocado**|Segundo plano|`TreeView.SelectedItemInactive`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó pai da caixa de ferramentas desfocado](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nó pai desfocado**|Borda|Nenhum|  
|![Nó de criança caixa de ferramentas desfocado](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nó infantil desfocado**|Borda|Nenhum|  
|![Nó pai da caixa de ferramentas desfocado](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nó pai desfocado**|Primeiro plano (Glifo)|`TreeView.SelectedItemInactive`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó de criança caixa de ferramentas desfocado](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nó infantil desfocado**|Primeiro plano (Glifo)|`TreeView.SelectedItemInactive`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó pai da caixa de ferramentas desfocado](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nó pai desfocado**|Primeiro plano (Texto)|`TreeView.SelectedItemInactive`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
|![Nó de criança caixa de ferramentas desfocado](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nó infantil desfocado**|Primeiro plano (Texto)|`TreeView.SelectedItemInactive`<br /><br /> Da categoria [de visualização de](../misc/shared-colors.md#BKMK_TreeView) árvore|  
  
## <a name="color-value-reference"></a>Referência de valor de cor  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|Componente|Parte|Elemento|Estado|Leve|Escuro|Azul|Alto Contraste|  
|Linhas divisórias|||Padrão|FFEEEEF2|FF2D2D30|FFEEEEF2|Controldark|  
|Glifo expansor||Primeiro plano|Padrão|||||  
|Glifo expansor||Primeiro plano|Passar o mouse|||||  
|Glifo expansor||Segundo plano|Padrão|||||  
|Glifo expansor||Segundo plano|Passar o mouse|||||  
|Glifo expansor||Borda|Padrão|||||  
|Glifo expansor||Borda|Passar o mouse|||||