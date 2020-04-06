---
title: Cores compartilhadas para visual studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e31e5d9c3d1dc284694bd2db2a9f37d863462ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699937"
---
# <a name="shared-colors-for-visual-studio"></a>Cores compartilhadas para Visual Studio
Quando você estiver projetando interface do usuário que usa elementos comuns do Visual Studio shell, ou você gostaria que seu elemento de interface fosse consistente com recursos semelhantes, use nomes de token existentes em arquivos de definição de pacote para escolher e atribuir cores. Isso garante que sua iu de usuário permaneça consistente com o ambiente geral do Visual Studio e que atualize automaticamente quando os temas forem adicionados ou atualizados.

Este artigo descreve elementos comuns de IU e os nomes de token que eles usam, que você pode referenciar ao construir iu semelhante. Para obter informações específicas sobre como acessar esses tokens de cores, consulte [O Serviço VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Certifique-se de usar os nomes de token corretamente:

- **Use nomes de token com base na função, não na cor em si.** As cores comuns compartilhadas são associadas a elementos de interface específicos e destinam-se apenas a ser usadas para as mesmas características ou similares. Por exemplo, não reutilize a cor de uma caixa de combinação pressionada para uma animação de progresso giratório só porque você gosta da cor. As funções da caixa de combinação e da animação são diferentes, e se a cor associada à caixa de combinação mudar, pode não ser mais uma cor apropriada para o seu elemento de animação. O uso consistente de cores ajuda a orientar seus usuários e evitar confusão.

- **Use as cores de fundo e texto na combinação correta.** As cores de fundo que se destinam a ser usadas com texto terão uma cor de texto associada. Não use cores de texto diferentes das especificadas para esse plano de fundo. Se não houver uma cor de texto associada, não use essa cor de fundo para qualquer superfície na qual você espera exibir texto. Outras combinações de cores de texto e de fundo podem resultar em uma interface ilegível.

- **Use cores de controle adequadas para sua localização.** Em certos estados, alguns controles do Visual Studio não têm bordas e cores de fundo separadas. Em vez disso, eles pegam essas cores das superfícies atrás deles. Certifique-se de que você sempre usa os nomes de token apropriados para o local onde você está colocando o controle.

> [!IMPORTANT]
> Não use tokens encontrados nas categorias "Página inicial" ou "Cidra".

## <a name="common-shared-controls"></a>Controles compartilhados comuns

Quando você usa uma barra de comando padrão do Visual Studio em seu recurso, você terá acesso a controles de shell estilizados. Você não deve re-modelar esses controles comuns. No entanto, se você precisar construir uma barra de comando personalizada, talvez seja necessário construir controles personalizados também. Nesse caso, certifique-se de usar os nomes de token corretos para cada um dos seguintes controles para que sua iu é consistente com o resto do Visual Studio.

### <a name="button-controls"></a>Controles de botão

![Linha vermelha do controle de botão](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Usar... | Não use... |
| --- | --- |
| ... para botões no documento bem que você deseja integrar com os temas do Visual Studio (Luz, Escuro, Azul ou um tema de alto contraste do sistema). | ... para botões que serão exibidos em um plano de fundo personalizado que não faz parte de um tema do Visual Studio. |

**Botão: estado padrão**

![Botão padrão](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Botão padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Botão | `CommonControls.Button` |
| Borda do botão | `CommonControls.ButtonBorder` |

**Botão: estado padrão**

![Botão padrão](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Botão padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Botão | `CommonControls.ButtonDefault` |
| Borda do botão | `CommonControls.ButtonBorderDefault` |

**Botão: estado desativado**

![Botão desativado](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Desativado")<br />Botão desativado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Botão | `CommonControls.ButtonDisabled` |
| Borda do botão | `CommonControls.ButtonBorderDisabled` |

**Botão: estado de hover**

![Botão em pairar](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Botão em pairar

| Elemento | Nome do token: Category.color |
| --- | --- |
| Botão | `CommonControls.ButtonHover` |
| Borda do botão | `CommonControls.ButtonBorderHover` |

**Botão: estado pressionado**

![Botão pressionado](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Botão.Pressionado")<br />Botão pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Botão | `CommonControls.ButtonPressed` |
| Borda do botão | `CommonControls.ButtonBorderPressed` |

**Botão: estado focado**

![Botão focado](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Botão focado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Botão | `CommonControls.ButtonFocused` |
| Borda do botão | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Controles da caixa de seleção
![Caixa de seleção (linha vermelha)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Caixa de seleção (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... para controles de caixa de seleção contidos dentro do documento bem. | ... para qualquer ui que não seja um controle de caixa de seleção. |

**Caixa de seleção: estado padrão**

![Caixa de seleção](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Caixa de seleção padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `CommonControls.CheckBoxBackground` |
| Borda | `CommonControls.CheckBoxBorder` |
| Texto | `CommonControls.CheckBoxText` |
| Glifo | `CommonControls.CheckBoxGlyph` |

**Caixa de seleção: estado desativado**

![Caixa de seleção desativada](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Caixa de seleção desativada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `CommonControls.CheckBoxBackgroundDisabled` |
| Borda | `CommonControls.CheckBoxBorderDisabled` |
| Texto | `CommonControls.CheckBoxTextDisabled` |
| Glifo | `CommonControls.CheckBoxGlyphDisabled` |

**Caixa de seleção: estado de hover**

 ![Caixa de seleção em hover](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Caixa de seleção em hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `CommonControls.CheckBoxBackgroundHover` |
| Borda | `CommonControls.CheckBoxBorderHover` |
| Texto | `CommonControls.CheckBoxTextHover` |
| Glifo | `CommonControls.CheckBoxGlyphHover` |

**Caixa de seleção: estado pressionado**

![Caixa de seleção pressionada](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Caixa de seleção pressionada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `CommonControls.CheckBoxBackgroundPressed` |
| Borda | `CommonControls.CheckBoxBorderPressed` |
| Texto | `CommonControls.CheckBoxTextPressed` |
| Glifo | `CommonControls.CheckBoxGlyphPressed` |

**Caixa de seleção: estado focado**

![Caixa de seleção focada](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Caixa de seleção focada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `CommonControls.CheckBoxBackgroundFocused` |
| Borda | `CommonControls.CheckBoxBorderFocused` |
| Texto | `CommonControls.CheckBoxTextFocused` |
| Glifo | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Drop-downs e caixas de combinação
![Caixa de parada/combo (linha vermelha)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Caixa de parada/combo (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... para drop-downs e caixas de combinação no documento bem. | ... para qualquer ui que não seja uma caixa de parada ou combo. |
| | ... para [drop-downs de](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) barra de comando ou [caixas de combinação](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Drop-downs e caixas de combinação: estado padrão**

![Caixa de parada/combo padrão](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Caixa de parada/combo padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `CommonControls.ComboBoxBackground` |
| Borda | `CommonControls.ComboBoxBorder` |
| Texto | `CommonControls.ComboBoxText` |
| Separador | `CommonControls.ComboBoxSeparator` |
| Glifo | `CommonControls.ComboBoxGlyph` |
| Fundo glifos | `CommonControls.ComboBoxGlyphBackground` |

**Drop-downs e caixas de combinação: estado desativado**

![Caixa de saque/combo desativada](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Caixa de saque/combo desativada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `CommonControls.ComboBoxBackgroundDisabled` |
| Borda | `CommonControls.ComboBoxBorderDisabled` |
| Texto | `CommonControls.ComboBoxTextDisabled` |
| Separador | `CommonControls.ComboBoxSeparatorDisabled` |
| Glifo | `CommonControls.ComboBoxGlyphDisabled` |
| Fundo glifos | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Drop-downs e caixas de combinação: estado de hover**

![Caixa de parada/combo no hover](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Caixa de parada/combo no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `CommonControls.ComboBoxBackgroundHover` |
| Borda | `CommonControls.ComboBoxBorderHover` |
| Texto | `CommonControls.ComboBoxTextHover` |
| Separador | `CommonControls.ComboBoxSeparatorHover` |
| Glifo | `CommonControls.ComboBoxGlyphHover` |
| Fundo glifos | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Drop-downs e caixas de combinação: estado pressionado**

![Caixa de parada/combinação pressionada](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Caixa de parada/combinação pressionada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `CommonControls.ComboBoxBackgroundPressed` |
| Borda | `CommonControls.ComboBoxBorderPressed` |
| Texto | `CommonControls.ComboBoxTextPressed` |
| Separador | `CommonControls.ComboBoxSeparatorPressed` |
| Glifo | `CommonControls.ComboBoxGlyphPressed` |
| Fundo glifos | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Itens de lista de itens de lista de entradas e caixas de combinação: estado pressionado**

 ![Exibição de item de lista pressionada/combo](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Exibição de item de lista pressionada/combo

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Borda | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Texto do item | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Sombra de fundo | `CommonControls.ComboBoxListBackgroundShadow` |

**Drop-downs e caixas de combinação: estado focado**

![Caixa de parada/combo com foco](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Caixa de parada/combo com foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `CommonControls.ComboBoxBackgroundFocused` |
| Borda | `CommonControls.ComboBoxBorderFocused` |
| Texto | `CommonControls.ComboBoxTextFocused` |
| Separador | `CommonControls.ComboBoxSeparatorFocused` |
| Glifo | `CommonControls.ComboBoxGlyphFocused` |
| Fundo glifos | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Drop-downs e caixas de combinação: seleção de entrada de texto**

![Seleção de entrada de texto de caixa de combo/down](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Seleção de entrada de texto de caixa de combo/down

| Elemento | Nome do token: Category.color |
| --- | --- |
| Realçar | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Controles de dados tabulares (grade)
Os controles de dados tabulares, também conhecidos como controles de grade, são controles comuns para o Visual Studio que podem ser usados para apresentar grandes quantidades de dados em várias colunas. Os controles de dados tabulares padrão podem ser encontrados em vários lugares dentro do Visual Studio: a janela da ferramenta Lista de erros, os relatórios do IntelliTrace e a exibição de pilha de memória, entre outros. Use sempre os controles de dados tabulares padrão fornecidos. Em alguns casos raros, você pode não ter acesso aos controles de dados tabulares padrão. Nessas situações, use os seguintes nomes de tokenpara garantir que sua iu é consistente com outros controles de dados tabulares no Visual Studio.

![Controle de dados/grade tabular (linha vermelha)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Controle de dados/grade tabular (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... para controles tabulares ou de grade. | ... para qualquer ui que não seja um controle tabular ou de grade. |

#### <a name="column-headers"></a>Cabeçalhos da coluna
Os cabeçalhos da coluna consistem em um plano de fundo, uma borda, o texto do título e um glifo opcional geralmente usado quando uma grade é classificada por essa coluna.

**Cabeçalho da coluna: estado padrão**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Header.Default` |
| Primeiro plano (Texto) | `Environment.CommandBarTextActive` |
| Primeiro plano (Glifo) | `Header.Glyph` |
| Borda | `Header.SeparatorLine` |

**Cabeçalho da coluna: estado de hover**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Header.MouseOver` |
| Primeiro plano (Texto) | `Environment.CommandBarTextHover` |
| Primeiro plano (Glifo) | `Header.MouseOverGlyph` |
| Borda | `Header.SeparatorLine` |

**Cabeçalho da coluna: estado pressionado**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `CommonControls.CheckBoxBackgroundPressed` |
| Primeiro plano (Texto) | `CommonControls.CheckBoxBorderPressed` |
| Primeiro plano (Glifo) | `CommonControls.CheckBoxTextPressed` |
| Borda | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Listar itens de exibição
 Os itens de exibição da lista consistem em um plano de fundo e no conteúdo. O conteúdo pode ser texto, um ícone ou ambos.

**Itens de exibição de lista: estado padrão**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | Transparente |
| Primeiro plano (Texto) | `Environment.CommandBarTextActive` |
| Borda | Nenhum |

**Itens de exibição de lista: estado ativo**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `TreeView.SelectedItemActive` |
| Primeiro plano (Texto) | `TreeView.SelectedItemActiveText` |
| Borda | Nenhum |

**Itens de exibição da lista: estado inativo**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `TreeView.SelectedItemInactive` |
| Primeiro plano (Texto) | `TreeView.SelectedItemInactiveText` |
| Borda | Nenhum |

### <a name="ui-text"></a>Texto de UI

#### <a name="instructional-text"></a>Texto instrutivo
O texto instrucional dá uma explicação principal proeminente do que fazer em uma página de diálogo ou documento.

![Texto de instrução padrão](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Texto de instrução padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (texto) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Texto instrutivo secundário
Em páginas de documentos com muito texto e controles, alguns textos instrucionais usam um valor de cor diferente. Isso ajuda a transmitir quais informações são mais importantes e diminuir a densidade geral dos elementos da UI. (Veja também a seção abaixo sobre o texto da dica.)

![Texto instrutivo secundário](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Texto instrutivo secundário

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (texto) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Texto de sugestão
O texto de dica aparece em um controle vazio, abaixo de um controle ou em uma superfície de documento vazia para mostrar ao usuário o que fazer a seguir. Você pode usar texto de sugestão com os fundos Janela ou Controle.

**Texto de sugestão padrão**

![Texto de sugestão padrão](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Texto de sugestão padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (texto) | `Environment.ControlEditHintText` |

**Texto de sugestão necessário**

![Texto de sugestão necessário](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Texto de sugestão necessário

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (texto) | `Environment.ControlRequiredHintText` |
| Segundo plano | `Environment.ControlRequiredBackground` |

**Texto de controle da caixa de pesquisa**

> Consulte [as caixas de pesquisa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) de outros tokens de cor relacionados ao controle de pesquisa.

![Texto de controle da caixa de pesquisa](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Texto de controle da caixa de pesquisa

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (texto) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
O hiperlink é um controle que não tem um par de primeiro plano/fundo. Em todos os casos, use a cor hyperlink do primeiro plano, que aparecerá corretamente em fundos escuros, cinzas e brancos. Se você não usar o token de cor para o controle de hiperlink, você verá a cor padrão do sistema para "pressionado", que piscará em vermelho. Esse é o sinal de que o controle não está usando o token de cor do ambiente correto.

![Hiperlink (linha vermelha)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hiperlink (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... quando você precisa criar um hiperlink personalizado. | ... para qualquer coisa que não seja um hiperlink. |

**Hiperlink: estado padrão**

![Hiperlink padrão](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Hiperlink padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (Texto) | `Environment.PanelHyperlink` |

**Hiperlink: estado de hover**

![Hiperlink em hover](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Hiperlink em hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (Texto) | `Environment.PanelHyperlinkHover` |

**Hiperlink: estado pressionado**

![Hiperlink pressionado](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Hiperlink pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (Texto) | `Environment.PanelHyperlinkPressed` |

**Hiperlink: estado desativado**

![Hiperlink desativado](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Hiperlink desativado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (Texto) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infobares
As barras de infosão são usadas para fornecer mais informações sobre um determinado contexto e sempre aparecem no topo de uma janela de documento ou janela de ferramenta.

![Infobar (linha vermelha)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Infobar (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... ao criar infobarras personalizados. | ... para elementos de IA que não são semelhantes a uma barra de informações. |

**Barra de informações: estado padrão**

![Barra de informações padrão](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Barra de informações padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `InfoBar.InfoBarBackground` |
| Primeiro plano (Texto) | `InfoBar.InfoBar` |
| Borda | `InfoBar.InfoBarBorder` |

**Botão Infobar&times;Close ( ) : estado padrão**

![Botão de fechar&times;a barra de informações padrão ( )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Botão de fechar&times;a barra de informações padrão ( )

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `InfoBar.CloseButton` |
| Borda | `InfoBar.CloseButtonBorder` |
| Glifo | `InfoBar.CloseButtonGlyph` |

**Botão Infobar&times;Close ( ) : estado de hover**

![Botão Infobar&times;Close ( ) no hover](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Botão Infobar&times;Close ( ) no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `InfoBar.CloseButtonHover` |
| Borda | `InfoBar.CloseButtonHoverBorder` |
| Glifo | `InfoBar.CloseButtonHoverGlyph` |

**Botão Infobar&times;Close ( ) : estado pressionado**

![Botão de fechar&times;a barra de informações pressionado ( )](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Botão de fechar&times;a barra de informações pressionado ( )

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `InfoBar.CloseButtonDown` |
| Borda | `InfoBar.CloseButtonDownBorder` |
| Glifo | `InfoBar.CloseButtonDownGlyph` |

**Botão de hiperlink infobar: estado padrão**

![Botão de hiperlink infobar padrão](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Botão de hiperlink infobar padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (texto) | `InfoBar.Hyperlink` |

**Botão de hiperlink infobar: estado de hover**

![Botão de hiperlink infobar no hover](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Botão de hiperlink infobar no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (texto) | `Infobar.HyperlinkMouseOver`<br />(Com sublinhado) |

**Botão de hiperlink infobar: estado pressionado**

![Botão de hiperlink infobar pressionado](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Botão de hiperlink infobar pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (texto) | `Infobar.HyperlinkMouseDown`<br />(Com sublinhado) |

**Hiperlink inline infobar (dentro de uma sentença): estado padrão**

![Botão de hiperlink de infobar inline padrão](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Botão de hiperlink de infobar inline padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (texto) | `InfoBar.Hyperlink` |

**Hiperlink inline infobar (dentro de uma frase): estado de hover**

![Botão de hiperlink inline infobar no hover](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Botão de hiperlink inline infobar no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (texto) | `Infobar.HyperlinkMouseOver`<br />(Com sublinhado) |

**Hiperlink inline infobar (dentro de uma frase): estado pressionado**

![Botão de hiperlink inline pressionado](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Botão de hiperlink inline pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (texto) | `Infobar.HyperlinkMouseDown`<br />(Com sublinhado) |

**Botão infobar: estado padrão**

![Botão de infobar padrão](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Botão de infobar padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `InfoBar.Button` |
| Primeiro plano (texto) | `InfoBar.Button` |
| Borda | `InfoBar.ButtonBorder` |

**Botão infobar: estado de hover**

![Botão infobar no hover](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Botão infobar no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `InfoBar.ButtonMouseOver` |
| Primeiro plano (texto) | `InfoBar.ButtonMouseOver` |
| Borda | `InfoBar.ButtonMouseOverBorder` |

**Botão infobar: estado pressionado**

![Botão de barra de informações pressionado](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Botão de barra de informações pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `InfoBar.ButtonMouseDown` |
| Primeiro plano (texto) | `InfoBar.ButtonMouseDown` |
| Borda | `InfoBar.ButtonMouseDownBorder` |

**Botão infobar: estado desativado**

![Botão de barra de informações desativado](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Botão de barra de informações desativado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `InfoBar.ButtonDisabled` |
| Primeiro plano (texto) | `InfoBar.ButtonDisabled` |
| Borda | `InfoBar.ButtonDisabledBorder` |

**Botão infobar: estado focado**

![Botão de infobar focado](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Botão de infobar focado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `InfoBar.ButtonFocus` |
| Primeiro plano (texto) | `InfoBar.ButtonFocus` |
| Borda | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Barras de rolagem
As barras de rolagem são estilizadas pelo ambiente do Visual Studio e não precisarão ser temáticas. No entanto, você pode decidir que deseja aproveitar as cores usadas nas barras de rolagem para que sua iu de ida e vida sempre pareça consistente com esta parte do ambiente do Visual Studio.

![Barra de rolagem (linha vermelha)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Barra de rolagem (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... quando você está criando ui que você deseja combinar barras de rolagem do Visual Studio. | ... para qualquer coisa que você não quer sempre combinar iu barra de rolagem. |

**Barra de rolagem: estado padrão**

![Barra de rolagem padrão](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Barra de rolagem padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Barra de rolagem | `Environment.ScrollBarBackground` |
| Primeiro plano (Polegar) | `Environment.ScrollBarThumbBackground` |

**Barra de rolagem: estado de hover**

![Barra de rolagem em hover](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Barra de rolagem em hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Barra de rolagem | `Environment.ScrollBarBackground` |
| Primeiro plano (Polegar) | `Environment.ScrollBarThumbMouseOverBackground` |

*Barra de rolagem: estado pressionado**

![Barra de rolagem pressionada](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Barra de rolagem pressionada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Barra de rolagem | `Environment.ScrollBarBackground` |
| Primeiro plano (Polegar) | `Environment.ScrollBarThumbPressedBackground` |

**Seta da barra de rolagem: estado padrão**

![Seta da barra de rolagem padrão](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Seta da barra de rolagem padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ScrollBarArrowBackground`<br />(Definir para a mesma cor que a barra de rolagem.) |
| Primeiro plano (Glifo) | `Environment.ScrollBarArrowGlyph` |

**Seta da barra de rolagem: estado de hover**

![Seta da barra de rolagem no hover](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Seta da barra de rolagem no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ScrollBarArrowMouseOverBackground`<br />(Definir para a mesma cor que a barra de rolagem.) |
| Primeiro plano (Glifo) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Seta da barra de rolagem: estado pressionado**

![Seta da barra de rolagem pressionada](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Seta da barra de rolagem pressionada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ScrollBarArrowPressedBackground`<br />(Definir para a mesma cor que a barra de rolagem.) |
| Primeiro plano (Glifo) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Caixas de pesquisa
Sempre que possível, use o controle de pesquisa comum fornecido pelo ambiente visual studio. As cores da caixa de pesquisa são encontradas na categoria "SearchControl" no arquivo **ShellColors.pkgdef,** que contém nomes de tokens para o campo de entrada, botão de ação, botão suspenso e menu suspenso.

Uma caixa de pesquisa pode ser um dos vários estados, alguns dos quais são mutuamente exclusivos:

- "Focado" ou "desfocado" refere-se a se o cursor está ou não na caixa de texto.

- "Ativo" ou "inativo" refere-se a saber se o usuário insenou uma consulta de pesquisa na caixa de texto.

- "Hover" significa que o usuário passou rato sobre a caixa de pesquisa com o mouse (este estado substitui todos os outros estados).

- "Desativado" significa que a funcionalidade de pesquisa está desativada para o contexto atual.

![Caixa de pesquisa (linha vermelha)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Caixa de pesquisa (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... quando você está projetando uma caixa de pesquisa personalizada. | ... para qualquer coisa que não seja uma caixa de pesquisa. |
| | ... para qualquer coisa que você não quer sempre corresponder a ui caixa de pesquisa. |

**Campo de entrada de pesquisa focado**

![Campo de entrada de pesquisa focado](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Campo de entrada de pesquisa focado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.FocusedBackground` |
| Primeiro plano (Texto) | `SearchControl.FocusedBackground` |
| Borda | `SearchControl.FocusedBorder` |
| Separador | `SearchControl.FocusedDropDownSeparator` |

**Campo de entrada de pesquisa ativo e desfocado**

![Campo de entrada de pesquisa desfocado](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Campo de entrada de pesquisa ativo e desfocado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.SearchActiveBackground` |
| Primeiro plano (Texto) | `SearchControl.SearchActiveBackground` |
| Borda | `SearchControl.UnfocusedBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Campo de entrada de pesquisa desfocado e inativo**

![Campo de entrada de pesquisa desfocado e inativo](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Campo de entrada de pesquisa desfocado e inativo

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.Unfocused` |
| Primeiro plano (Texto) | `SearchControl.Unfocused` |
| Borda | `SearchControl.UnfocusedBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Campo de entrada de pesquisa destacado (somente texto)**

![Campo de entrada de pesquisa destacado](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Campo de entrada de pesquisa destacado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.Selection` |
| Primeiro plano (Texto) | `SearchControl.FocusedBackground` |
| Borda | Nenhum |
| Separador | `SearchControl.FocusedDropDownSeparator` |

**Campo de entrada de pesquisa desativado**

![Campo de entrada de pesquisa desativado](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Campo de entrada de pesquisa desativado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.Disabled` |
| Primeiro plano (Texto) | `SearchControl.Disabled` |
| Borda | `SearchControl.DisabledBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Botão de ação de pesquisa focado**

![Botão de ação de pesquisa focado](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Botão de ação de pesquisa focado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | Nenhum |
| Primeiro plano (Glyph de pesquisa) | `SearchControl.SearchGlyph` |
| Primeiro plano (Pare o glifo) | `SearchControl.StopGlyph` |
| Primeiro plano (Limpar glifo) | `SearchControl.ClearGlyph` |
| Borda | N/D |

**Botão de ação de pesquisa desfocado**

![Botão de ação de pesquisa desfocado](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Botão de ação de pesquisa desfocado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | N/D |
| Primeiro plano (Glyph de pesquisa) | `SearchControl.SearchGlyph` |
| Primeiro plano (Pare o glifo) | `SearchControl.StopGlyph` |
| Primeiro plano (Limpar glifo) | `SearchControl.ClearGlyph` |
| Borda | N/D |

**Botão de ação de pesquisa pressionado**

![Botão de ação de pesquisa pressionado](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Botão de ação de pesquisa pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.ActionButtonMouseDown` |
| Primeiro plano (Glifo) | `SearchControl.ActionButtonMouseDownGlyph` |
| Borda | `SearchControl.ActionButtonMouseDownBorder` |

**Botão de ação de pesquisa desativado**

![Botão de ação de pesquisa desativado](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Botão de ação de pesquisa desativado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | Nenhum |
| Primeiro plano (Glifo) | `SearchControl.ActionButtonDisabledGlyph` |
| Borda | Nenhum |

**Botão de saque de pesquisa focado**

![Botão de saque de pesquisa focado](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Botão de saque de pesquisa focado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.FocusedDropDownButton` |
| Primeiro plano (Glifo) | `SearchControl.FocusedDropDownButtonGlyph` |
| Borda | `SearchControl.FocusedDropDownButtonBorder` |

**Botão de saque de pesquisa desfocado**

![Botão de saque de pesquisa desfocado](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Botão de saque de pesquisa desfocado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.UnfocusedDropDownButton` |
| Primeiro plano (Glifo) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Borda | `SearchControl.UnfocusedDropDownButtonBorder` |

**Botão de parada de pesquisa pressionado**

![Botão de parada de pesquisa pressionado](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Botão de parada de pesquisa pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.MouseDownDropDownButton` |
| Primeiro plano (Glifo) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Borda | `SearchControl.MouseDownDropDownButtonBorder` |

**Botão de saque de pesquisa desativado**

![Botão de saque de pesquisa desativado](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Botão de saque de pesquisa desativado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | Nenhum |
| Primeiro plano (Glifo) | `SearchControl.DisabledDownButtonGlyph` |
| Borda | Nenhum |

#### <a name="search-drop-down-lists"></a>Pesquisar listas de paradas
O menu suspenso da caixa de pesquisa tem o potencial de ser um pouco mais complexo do que outros menus suspensos no Visual Studio. As seções "pesquisas sugeridas" e "opções de pesquisa" podem aparecer sozinhas ou juntas no menu, e cada uma delas é colorida separadamente. Uma linha também separa essas duas seções quando elas aparecem juntas e uma borda cerca todo o menu suspenso.

![Lista de desporto de pesquisa (linha vermelha)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Lista de desporto de pesquisa (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... quando você está criando uma lista de sossevai de pesquisa personalizada. | ... para listas paradas que aparecem em outros contextos. |
| ... os nomes de token corretos para os componentes corretos da lista. | ... em qualquer combinação de plano de fundo/primeiro plano que não seja especificada. |

**Pesquisar elementos da lista de lista de sosseico**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Borda | `SearchControl.PopupBorder` |
| Separador | `SearchControl.PopupSectionHeaderSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Pesquisas sugeridas: estado padrão**

![Pesquisas sugeridas padrão](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Pesquisas sugeridas padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `SearchControl.PopupItemText` |

**Pesquisas sugeridas: estado de hover**

![Pesquisas sugeridas no hover](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Pesquisas sugeridas no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `SearchControl.PopupMouseOverItemText` |
| Borda | `SearchControl.PopupControlMouseOverBorder` |

**Opções de pesquisa: estado padrão**

![Caixa de seleção de pesquisa](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Opções de pesquisa padrão (caixa de seleção)

![Opções de pesquisa](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Opções de pesquisa padrão (link)

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto da caixa de seleção) | `SearchControl.PopupCheckboxText` |
| Primeiro plano (texto de link) | `SearchControl.PopupButtonText` |
| Fundo do cabeçalho | `SearchControl.PopupSectionHeaderGradientBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (texto de cabeçalho) | `SearchControl.PopupSectionHeaderText` |

**Opções de pesquisa: estado de hover**

![Opções de pesquisa (caixa de seleção) no hover](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Opções de pesquisa (caixa de seleção) no hover

![Opções de pesquisa (link) no hover](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Opções de pesquisa (link) no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto da caixa de seleção) | `SearchControl.PopupCheckboxMouseDownText` |
| Primeiro plano (texto de link) | `SearchControl.PopupButtonMouseDownText` |
| Borda | `SearchControl.PopupControlMouseOverBorder` |

**Opções de pesquisa: estado pressionado**

![Opções de pesquisa pressionadas (caixa de seleção)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Opções de pesquisa pressionadas (caixa de seleção)

![Opções de pesquisa pressionadas (link)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Opções de pesquisa pressionadas (link)

| Elemento | Nome do token: Category.color |
| --- | --- |
| Versá-lo em segundo plano | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto da caixa de seleção) | `SearchControl.PopupCheckboxMouseDownText` |
| Fundo de link | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (texto de link) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a>Vista de árvores
Várias janelas de ferramentas, incluindo o Solution Explorer, Server Explorer e Class View, implementam um esquema organizacional hierárquico cujas cores são controladas por nomes de cores na `TreeView` categoria. Todos os itens em uma visualização de árvore têm cores de fundo e texto. Os itens que possuem elementos infantis aninhados também têm glifos que indicam se o item é expandido ou colapsado.

![Vista da árvore (linha vermelha)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Vista da árvore (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... em qualquer lugar que você precisa para implementar uma visão organizacional hierárquica. | ... para qualquer coisa que não seja semelhante a uma visão de árvore. |
| | ... em qualquer combinação de plano de fundo/primeiro plano que não seja especificada. |

**Item de exibição de árvore: estado padrão**

![Item de visualização de árvore padrão](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Item de visualização de árvore padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `TreeView.Background` |
| Primeiro plano (Texto) | `TreeView.Background` |
| Primeiro plano (Glifo) | `TreeView.Glyph` |
| Borda | Nenhum |

**Item de visualização de árvore: estado de hover**

![Item de visualização de árvore no hover](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Item de visualização de árvore no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `TreeView.Background` |
| Primeiro plano (Texto) | `TreeView.Background` |
| Primeiro plano (Glifo) | `TreeView.GlyphMouseOver` |
| Borda | Nenhum |

**Item de visualização de árvore: arraste sobre o estado**

![Item de visualização de árvore no arrasto](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Item de visualização de árvore no arrasto

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `TreeView.DragOverItem` |
| Primeiro plano (Texto) | `TreeView.DragOverItem` |
| Primeiro plano (Glifo) | `TreeView.DragOverItemGlyph` |
| Borda | Nenhum |

**Item de visualização de árvore: estado selecionado e focado**

![Item de visualização de árvore selecionado e focado](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Item de visualização de árvore selecionado e focado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `TreeView.SelectedItemActive` |
| Primeiro plano (Texto) | `TreeView.SelectedItemActive` |
| Primeiro plano (Glifo) | `TreeView.SelectedItemActiveGlyph` |
| Borda | `TreeView.FocusVisualBorder` |

**Item de visualização de árvore: estado selecionado e sem foco**

![Item de visualização de árvore selecionado e desfocado](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Item de visualização de árvore selecionado e desfocado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `TreeView.SelectedItemInactive` |
| Primeiro plano (Texto) | `TreeView.SelectedItemInactive` |
| Primeiro plano (Glifo) | `TreeView.SelectedItemInactiveGlyph` |
| Borda | Nenhum |

**Item de visualização de árvore: estado em pairado, selecionado e focado**

![Item de visualização de árvore selecionado e focado no hover](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Item de visualização de árvore selecionado e focado no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `TreeView.SelectedItemActive` |
| Primeiro plano (Texto) | `TreeView.SelectedItemActive` |
| Primeiro plano (Glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Borda | `TreeView.FocusVisualBorder` |

**Item de visualização de árvore: estado empaired, selecionado e desfocado**

![Item de visualização de árvore selecionado e desfocado no hover](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Item de visualização de árvore selecionado e desfocado no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `TreeView.SelectedItemInactive` |
| Primeiro plano (Texto) | `TreeView.SelectedItemInactive` |
| Primeiro plano (Glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Borda | Nenhum |

## <a name="shell-appearance"></a>Aparência do Shell

### <a name="background"></a>Segundo plano
O plano de fundo do ambiente consiste em duas camadas. A camada inferior é uma cor sólida que cobre todo o IDE. A camada superior se encaixa sob a prateleira de comando e entre os canais de ocultação automática da janela da ferramenta nas bordas esquerda e direita do IDE. As camadas de fundo superior e inferior são definidas para a mesma cor nos temas Luz e Escuridão.

![Visual Studio shell background (linha vermelha)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Visual Studio shell background (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... para lugares onde você deseja combinar com o fundo do ambiente visual studio. | ... como um preenchimento para lugares que não são superfícies de fundo. |
| | ... como um plano de fundo para colocar elementos em primeiro plano. |

**Aparência da camada inferior**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.EnvironmentBackground` |

**Aparência da camada superior**

> O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Prateleira de comando
Dois conjuntos de nomes de token são usados para os fundos da prateleira de comando: um conjunto para onde a barra de menu situa e outro para onde as barras de comando se sentam. Um grupo de barras de comando individual tem seus próprios valores de cor de fundo, que são discutidos com mais detalhes na seção "barra de comando". O texto da barra de menu e da barra de comando é discutido nas seções menu e barra de comando, respectivamente.

![Prateleira de comando visual studio (linha vermelha)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Prateleira de comando visual studio (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... para áreas onde você coloca menus ou barras de ferramentas. | ... para áreas que não são semelhantes a uma prateleira de comando. |
|... com a combinação correta de nome de token de plano de fundo/primeiro plano. | |

**Barra de menu da prateleira de comando**

> O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Barra de comando da prateleira de comando**

> O gradiente pára definido para o mesmo valor de cor nos temas Visual Studio 2013 Light and Dark.

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Designer de manifesto
O Manifest Designer foi projetado como uma maneira de facilitar a edição do arquivo manifesto nos projetos windows 8 e Windows Phone 8. Embora não haja uma estrutura compartilhada disponível para consumo, pode ser apropriado para você combinar o layout de design e as cores das guias de orientação/navegação e da estrutura geral. Para obter mais informações sobre detalhes do layout, consulte [Layout para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Manifest Designer (linha vermelha)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Manifest Designer (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... para designers que são semelhantes ao Manifest Designer. | ... se você tiver mais de seis guias. |
| ... no lugar de usar controles comuns de guia na parte superior de um editor dentro do documento bem. | ... para qualquer ui que não esteja estruturada como o Manifest Designer. |

**Guia selecionada do Manifest Designer: estado padrão**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `ManifestDesigner.TabActive` |
| Borda | Nenhum |

**Painel de descrição selecionado do Manifest Designer: estado padrão**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `ManifestDesigner.DescriptionPane` |

**Página de conteúdo selecionada do Manifest Designer: estado padrão**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `ManifestDesigner.Background` |
| Texto auxiliar de diálogo | `ManifestDesigner.WatermarkText`<br />(Este nome de token não corresponde à sua função.) |

**Guia Manifest Designer: estado não selecionado**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `ManifestDesigner.Tab.Inactive` |

**Guia Manifest Designer: estado de hover**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Estruturas de comando

### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Menus
Os menus podem ocorrer em vários lugares dentro do Visual Studio: a barra de menu principal, incorporada em janelas de documentos ou ferramentas, ou no clique com o botão direito do mouse em vários locais ao longo do IDE. Implementações de menus associados a outros elementos de IU são discutidas na seção para o respectivo elemento. Você deve sempre usar a implementação padrão do menu fornecida pelo ambiente Visual Studio. No entanto, em alguns casos raros, você pode não ter acesso aos menus padrão do Visual Studio. Nessas situações, use os seguintes nomes de token para garantir que sua iu é consistente com outros menus no Visual Studio.

![Menu visual studio (linha vermelha)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Menu visual studio (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... quando você precisa criar um menu personalizado.| ... a cor de fundo sozinho. Use sempre a combinação de plano de fundo/primeiro plano conforme especificado. |
| ... quando você tem um novo componente de ida e volta que deseja combinar com os menus do Visual Studio.| |

#### <a name="menu-titles"></a>Títulos do menu
Os títulos do menu consistem em um plano de fundo, uma borda e o texto do título, bem como um glifo opcional, geralmente quando o menu é encontrado em uma barra de comando.

![Título do menu (linha vermelha)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Título do menu (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... sempre que você estiver criando um título de menu personalizado. | ... para qualquer coisa que você não quer sempre corresponder ao título do menu. |
| | ... em qualquer combinação de plano de fundo/primeiro plano que não seja especificada. |

**Título do menu: estado padrão**

![Título do menu padrão](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Título do menu padrão

![Título do menu padrão com glifo](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Título do menu padrão com glifo

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | Nenhum |
| Primeiro plano (texto) | `Environment.CommandBarTextActive` |
| Primeiro plano (glifo) | `Environment.CommandBarMenuGlyph` |
| Borda | Nenhum |

**Título do menu: estado de hover**

![Título do menu em hover](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Título do menu em hover

![Título do menu com glifo no hover](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Título do menu com glifo no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarMouseOverBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (texto) | `Environment.CommandBarTextHover` |
| Primeiro plano (glifo) | `Environment.CommandBarMenuMouseOverGlyph` |
| Borda | `Environment.CommandBarBorder` |

**Título do menu: estado pressionado**

![Título do menu pressionado](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Título do menu pressionado

![Título do menu pressionado com glifo](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Título do menu pressionado com glifo

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.CommandBarTextActive` |
| Primeiro plano (Glifo) | `Environment.CommandBarMenuMouseDownGlyph` |
| Borda | `Environment.CommandBarMenuBorder`<br />(Apenas os lados esquerdo, superior e direito.) |

**Título do menu: estado desativado**

![Título do menu desativado com glifo](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Título do menu desativado com glifo

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | Nenhum |
| Primeiro plano (Texto) | `Environment.CommandBarTextInactive` |
| Primeiro plano (Glifo) | `Environment.CommandBarTextInactive` |
| Borda | Nenhum |

#### <a name="menu-items"></a>Itens de menu
Um item de menu individual consiste no texto do menu e um ícone opcional, caixa de seleção ou glifo de menu submenu. Seu plano de fundo e cor de texto mudam no hover. Este token de cor é um par de plano de fundo/primeiro plano.

![Itens do menu em linha vermelha](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Usar... | Não use... |
|---|---|
| ... para qualquer lista suspenso que seja lançada a partir de uma barra de menu ou barra de comando. | ... para qualquer lista de parada em outro contexto. |
| | ... em qualquer combinação de plano de fundo/primeiro plano que não seja especificada. |

**Itens do menu: estado padrão**

![Itens de menu padrão](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Itens de menu padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.CommandBarTextActive` |
| Primeiro plano (Glifo do submenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Borda | `Environment.CommandBarMenuBorder` |
| Histórico do canal de ícones | `Environment.CommandBarMenuIconBackground` |
| Separador | `Environment.CommandBarMenuSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Itens do menu: estados verificados e selecionados**

![Menu verificado](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Item do menu verificado

![Menu selecionado](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Item do menu selecionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Marca de seleção | `Environment.CommandBarCheckBox` |
| Verifique o plano de fundo da marca | `Environment.CommandBarSelectedIcon` |
| Histórico de ícones | `Environment.CommandBarSelected` |
| Fronteira do ícone | `Environment.CommandBarSelectedBorder` |

**Itens do menu: estado de hover**

![O menu paira](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Item do menu em hover

![Menu hover verificado](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Item do menu verificado no hover

![Menu hover selecionado](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Item de menu selecionado no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarMenuItemMouseOver` |
| Primeiro plano (Texto) | `Environment.CommandBarMenuItemMouseOverText` |
| Primeiro plano (Glifo do submenu) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Marca de seleção | `Environment.CommandBarCheckBoxMouseOver` |
| Verifique o plano de fundo da marca | `Environment.CommandBarHoverOverSelectedIcon` |
| Histórico de ícones | `Environment.CommandBarHoverOverSelected` |
| Fronteira do ícone | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Itens do menu: estado desativado**

![Menu desativado](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Item de menu desativado

![Menu desativado verificado](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Item do menu desativado com marca de verificação

| Elemento | Nome do token: Category.color |
| --- | --- |
| Primeiro plano (Texto) | `Environment.CommandBarTextInactive` |
| Primeiro plano (Glifo do submenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Marca de seleção | `Environment.CommandBarCheckBoxDisabled` |
| Verifique o plano de fundo da marca | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Barras de comando
Uma barra de comando pode aparecer em vários lugares dentro do Visual Studio IDE, mais notavelmente na prateleira de comando e embutida em janelas de ferramentas ou documentos.

Em geral, use sempre a implementação padrão da barra de comando fornecida pelo ambiente Visual Studio. O uso do mecanismo padrão garante que todos os detalhes visuais apareçam corretamente e que os elementos interativos se comportarão consistentemente com outros controles da barra de comando do Visual Studio. No entanto, se for necessário para você construir sua própria barra de comando, certifique-se de estilizá-la corretamente usando os seguintes nomes de token.

![Barra de comando linha vermelha](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Barra de comando (linha vermelha)

![Linha vermelha do botão de transbordamento](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Botão de estouro (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... em lugares onde você precisa de uma barra de comando incorporada, mas não pode usar a implementação padrão da barra de comando do Visual Studio. | ... para elementos de IA que não são semelhantes a uma barra de comando. |
| | ... para componentes da barra de comando que não sejam aqueles para os quais os nomes de token são especificados. |

#### <a name="command-bar-groups"></a>Grupos de barras de comando
Um grupo de barras de comando consiste em um conjunto relacionado de controles de barra de comando e pode conter qualquer número de botões, botões divididos, menus suspensos, caixas de combinação ou menus. As cores para esses controles são reguladas por nomes de tokens separados e são discutidas individualmente em outros lugares neste guia. Uma linha separadora é usada para dividir um grupo de barras de comando em subgrupos relacionados.

![Linha vermelha do grupo de barras de comando](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Grupo de barras de comando (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... em lugares onde você precisa de uma barra de comando incorporada, mas não pode usar a implementação padrão da barra de comando do Visual Studio. | ... para elementos de IA que não são semelhantes a uma barra de comando. |
| | ... para componentes da barra de comando que não sejam aqueles para os quais os nomes de token são especificados. |

**Grupo de barras de comando: estado padrão**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarGradientBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Borda | `Environment.CommandBarToolBarBorder` |
| Identificador de arrastar | `Environment.CommandBarDragHandle` |
| Separador | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Ícones de comando
![Ícone de comando linha vermelha](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Ícone de comando (linha vermelha)

![Ícone de comando com linha vermelha de texto](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Ícone de comando com texto (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... para quaisquer botões que serão colocados em uma barra de comando. | ... para controles que têm seus próprios nomes de tokens. |
| | ... em qualquer combinação de plano de fundo/primeiro plano que não seja especificada. |

**Ícone de comando: estado padrão**

![Padrão do ícone de comando](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Ícone de comando padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | N/A (herda do fundo da barra de comando) |
| Primeiro plano (Texto) | `Environment.CommandBarTextActive` |
| Borda | N/D |

**Ícone de comando: estado padrão, selecionado**

![Ícone de comando padrão e selecionado](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Ícone de comando padrão e selecionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarSelected` |
| Primeiro plano (Texto) | `Environment.CommandBarTextSelected` |
| Borda | `Environment.CommandBarSelectedBorder` |

**Ícone de comando: pairando ou estados de foco**

![Ícone de comando em pairam ou foco](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Ícone de comando em pairam ou foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarMouseOverBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.CommandBarTextHover` |
| Borda | `Environment.CommandBarBorder` |

**Ícone de comando: hover ou estados de foco, selecionados**

![Ícone de comando selecionado em pairam ou foco](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Ícone de comando selecionado em pairam ou foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarHoverOverSelected` |
| Primeiro plano (Texto) | `Environment.CommandBarTextHoverOverSelected` |
| Borda | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Ícone de comando: estado pressionado**

![Ícone de comando pressionado](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Ícone de comando pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarMouseDownBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.CommandBarTextMouseDown` |
| Borda | `Environment.CommandBarBorder` |

**Ícone de comando: estado desativado**

![Ícone de comando desativado](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Ícone de comando desativado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | N/A (herda do fundo da barra de comando) |
| Primeiro plano (Texto) | `Environment.CommandBarTextInactive` |
| Borda | N/D |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a>Caixas de combinação de barra de comando

> [!IMPORTANT]
> As caixas de combo são semelhantes às gotas, mas incluem uma região de texto editável. Se a sua parada de texto não incluir uma região de texto editável, use os tokens de cor para [as gotas da barra de comando](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Ordem de combo da barra de comando redline](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Caixa de combinação da barra de comando (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... ao construir caixas de combinação personalizadas. | ... para qualquer coisa que você não quer sempre corresponder a ui barra de comando. |
| ... ao criar um controle de barra de comando semelhante a uma caixa de combinação. | ... quando você tem acesso a uma caixa de combinação estilizada. |

**Campo de entrada da caixa de combo da barra de comando: estado padrão**

![Campo de entrada da caixa de combo da barra de comando](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Campo de entrada da caixa de combo da barra de comando

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ComboBoxBackground` |
| Primeiro plano (Texto) | `Environment.ComboBoxText` |
| Borda | `Environment.ComboBoxBorder` |
| Separador | Sem separador |

**Botão de baixa da barra de comando: estado padrão**

![Caixa de combinação botão de abaixado&#45;](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Botão de parada da barra de comando

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | N/A (herda do fundo da barra de comando) |
| Primeiro plano (Glifo) | `Environment.ComboBoxGlyph` |

**Lista de baixa da barra de comando: estado padrão**

![Lista de parada da barra de comando](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Lista de parada da barra de comando

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ComboBoxPopupBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.ComboBoxItemText` |
| Borda | `Environment.ComboBoxPopupBorder` |

**Campo de entrada da caixa de combo da barra de comando: estado de hover**

![Campo de entrada da caixa de combo da barra de comando no hover](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Campo de entrada da caixa de combo da barra de comando no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.ComboBoxMouseOverText` |
| Borda | `Environment.ComboBoxMouseOverBorder` |
| Separador | `Environment.ComboBoxMouseOverSeparator` |

 **Botão de queda da barra de comando: estado de hover**

![Botão de parada da barra de comando no hover](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Botão de parada da barra de comando no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ComboBoxButtonMouseOverBackground` |
| Primeiro plano (Glifo) | `Environment.ComboBoxMouseOverGlyph` |

**Lista de parada da barra de comando: estado de hover**

 ![Lista de parada da barra de comando no hover](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Lista de parada da barra de comando no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Plano de fundo (item do menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Primeiro plano (Texto) | `Environment.ComboBoxItemMouseOverText` |
| Borda (item do menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo de entrada da caixa de combo da barra de comando: estado focado**

![Campo de entrada de caixa de combo de barra de comando focado](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Campo de entrada de caixa de combo de barra de comando focado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ComboBoxFocusedBackground` |
| Primeiro plano (Texto) | `Environment.ComboBoxFocusedText` |
| Borda | `Environment.ComboBoxFocusedBorder` |
| Separador | `Environment.ComboBoxFocusedButtonSeparator` |

**Botão de baixa da barra de comando: estado focado**

![Botão de baixa da barra de comando focado](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Botão de baixa da barra de comando focado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ComboBoxFocusedButtonBackground` |
| Primeiro plano (Glifo) | `Environment.ComboBoxFocusedGlyph` |

 **Campo de entrada da caixa de combo da barra de comando: estado pressionado**

![Campo de entrada da caixa de combo da barra de comando pressionado](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Campo de entrada da caixa de combo da barra de comando pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ComboBoxMouseDownBackground` |
| Primeiro plano (Texto) | `Environment.ComboBoxMouseDownText` |
| Borda | `Environment.ComboBoxMouseDownBorder` |
| Separador | `Environment.ComboBoxMouseDownSeparator` |

**Botão de baixa da barra de comando: estado pressionado**

![Botão de disquete da barra de comando pressionado](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Botão de disquete da barra de comando pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ComboBoxButtonMouseDownBackground` |
| Primeiro plano (Glifo) | `Environment.ComboBoxMouseDownGlyph` |

**Campo de entrada da caixa de combo da barra de comando: estado desativado**

![Campo de entrada de caixa de combo de barra de comando desativado](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Campo de entrada de caixa de combo de barra de comando desativado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ComboBoxDisabledBackground` |
| Primeiro plano (Texto) | `Environment.ComboBoxDisabledText` |
| Borda | `Environment.ComboBoxDisabledBorder` |
| Separador | Sem separador |

**Botão de baixa da barra de comando: estado desativado**

![Botão de baixa da barra de comando desativado](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Botão de baixa da barra de comando desativado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | Nenhum |
| Primeiro plano (Glifo) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a>Drop-downs da barra de comando

> [!IMPORTANT]
> As drop-downs são semelhantes às caixas de combinação, mas não possuem regiões de texto editáveis. Se a sua parada estivista incluir uma região de texto editável, use os tokens de cor para [caixas de combinação de barra de comando](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Barra de comando drop-down (linha vermelha)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Barra de comando drop-down (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... quando você está criando controles de lista baixa personalizados. | ... para qualquer coisa que não seja semelhante a uma lista de paradas. |
| | ... para caixas de combinação ou botões divididos. |

**Campo de seleção da barra de comando: estado padrão**

![Campo de seleção de barra de comando padrão](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Campo de seleção de barra de comando padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.DropDownBackground` |
| Primeiro plano (Texto) | `DropDownText` |
| Borda | `DropDownBorder` |
| Separador | Sem separador |

**Botão de baixa da barra de comando: estado padrão**

![Botão de baixa da barra de comando padrão](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Botão de baixa da barra de comando padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | Nenhum |
| Primeiro plano (Glifo) | `Environment.DropDownGlyph` |

**Lista de baixa da barra de comando: estado padrão**

![Lista de estionda da barra de comando padrão](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Lista de estionda da barra de comando padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.DropDownPopupBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.ComboBoxItemText` |
| Borda | `Environment.DropDownPopupBorder` |
| Shadow | `Environment.DropShadowBackground` |

**Campo de seleção da barra de comando: estado de hover**

![Campo de seleção de barra de comando em hover](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Campo de seleção de barra de comando em hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.DropDownMouseOverBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.DropDownMouseOverText` |
| Borda | `Environment.DropDownMouseOverBorder` |
| Separador | `Environment.DropDownButtonMouseOverSeparator` |

**Botão de queda da barra de comando: estado de hover**

![Botão de parada da barra de comando no hover](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Botão de parada da barra de comando no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.DropDownButtonMouseOverBackground` |
| Primeiro plano (Glifo) | `Environment.DropDownMouseOverGlyph` |

**Lista de parada da barra de comando: estado de hover**

![Lista de parada da barra de comando no hover](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Lista de parada da barra de comando no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Plano de fundo (item do menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Primeiro plano (Texto) | `Environment.ComboBoxItemMouseOverText` |
| Borda (item do menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo de seleção da barra de comando: estado pressionado**

![Drop&#45;campo de seleção pressionado](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Campo de seleção da barra de comando pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.DropDownMouseDownBackground` |
| Primeiro plano (Texto) | `Environment.DropDownMouseDownText` |
| Borda | `Environment.DropDownMouseDownBorder` |
| Separador | `Environment.DropDownButtonMouseDownSeparator` |

**Botão de baixa da barra de comando: estado pressionado**

![Botão de disquete da barra de comando pressionado](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Botão de disquete da barra de comando pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.DropDownButtonMouseDownBackground` |
| Primeiro plano (Glifo) | `Environment.DropDownMouseDownGlyph` |

**Campo de seleção da barra de comando: estado desativado**

![Campo de seleção de barra de comando desativado](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Campo de seleção de barra de comando desativado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.DropDownDisabledBackground` |
| Primeiro plano (Texto) | `Environment.DropDownDisabledText` |
| Borda | `Environment.DropDownDisabledBorder` |
| Separador | Sem separador |

**Botão de baixa da barra de comando: estado desativado**

![Botão de baixa da barra de comando desativado](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Botão de baixa da barra de comando desativado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | N/D |
| Primeiro plano (Glifo) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Botões de divisão da barra de comando
Os botões divididos compartilham muitos nomes de tokens com outros controles da barra de comando, como botões, menus e texto da barra de comando. Todas as ações necessárias e nomes de token de botão de baixa são repetidos aqui por conveniência. Listas de parada de botões divididos são implementações de [menus](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)de barras de comando .

![Linha vermelha do botão de divisão](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Botão de divisão da barra de comando (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... quando você está criando um botão de divisão personalizado. | ... para outros tipos de botões. |
| | ... em qualquer combinação de plano de fundo/primeiro plano que não seja especificada. |

**Botão de divisão da barra de comando: estado padrão**

![Botão de divisão da barra de comando padrão](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Botão de divisão da barra de comando padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | Nenhum |
| Primeiro plano (Texto) | `Environment.CommandBarTextActive` |
| Primeiro plano (Glifo) | `Environment.CommandBarSplitButtonGlyph` |
| Borda | N/D |
| Separador | N/D |

**Botão de divisão da barra de comando: estado de hover**

![Botão de divisão da barra de comando no hover](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Botão de divisão da barra de comando no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarMouseOverBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.CommandBarTextHover` |
| Primeiro plano (Glifo) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Borda | `Environment.CommandBarBorder` |
| Separador | `Environment.CommandBarSplitButtonSeparator` |

**Botão de divisão da barra de comando: estado pressionado**

![Botão de divisão da barra de comando pressionado](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Botão de divisão da barra de comando pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarMouseDownBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.CommandBarTextMouseDown` |
| Primeiro plano (Glifo) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Borda | `Environment.CommandBarBorder` |
| Separador | N/D |

**Botão de divisão da barra de comando: estado desativado**

![Botão de divisão da barra de comando desativado](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Botão de divisão da barra de comando desativado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | N/D |
| Primeiro plano (Texto) | `Environment.ComboBoxItemTextInactive` |
| Primeiro plano (Glifo) | `Environment.CommandBarTextInactive` |
| Borda | N/D |
| Separador | N/D |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Barra de comando 'Mais opções' e botões 'Estouro'
O botão "Mais opções" é usado quando um grupo de barras de comando é personalizável adicionando ou removendo botões relacionados da barra de comando. O botão "Estouro" aparece quando uma barra de comando é truncada devido à falta de espaço horizontal, e no clique mostra um menu contendo os botões da barra de comando que não podem ser exibidos. As cores desses dois botões são controladas pelo mesmo conjunto de nomes de tokens.

![Botão 'Mais opções' da barra de comando (linha vermelha)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Botão 'Mais opções' da barra de comando (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... para botões personalizados 'Mais opções' ou 'Estouro'. | ... para botões que não têm funcionalidade semelhante a um botão 'Mais opções' ou 'Estouro'. |

**Barra de comando 'Mais opções' e 'Estouro': estado padrão**

![Botão 'Mais opções' da barra de comando padrão](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Botão 'Mais opções' da barra de comando padrão

![Botão 'Estouro' da barra de comando padrão](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Botão 'Estouro' da barra de comando padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarOptionsBackground` |
| Primeiro plano (Glifo) | `Environment.CommandBarOptionsGlyph` |

**Barra de comando 'Mais opções' e 'Estouro': estado de hover**

![Botão 'Mais opções' da barra de comando no hover](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Botão 'Mais opções' da barra de comando no hover

![Botão 'Estouro' da barra de comando no hover](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Botão 'Estouro' da barra de comando no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Barra de comando 'Mais opções' e 'Estouro': estado pressionado**

![Botão 'Mais opções' da barra de comando pressionada](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Botão 'Mais opções' da barra de comando pressionada

![Estouro pressionado](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Botão 'Estouro' da barra de comando pressionado

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Janelas de documentos
Não há necessidade de replicar janelas de documentos, porque elas são fornecidas pelo ambiente do Visual Studio. No entanto, você pode decidir que deseja aproveitar as cores usadas nas janelas de documentos para que sua ida e vida também pareça consistente com esta parte do ambiente do Visual Studio.

Ao usar tokens de cor da janela do documento, tenha cuidado ao usá-los apenas para elementos semelhantes e sempre em pares. Se você não fizer isso, você pode obter resultados inesperados em sua ui.

### <a name="document-window-frames"></a>Quadros de janelas de documentos
Janelas de documento podem ser encaixadas no IDE ou flutuando como uma janela separada. Quando uma janela de documento está flutuando fora do IDE, ela ainda se senta bem em um documento e tem cores de fundo, borda, texto e guia que são as mesmas de quando faz parte do IDE. No entanto, o documento fica dentro de um quadro que tem seu próprio plano de fundo, borda e cores de texto. Quando as janelas da ferramenta estão encaixadas bem no documento, elas herdam o comportamento e a cor de suas guias a partir de nomes de tokens de janelas de documento.

![Janela de documento ancorada (linha vermelha)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Janela de documento ancorada (linha vermelha)

![Janela de documento flutuante (linha vermelha)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Janela de documento flutuante (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... em qualquer lugar que você está criando ui que você deseja combinar a janela do documento. | ...  para qualquer ui que você não deseja mudar automaticamente se o shell tiver uma atualização de tema. |

**Janela de documento ancorada ou flutuante: estado padrão**

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | Depende do tipo de documento |
| Primeiro plano (Texto) | Depende do tipo de documento |
| Borda | `Environment.ToolWindowBorder` |

**Quadro de janela de documento flutuante focado: estado padrão**

![Padrão focado, quadro de janela de documento flutuante](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Padrão focado, quadro de janela de documento flutuante

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowFloatingFrame` |
| Primeiro plano (Texto) | `Environment.ToolWindowFloatingFrame` |
| Primeiro plano (Glifo) | `Environment.RaftedWindowButtonActiveGlyph` |
| Borda | `Environment.MainWindowActiveDefaultBorder` |
| Borda (Glifo) | `Environment.RaftedWindowButtonActiveBorder`<br />(Definido como transparente) |

**Quadro de janela de documento flutuante e desfocado: estado padrão**

![Padrão desfocado, quadro de janela de documento flutuante](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Padrão desfocado, quadro de janela de documento flutuante

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowFloatingFrameInactive` |
| Primeiro plano (Texto) | `Environment.ToolWindowFloatingFrameInactive` |
| Primeiro plano (Glifo) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Borda | `Environment.MainWindowInactiveBorder` |
| Borda (Glifo) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Definido como transparente) |

**Quadro da janela do documento flutuante focado: estado de pairar**

![Quadro de janela de documento flutuante focado no pairar](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Quadro de janela de documento flutuante focado no pairar

| Elemento | Nome do token: Category.color |
| --- | --- |
| Fundo (Glifo) | `Environment.RaftedWindowButtonHoverActive` |
| Primeiro plano (Glifo) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Borda (Glifo) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Quadro da janela do documento flutuante e desfocado: estado de pairar**

![Quadro de janela de documento flutuante e desfocado no pairar](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Quadro de janela de documento flutuante e desfocado no pairar

| Elemento | Nome do token: Category.color |
| --- | --- |
| Fundo (Glifo) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Primeiro plano (Glifo) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Borda (Glifo) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Quadro da janela do documento flutuante focado: estado pressionado**

![Quadro da janela do documento flutuante focado na prensa](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Quadro da janela do documento flutuante focado na prensa

| Elemento | Nome do token: Category.color |
| --- | --- |
| Fundo (Glifo) | `Environment.RaftedWindowButtonDown` |
| Primeiro plano (Glifo) | `Environment.RaftedWindowButtonDownGlyph` |
| Borda (Glifo) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Guias de documento
As guias de documento ficam no canal da guia para indicar quais documentos estão abertos no momento, juntamente com qual deles é o documento selecionado ou ativo atual. As janelas da ferramenta também podem ser encaixadas no canal da guia de documentos se o usuário as colocar lá. Nesta situação, eles usam as mesmas cores de guia que janelas de documento. Se você estiver criando a ui que deseja sempre corresponder às cores da janela do documento (incluindo atualizações de temas ou se novos temas forem instalados), faça referência a esses tokens de cor.

![Guias de documentos (linha vermelha)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Guias de documentos (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... em qualquer lugar que você está criando uI que você deseja combinar guias de documentos e pegar automaticamente atualizações temáticas ou novas cores temáticas. | ... para qualquer ui que você não queira alterar automaticamente quando o shell tiver uma atualização de tema. |

#### <a name="open-document-tabs"></a>Abrir guias de documentos
Cada documento aberto tem uma guia no canal da guia de documentos que exibe seu nome. Os documentos podem ser selecionados ou abertos em segundo plano, e suas guias refletem esses estados:

- A guia selecionada representa bem o documento exibido no documento. Uma guia selecionada tem uma borda de documento que se estende pela borda superior do documento.

- Guias de fundo são as guias de documento que não são a guia selecionada no momento. Uma vez clicados, eles se tornam a guia selecionada e adquirem todas as cores de fundo, borda e texto desses nomes de token.

![Abra a guia de documentos (linha vermelha)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Abra a guia de documentos (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... quando você está criando guias personalizadas de documentos. | ... para guias provisórias (visualização). |
| | ... para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema. |

**Guia de documento selecionada e focada**

![Guia de documento selecionada e focada](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Guia de documento selecionada e focada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.FileTabSelectedGradientTop`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.FileTabSelectedText` |
| Borda | `Environment.FileTabSelectedBorder`<br />(Definir para a mesma cor que o fundo.) |
| Fronteira do documento | `Environment.FileTabDocumentBorderBackground` |

**Guia de documento selecionada e sem foco**

![Guia de documento selecionada e sem foco](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Guia de documento selecionada e sem foco

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.FileTabInactiveGradientTop`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.FileTabInactiveText` |
| Borda | `Environment.FileTabInactiveBorder`<br />(Definir para a mesma cor que o fundo.) |
| Fronteira do documento | `Environment.FileTabInactiveDocumentBorderBackground` |

**Guia de documento de fundo: estado padrão**

![Guia de documento de fundo padrão](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Guia de documento de fundo padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.FileTabBackground` |
| Primeiro plano (Texto) | `Environment.FileTabText` |
| Borda | `Environment.FileTabBorder`<br />(Definir para a mesma cor que o fundo.) |

**Guia de documento de fundo: estado de hover**

![Guia de documento de fundo no hover](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Guia de documento de fundo no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.FileTabHotGradientTop`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.FileTabHotText` |
| Borda | `Environment.FileTabHotBorder`<br />(Definir para a mesma cor que o fundo.) |

#### <a name="preview-tab"></a>Guia de visualização
Também chamado de guia "provisória". A guia de visualização aparece no lado direito do canal da guia do documento quando o usuário clica em um item na janela da ferramenta Solution Explorer. Ele funciona como uma visualização do documento e também dá ao usuário a opção de manter o documento aberto no lado esquerdo do canal da guia do documento. Apenas uma guia de visualização aberta pode ser aberta de cada vez. As guias de visualização têm tanto o plano de fundo quanto os estados selecionados, como guias abertas, e podem ser focadas ou desfocadas em seu estado ativo.

![Guia de visualização (linha vermelha)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Guia de visualização (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... em qualquer lugar que você está criando visualização provisória e deseja que algum elemento corresponda à cor da guia de visualização atual. | ... para qualquer tipo de documento ou guia que não seja provisória (visualização). |
| | ... para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema. |

**Guia de visualização focada e selecionada**

![Guia de visualização focada e selecionada](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Guia de visualização focada e selecionada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.FileTabProvisionalSelectedActive` |
| Primeiro plano (Texto) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Borda | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Definir para a mesma cor que o fundo.) |
| Fronteira do documento | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Guia de visualização desfocada e selecionada**

![Guia de visualização desfocada e selecionada](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Guia de visualização desfocada e selecionada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.FileTabProvisionalSelectedInactive` |
| Primeiro plano (Texto) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Borda | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Fronteira do documento | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Guia de visualização de fundo: estado padrão**

![Guia de visualização de plano de fundo padrão](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Guia de visualização de plano de fundo padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.FileTabProvisionalInactive` |
| Primeiro plano (Texto) | `Environment.FileTabProvisionalInactiveForeground` |
| Borda | `Environment.FileTabProvisionalInactiveBorder`<br />(Definir para a mesma cor que o fundo.) |

**Guia de visualização de fundo: estado de hover**

![Guia de visualização de fundo no hover](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Guia de visualização de fundo no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.FileTabProvisionalHover` |
| Primeiro plano (Texto) | `Environment.FileTabProvisionalHoverForeground` |
| Borda | `Environment.FileTabProvisionalHoverBorder`<br />(Definir para a mesma cor que o fundo.) |

#### <a name="document-overflow-button"></a>Botão de estouro de documento
O botão de estouro de documento está presente se houver um ou mais documentos abertos, independentemente de haver espaço vertical na configuração atual para caber todas as guias do documento. O menu suspenso de estouro de estouro de documento, que é controlado pelas cores do menu da barra de [comando,](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) exibe uma lista de todos os documentos abertos, visíveis e ocultos, e o glifo de transbordamento muda dependendo se todos os documentos abertos são exibidos no canal da guia.

![Botão de estouro de documento (linha vermelha)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Botão de estouro de documento (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... quando você está criando um botão de estouro de documento personalizado. | ... para iU que não é semelhante a um botão de estouro. |
| | ... para botões de estouro da barra de comando. |

**Botão de estouro do documento: estado padrão**

![Botão de estouro de documento padrão](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Botão de estouro de documento padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.DocWellOverflowButtonBackground` |
| Primeiro plano (Glifo) | `Environment.DocWellOverflowButtonGlyph` |
| Borda | N/D |

**Botão de estouro do documento: estado de sobrecarga**

![Botão de estouro de documento em pairar](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Botão de estouro de documento em pairar

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Primeiro plano (Glifo) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Borda | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Botão de estouro do documento: estado pressionado**

![Botão de estouro de documento na pressão](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Botão de estouro de documento na pressão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Primeiro plano (Glifo) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Borda | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Marcação
O Visual Studio suporta a marcação, que permite que um usuário declare palavras-chave pesquisáveis para fins de rastreamento. Por exemplo, gerentes de projeto e desenvolvedores podem usar o Team Foundation Server (TFS) para marcar itens de trabalho. As tabelas abaixo dão nomes de cores tanto para a tag em si quanto para o glifo "ícone de fechamento" que aparece em hover e estados selecionados.

![Marcação no Visual Studio (linha vermelha)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Marcação no Visual Studio (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... para a UI que suporta a marcação. | ... para qualquer outro tipo de ui. |

#### <a name="tags"></a>Marcas

**Tag: estado padrão**

![Tag padrão](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Tag padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Tag.Background` |
| Primeiro plano (Texto) | `Tag.Background` |

**Tag: estado de hover**

![Tag on hover](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Tag on hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Tag.HoverBackground` |
| Primeiro plano (Texto) | `Tag.HoverBackgroundText` |

**Tag: estado pressionado**

![Tag pressionada](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Tag pressionada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Tag.PressedBackground` |
| Primeiro plano (Texto) | `Tag.PressedBackgroundText` |

**Tag: estado selecionado**

![Tag selecionada](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Tag selecionada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Tag.SelectedBackground` |
| Primeiro plano (Texto) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Fechar&times;( ) gifa tag

**Fechar&times;( ) glyph tag: estado padrão**

![Gifo&times;de tag (Fechamento padrão)](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Gifo&times;de tag (Fechamento padrão)

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | N/D |
| Primeiro plano (Glifo) | `Tag.TagHoverGlyph` |

**Fechar&times;( ) tag gliph: hover state**

![Fechar&times;( ) tag gliph no hover](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Fechar&times;( ) tag gliph no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Tag.TagHoverGlyphHoverBackground` |
| Primeiro plano (Glifo) | `Tag.TagHoverGlyphHover` |
| Borda | `Tag.TagHoverGlyphHoverBorder` |

**Fechar&times;( ) gifo de tag: estado pressionado**

![Fecho&times;de fechamento pressionado ( ) tag glifo](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Fecho&times;de fechamento pressionado ( ) tag glifo

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Tag.TagHoverGlyphPressedBackground` |
| Primeiro plano (Glifo) | `Tag.TagHoverGlyphPressed` |
| Borda | `Tag.TagHoverGlyphPressedBorder` |

**Tag selecionada com&times;glifo de fechamento ( ) : estado padrão**

![Tag selecionada padrão&times;com glyph de fechamento ()](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Tag selecionada padrão&times;com glyph de fechamento ()

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | N/D |
| Primeiro plano (Glifo) | `Tag.TagSelectedGlyph` |

**Tag selecionada com&times;glifo de fechamento ( ) : hover state**

![Tag selecionada com&times;glifo de fechamento () no hover](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Tag selecionada com&times;glifo de fechamento () no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Tag.TagSelectedGlyphHoverBackground` |
| Primeiro plano (Glifo) | `Tag.TagSelectedGlyphHover` |
| Borda | `Tag.TagSelectedGlyphHoverBorder` |

**Tag selecionada com&times;glifo de fechamento ( ) : estado pressionado**

![Selecionado, pressionado tag&times;com glyph Close ( )](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Selecionado, pressionado tag&times;com glyph Close ( )

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Tag.TagSelectedGlyphPressedBackground` |
| Primeiro plano (Glifo) | `Tag.TagSelectedGlyphPressed` |
| Borda | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Janelas da ferramenta
Não há necessidade de replicar janelas de ferramentas, porque elas são fornecidas pelo ambiente do Visual Studio. No entanto, você pode decidir que deseja aproveitar as cores usadas nas janelas das ferramentas para que sua ida e vida também pareça consistente com esta parte do ambiente do Visual Studio.

![Janela da ferramenta (linha vermelha)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Janela da ferramenta (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... em qualquer lugar que você está criando ui que você deseja combinar janelas de ferramentas. | ... para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema. |

### <a name="tool-window-frame"></a>Quadro da janela da ferramenta
Janelas de ferramentas no Visual Studio são usadas para muitas tarefas diferentes, e podem existir em um dos vários estados diferentes. Se uma janela de ferramenta estiver aberta, ela pode ser atribuída a qualquer um dos quatro lados da área do documento. As janelas de ferramentas também podem flutuar fora do IDE, o que permite que eles sejam reposicionados em qualquer lugar dentro da tela do usuário. Janelas flutuantes sempre se sentam em cima do IDE. Finalmente, as janelas das ferramentas podem ser encaixadas como janelas de documentos e aparecer como uma guia no documento bem. Janelas de ferramentas que foram encaixadas como janelas de documentos são coloridas em parte usando nomes de token de janela de documento.

![Quadro da janela da ferramenta (linha vermelha)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Quadro da janela da ferramenta (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ...  em qualquer lugar que você está criando ui que você deseja combinar janelas de ferramentas. | ... para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema. |

**Janela de ferramenta ancorada**

![Janela de ferramenta ancorada](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Janela de ferramenta ancorada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowBackground` |
| Borda | `Environment.ToolWindowBorder` |

**Janela de ferramenta flutuante e focada**

![Janela de ferramenta flutuante e focada](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Janela de ferramenta flutuante e focada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowBackground` |
| Borda | `Environment.MainWindowActiveDefaultBorder` |

**Janela de ferramentas flutuante e desfocada**

![Janela de ferramentas flutuante e desfocada](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Janela de ferramentas flutuante e desfocada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowBackground` |
| Borda | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Janelas semelhantes a caixas de ferramentas
A caixa de ferramentas é uma das janelas de ferramentas mais usadas no Visual Studio. É essencialmente um controle de árvore com um tema especial e estilo aplicado.

![Janela semelhante a caixa de ferramentas (linha vermelha)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Janela semelhante a caixa de ferramentas (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... quando você está projetando uma janela de ferramenta que você deseja ser sempre consistente com a caixa de ferramentas shell. | ... para qualquer coisa que não seja semelhante à ui da caixa de ferramentas, ou se você não tem certeza se sua iu terá problemas se as cores da caixa de ferramentas shell mudarem. |

**Nó da caixa de ferramentas: estado padrão**

![Nó pai da caixa de ferramentas padrão](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Nó pai da caixa de ferramentas padrão

![Nó de criança da caixa de ferramentas padrão](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Nó de criança da caixa de ferramentas padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolboxContent`<br />(Títulos) |
| Segundo plano | `Environment.ToolWindowBackground`<br />(Itens individuais ou janela inteira se não houver controles disponíveis) |
| Borda | Nenhum |
| Primeiro plano (Glifo) | `Environment.ToolboxContent` |
| Primeiro plano (Texto) | `Environment.ToolboxContent` |

**Nó de criança caixa de ferramentas: estado de hover**

![Nó de criança caixa de ferramentas no hover](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Nó de criança caixa de ferramentas no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolboxContentMouseOver`<br />(Somente itens individuais) |
| Borda | Nenhum |
| Primeiro plano (Texto) | `Environment.ToolboxContentMouseOver`<br />(Somente itens individuais) |

**Nó de caixa de ferramentas selecionado: estado focado**

![Foco, nó pai da caixa de ferramentas selecionada](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Foco, nó pai da caixa de ferramentas selecionada

![Foco, nó de criança caixa de ferramentas selecionada](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Foco, nó de criança caixa de ferramentas selecionada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `TreeView.SelectedItemActive`<br />Da categoria [de visualização de](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) árvore |
| Borda | `TreeView.FocusVisualBorder`<br />Da categoria [de visualização de](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) árvore |
| Primeiro plano (Glifo) | `TreeView.SelectedItemActive`<br />Da categoria [de visualização de](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) árvore |
| Primeiro plano (Texto) | `TreeView.SelectedItemActive`<br />Da categoria [de visualização de](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) árvore |

**Nó de caixa de ferramentas selecionado: estado desfocado**

![Nó pai da caixa de ferramentas selecionada e desfocada](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Nó pai da caixa de ferramentas selecionada e desfocada

![Nó de criança da caixa de ferramentas selecionada e desfocada](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Nó de criança da caixa de ferramentas selecionada e desfocada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `TreeView.SelectedItemInactive`<br />Da categoria [de visualização de](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) árvore |
| Borda | Nenhum |
| Primeiro plano (Glifo) | `TreeView.SelectedItemInactive`<br />Da categoria [de visualização de](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) árvore |
| Primeiro plano (Texto) | `TreeView.SelectedItemInactive`<br />Da categoria [de visualização de](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) árvore |

### <a name="tool-window-title-bar"></a>Barra de título da janela da ferramenta
A fronteira da barra do título não é uma fronteira verdadeira, é uma linha grossa do outro lado da barra de título. Ele não tem um nome simbólico para seu estado desfocado.

![Barra de título da janela da ferramenta (linha vermelha)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Barra de título da janela da ferramenta (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... em qualquer lugar que você está criando ui que você deseja combinar janelas de ferramentas. | ... para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema. |

**Barra de título focada**

![Barra de título focada](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Barra de título focada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.TitleBarActiveGradientBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.TitleBarActiveText` |
| Borda | `Environment.TitleBarActiveBorder`<br />(Definir para a mesma cor que o fundo.) |
| Identificador de arrastar | `Environment.TitleBarDragHandleActive` |

**Barra de título desfocada**

![Barra de título desfocada](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Barra de título desfocada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.TitleBarInactiveGradientBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.TitleBarInactiveText` |
| Borda | N/D |
| Identificador de arrastar | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Botões da barra de título da janela da ferramenta
![Botão da barra de título (linha vermelha)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Botão da barra de título (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... para botões que aparecem em UI que usa tokens de cor das barras de título da janela da ferramenta. | ... para botões que aparecem em outros locais. |
| | ... em qualquer combinação de plano de fundo/primeiro plano que não seja especificada. |

**Botões de barra de título focados: estado padrão**

![Botões padrão e focados na barra de título](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Botões padrão e focados na barra de título

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | N/D |
| Primeiro plano (Glifo) | `Environment.ToolWindowButtonActiveGlyph` |
| Borda | N/D |

**Botões de barra de título sem foco: estado padrão**

![Botões padrão e desfocados da barra de título](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Botões padrão e desfocados da barra de título

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | N/D |
| Primeiro plano (Glifo) | `Environment.ToolWindowButtonInactiveGlyph` |
| Borda | N/D |

**Botões de barra de título focados: estado de hover**

![Botões de barra de título focados no hover](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Botões de barra de título focados no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowButtonHoverActive` |
| Primeiro plano (Glifo) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Borda | `Environment.ToolWindowButtonHoverActiveBorder` |

**Botões de barra de título desfocados: estado de hover**

![Botões de barra de título desfocados no hover](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Botões de barra de título desfocados no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowButtonHoverInactive` |
| Primeiro plano (Glifo) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Borda | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Botões de barra de título focados: estado pressionado**

![Botões de barra de título focados na pressão](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Botões de barra de título focados na pressão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowButtonDown` |
| Primeiro plano (Glifo) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Borda | `Environment.ToolWindowButtonDownBorder` |

**Botões de barra de título desfocados: estado pressionado**

![Botões de barra de título desfocados na pressão](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Botões de barra de título desfocados na pressão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowButtonDown` |
| Primeiro plano (Glifo) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Borda | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Guias de janela de ferramenta
![Guia da janela da ferramenta (linha vermelha)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Guia da janela da ferramenta (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... em qualquer lugar que você está criando ui que você deseja combinar janelas de ferramentas. | ... para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema. |

**Guia de janela de ferramenta selecionada e focada**

![Guia de janela de ferramenta selecionada e focada](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Guia de janela de ferramenta selecionada e focada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowTabSelectedTab` |
| Primeiro plano (Texto) | `Environment.ToolWindowTabSelectedActiveText` |
| Borda | `Environment.ToolWindowTabSelectedBorder`<br />(Definir para a mesma cor que o fundo.) |

**Guia de janela de ferramenta selecionada e desfocada**

![Guia de janela de ferramenta selecionada e desfocada](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Guia de janela de ferramenta selecionada e desfocada

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowTabSelectedTab` |
| Primeiro plano (Texto) | `Environment.ToolWindowTabSelectedText` |
| Borda | `Environment.ToolWindowTabSelectedBorder`<br />(Definir para a mesma cor que o fundo.) |

**Guia da janela da ferramenta de fundo: estado padrão**

![Guia de janela de ferramenta de fundo padrão](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Guia de janela de ferramenta de fundo padrão

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(O gradiente pára definido para o mesmo valor de cor no Visual Studio 2013.) |
| Primeiro plano (Texto) | `Environment.ToolWindowTabText` |
| Borda | `Environment.ToolWindowTabBorder` |

**Guia da janela da ferramenta de fundo: estado de hover**

![Guia da janela da ferramenta de fundo no hover](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Guia da janela da ferramenta de fundo no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(O gradiente pára definido para o mesmo valor de cor no Visual Studio 2013.) |
| Primeiro plano (Texto) | `Environment.ToolWindowTabMouseOverText` |
| Borda | `Environment.ToolWindowTabMouseOverBorder`<br />(Definir para a mesma cor que o fundo.) |

### <a name="auto-hide-tabs"></a>Guias de ocultação automática

![Guias de ocultação automática (linha vermelha)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Guias de ocultação automática (linha vermelha)

| Usar... | Não use... |
| --- | --- |
| ... em qualquer lugar que você está criando ui que você deseja combinar guias de janela de ferramenta automaticamente ocultas. | ... para qualquer ui que você não queira alterar automaticamente se o shell tiver uma atualização de tema. |

**Guias de ocultação automática: estado padrão**

![Guia padrão de ocultação automática](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Guia padrão de ocultação automática

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.AutoHideTabBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.AutoHideTabText` |
| Borda | `Environment.AutoHideTabBorder` |

**Guias de ocultação automática: estado de hover**

![Guia de ocultação automática no hover](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Guia de ocultação automática no hover

| Elemento | Nome do token: Category.color |
| --- | --- |
| Segundo plano | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(O gradiente pára para este token não usado em ui temática.) |
| Primeiro plano (Texto) | `Environment.AutoHideTabMouseOverText` |
| Borda | `Environment.AutoHideTabMouseOverBorder` |
