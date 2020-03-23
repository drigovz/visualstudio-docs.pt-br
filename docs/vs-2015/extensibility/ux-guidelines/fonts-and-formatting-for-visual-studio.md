---
title: Fontes e formatação
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ede8844b34473e1c900bd6af040cac99ceee1514
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302409"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Fontes e formatação para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>A fonte do ambiente
 Todas as fontes dentro do Visual Studio devem ser expostas ao usuário para personalização. Isso é feito principalmente através da página **Fontes e Cores** na caixa de diálogo Ferramentas > **Opções.** As três principais categorias de configurações de fonte são:

- **Fonte do ambiente** — a fonte principal do IDE (ambiente de desenvolvimento integrado), usada para todos os elementos da interface, incluindo diálogos, menus, janelas de ferramentas e janelas de documentos. Por padrão, a fonte do ambiente está vinculada a uma fonte do sistema que aparece como 9 pt Segoe UI nas versões atuais do Windows. O uso de uma fonte para todos os elementos da interface ajuda a garantir uma aparência de fonte consistente em todo o IDE.

- **Editor de texto** — elementos que surgem em código e outros editores baseados em texto podem ser personalizados na página Editor de texto em **Ferramentas > Opções**.

- **Coleções específicas** — janelas de designer que oferecem personalização do usuário de seus elementos de interface podem expor fontes específicas à sua superfície de design em sua própria página de configurações em **Ferramentas > Opções**.

### <a name="editor-font-customization-and-resizing"></a>Personalização e redimensionamento da fonte do editor
 Os usuários muitas vezes aumentarão ou ampliarão o tamanho e/ou a cor do texto no editor de acordo com sua preferência, independente da interface geral do usuário. Como a fonte do ambiente é usada em elementos que podem aparecer dentro ou como parte de um editor/designer, é importante observar o comportamento esperado quando uma dessas classificações de fonte é alterada.

 Ao criar elementos de IU que aparecem no editor, mas não fazem parte do *conteúdo,* é importante usar a fonte do ambiente e não a fonte de texto para que os elementos redimensionem de forma previsível.

1. Para texto de código no editor, redimensione com a configuração da fonte de texto do código e responda ao nível de zoom do texto do editor.

2. Todos os outros elementos da interface devem ser vinculados à configuração da fonte do ambiente e responder a quaisquer mudanças globais no ambiente. Isso inclui (mas não se limita a):

    - Texto em menus de contexto

    - Texto em um adorno de editor, como texto do menu da lâmpada, painel de editor de encontrar rápido e navegar para o painel

    - Rotular texto em caixas de diálogo, como Encontrar em Arquivos ou Refatorar

### <a name="accessing-the-environment-font"></a>Acessando a fonte do ambiente
 No código Nativo ou WinForms, a fonte do ambiente pode ser acessada chamando o método **IUIHostLocale::GetDialogFont** depois de consultar a interface do serviço SID_SUIHostLocale.

 Para o Windows Presentation Foundation (WPF), obtenha a classe de janela de diálogo da classe **DialogWindow** da shell em vez da classe **Janela** do WPF.

 Em XAML, o código se parece com isso:

```
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>

code behind:

internal partial class WebConfigModificationWindow : DialogWindow
{
}

```

 (Substitua pela `Microsoft.VisualStudio.Shell.11.0` versão atual do dll.)

 Para exibir a caixa de diálogo, chame "**ShowModal()**" na classe sobre **ShowDialog().** **O ShowModal define** o estado modal correto na concha, garante que a caixa esteja centrada na janela dos pais e assim por diante.

 O código é o seguinte:

```
MyWindow window = new MyWindow();
window.ShowModal()

```

 **ShowModal** devolve um bool? (booleano anulado) com o **DialogResult**, que pode ser usado se necessário. O valor de retorno é verdadeiro se a caixa de diálogo foi fechada com **OK**.

 Se você precisar exibir algum WPF UI que não seja um diálogo e estiver hospedado em seu próprio **HwndSource**, como uma janela pop-up ou uma janela de criança WPF de uma janela de janela pai Win32/WinForms, você precisará definir o **FontFamily** e **fontSize** no elemento raiz do elemento WPF. (O shell define as propriedades na janela principal, mas elas não serão herdadas após um HWND). O shell fornece recursos aos quais as propriedades podem ser vinculadas, assim:

```
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />

```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>Referência de formatação (escala/negrito)
 Alguns diálogos exigem que um texto específico seja ousado ou um tamanho diferente da fonte do ambiente. Anteriormente, fontes maiores que a fonte do ambiente eram codificadas como "fonte de ambiente +2" ou similares. O uso dos trechos de código fornecidos suportará monitores de alto DPI e garantirá que o texto de exibição apareça sempre no tamanho e peso corretos (como Light ou Semilight).

> **Nota: Antes de aplicar a formatação, certifique-se de que está seguindo as orientações encontradas no [estilo Texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**

 Para dimensionar a fonte do ambiente, defina o estilo do TextBlock ou do Label conforme indicado. Cada um desses trechos de código, devidamente utilizados, gerará a fonte correta, incluindo as variações de tamanho e peso apropriadas.

 Onde "vsui" é uma referência ao namespace Microsoft.VisualStudio.Shell:

```
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"

```

#### <a name="375-environment-font--light"></a>Fonte de ambiente de 375% + Luz
 **Aparece como:** 34 pt Segoe UI Light

 **Use para:** (raro) iu de marca única, como na Página inicial

 **Código processual:** Quando "textBlock" é um TextBlock e "label" previamente definidos é um rótulo previamente definido.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);

```

 **XAML:** Defina o estilo do TextBlock ou do Label como mostrado.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>

```

#### <a name="310-environment-font--light"></a>Fonte de ambiente 310% + Luz
 **Aparece como:** 28 pt Segoe UI Light

 **Uso para:** grandes títulos de diálogo de assinatura, principal título em relatórios

 **Código processual:** Quando "textBlock" é um TextBlock e "label" previamente definidos é um rótulo previamente definido.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);

```

 **XAML:** Defina o estilo do TextBlock ou do Label como mostrado.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>

```

#### <a name="200-environment-font--semilight"></a>Fonte 200% ambiente + Semilight
 **Aparece como:** 18 pt Segoe UI Semilight

 **Uso para:** subtítulos, títulos em diálogos de pequeno e médio porte

 **Código processual:** Quando "textBlock" é um TextBlock e "label" previamente definidos é um rótulo previamente definido.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);

```

 **XAML:** Defina o estilo do TextBlock ou do Label como mostrado.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>

```

#### <a name="155-environment-font"></a>Fonte de ambiente de 155%
 **Aparece como:** 14 pt Segoe UI

 **Use para:** títulos de seção em documento bem ui ou relatórios

 **Código processual:** Quando "textBlock" é um TextBlock e "label" previamente definidos é um rótulo previamente definido.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);

```

 **XAML:** Defina o estilo do TextBlock ou do Label como mostrado.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>

```

#### <a name="133-environment-font"></a>Fonte de ambiente de 133%
 **Aparece como:** 12 pt Segoe UI

 **Use para:** subtítulos menores em diálogos de assinatura e bem documento UI

 **Código processual:** Quando "textBlock" é um TextBlock e "label" previamente definidos é um rótulo previamente definido.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);

```

 **XAML:** Defina o estilo do TextBlock ou do Label como mostrado.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>

```

#### <a name="122-environment-font"></a>Fonte de ambiente de 122%
 **Aparece como:** 11 pt Segoe UI

 **Uso para:** títulos de seção em diálogos de assinatura, nó superior na exibição da árvore, navegação vertical de guias

 **Código processual:** Quando "textBlock" é um TextBlock e "label" previamente definidos é um rótulo previamente definido.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);

```

 **XAML:** Defina o estilo do TextBlock ou do Label como mostrado.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>

```

#### <a name="environment-font--bold"></a>Fonte do ambiente + negrito
 **Aparece como:** negrito 9 pt Segoe UI

 **Use para:** rótulos e sub-cabeças em diálogos de assinatura, relatórios e bem uI documente

 **Código processual:** Quando "textBlock" é um TextBlock e "label" previamente definidos é um rótulo previamente definido.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);

```

 **XAML:** Defina o estilo do TextBlock ou do Label como mostrado.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>

```

### <a name="localizable-styles"></a>Estilos localizáveis
 Em alguns casos, os localizadores precisarão modificar estilos de fonte para diferentes locais, como remover ousadia de texto para línguas do leste asiático. Para tornar possível a localização dos estilos de fonte, esses estilos devem estar dentro do arquivo .resx. A melhor maneira de realizar isso e ainda editar estilos de fonte no designer de formulários do Visual Studio é definir explicitamente os estilos de fonte na hora do design. Embora isso crie um objeto de fonte completo e possa parecer quebrar a herança das fontes-mãe, apenas a propriedade FontStyle é usada para definir a fonte.

 A solução é conectar o evento **FontChanged** do formulário de diálogo. No evento **FontChanged,** caminhe todos os controles e verifique se a fonte está definida. Se estiver definido, altere-o para uma nova fonte com base na fonte do formulário e no estilo de fonte anterior do controle. Um exemplo disso em código é:

```
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 O uso deste código garante que quando a fonte do formulário for atualizada, as fontes de controles também serão atualizadas. Esse método também deve ser chamado do construtor do formulário, porque a caixa de diálogo pode não conseguir uma instância do **IUIService** e o evento **FontChanged** nunca será acionado. O hooking **FontChanged** permitirá que os diálogos peguem dinamicamente a nova fonte mesmo que a caixa de diálogo já esteja aberta.

### <a name="testing-the-environment-font"></a>Testando a fonte do ambiente
 Para garantir que sua ui esteja usando a fonte do ambiente e respeite as configurações de tamanho, abra **as ferramentas > opções > ambiente > fontes e cores e** selecione "Fonte de ambiente" no menu suspenso "Mostrar configurações para:".

 ![Página Fontes e Cores na caixa de diálogo Ferramentas &#62; Opções](../../extensibility/ux-guidelines/media/0201-a-optionsfonts.png "0201-a_OptionsFonts")

 **Configurações de fontes e cores na caixa de diálogo Ferramentas > Opções**

 Defina a fonte como algo muito diferente do padrão. Para deixar claro que a ui não atualiza, escolha uma fonte com serifs (como "Times New Roman") e defina um tamanho muito grande. Em seguida, teste sua iu de iu a ida e para garantir que ela respeite o ambiente. Aqui está um exemplo usando a caixa de diálogo de licença:

 ![Exemplo de diálogo que não usa a fonte do ambiente](../../extensibility/ux-guidelines/media/0201-b-wrongfontdialog.png "0201-b_WrongFontDialog")

 **Exemplo de texto de IU que não respeita a fonte do ambiente**

 Neste caso, "Informações do Usuário" e "Informações do Produto" não estão respeitando a fonte. Em alguns casos, isso pode ser uma escolha explícita de design, mas pode ser um bug se a fonte explícita não for especificada como parte das especificações da linha vermelha.

 Para redefinir a fonte, clique em "Usar Padrões" em **Ferramentas > Opções > Ambiente > Fontes e Cores**.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a>Estilo de texto
 O estilo de texto refere-se ao tamanho da fonte, peso e invólucro. Para obter orientação de implementação, consulte [A fonte do ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Invólucro de texto

#### <a name="all-caps"></a>Todo em maiúsculas
 Não use todas as tampas para títulos ou rótulos no Visual Studio.

#### <a name="all-lowercase"></a>Todas as minúsculas
 Não use todas as minúsculas para títulos ou rótulos no Visual Studio.

#### <a name="sentence-and-title-case"></a>Sentença e caso de título
 O texto no Visual Studio deve usar o caso do título ou do caso da sentença, dependendo da situação.

|Use o case de título para:|Use o caso da sentença para:|
|-------------------------|----------------------------|
|Títulos de diálogo|Rótulos|
|Caixas de grupo|Caixas de seleção|
|Itens de menu|Botões de opção|
|Itens de menu de contexto|Listar itens da caixa|
|Botões|Barras de status|
|Rótulos de mesa||
|Cabeçalhos da coluna||
|Dicas de Ferramenta||

##### <a name="title-case"></a>Capitalização de título
 Case de título é um estilo no qual as primeiras letras da maioria ou de todas as palavras dentro de uma frase são capitalizadas. No Visual Studio, o case de título é usado para muitos itens, incluindo:

- **Dicas.** Exemplo: "Visualizar itens selecionados"

- **Cabeçalhos de coluna.** Exemplo: "Resposta ao sistema"

- **Itens do menu.** Exemplo: "Salvar tudo"

  Ao usar o caso do título, estas são as diretrizes para quando capitalizar palavras e quando deixá-las em minúsculas:

|Letras Maiúsculas|Comentários e exemplos|
|---------------|---------------------------|
|Todos os nomes||
|Todos os verbos|Incluindo "É" e outras formas de "ser"|
|Todos os advébis|Incluindo "Than" e "When"|
|Todos os adjetivos|Incluindo "Isso" e "Aquilo"|
|Todos os pronomes|Incluindo o possessivo "Its" bem como "It's", uma contração do pronome "it" e o verbo "é"|
|Primeira e última sapateada, independentemente das partes da fala||
|Preposições que fazem parte de uma frase verbo|"Fechando todas as Janelas" ou "Desligando o Sistema"|
|Todas as letras de um acrônimo|HTML, XML, URL, IDE, RGB|
|A segunda palavra em uma palavra composta se é um nome ou adjetivo adequado, ou se as palavras têm o mesmo peso|Cross-Reference, software pré-Microsoft, acesso a leitura/gravação, tempo de execução|

|Letras minúsculas|Exemplos|
|---------------|--------------|
|A segunda palavra em uma palavra composta se for outra parte da fala ou um particípio modificando a primeira palavra|Como fazer, Decolagem|
|Artigos, a menos que seja a primeira palavra no título|um, uma, o, a|
|Coordenar conjunções|e, mas, para, nem, ou|
|Preposições com palavras de quatro ou menos letras fora de uma frase verbo|em, para, como para, fora, em cima de|
|"Para" quando usado em uma frase infinitiva|"Como formatar seu disco rígido"|

##### <a name="sentence-case"></a>Caso da sentença
 O caso da sentença é o método padrão de capitalização para escrever em que apenas a primeira palavra da sentença é capitalizada, juntamente com quaisquer nomes próprios e o pronome "I". Em geral, o caso de sentença é mais fácil para um público mundial ler, especialmente quando o conteúdo será traduzido por uma máquina. Use o caso da sentença para:

1. **Mensagens de barra de status.** Estes são simples, curtos e fornecem apenas informações de status. Exemplo: "Arquivo de projeto de carregamento"

2. **Todos os outros elementos de IA**, incluindo etiquetas, caixas de seleção, botões de rádio e itens de caixa de lista. Exemplo: "Selecione todos os itens da lista"

### <a name="text-formatting"></a>Formatação de texto
 A formatação de texto padrão no Visual Studio 2013 é controlada por uma [fonte de ambiente .](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont) Este serviço ajuda a garantir uma aparência de fonte consistente em todo o IDE (ambiente de desenvolvimento integrado), e você deve usá-lo para garantir uma experiência consistente para seus usuários.

 O tamanho padrão usado pelo serviço de fonte Visual Studio vem do Windows e aparece como 9 pt.

 Você pode aplicar a formatação na fonte do ambiente. Este tópico abrange como e onde usar estilos. Para obter informações sobre a implementação, consulte [A fonte do ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Texto em negrito
 O texto em negrito é usado com moderação no Visual Studio e deve ser reservado para:

- rótulos de questão em assistentes

- designação do projeto ativo no Solution Explorer

- valores substituídos na janela de ferramentas Propriedades

- certos eventos nas listas de seleção do editor Visual Basic

- conteúdo gerado por servidor no esboço do documento para páginas da Web

- cabeçalhos de seção em diálogo complexo ou ui designer

#### <a name="italics"></a>Itálico
 O Visual Studio não usa texto itálico ou em negrito.

#### <a name="color"></a>Color

- O azul é reservado para hiperlinks (navegação e comando) e nunca deve ser usado para orientação.

- Títulos maiores (fonte de ambiente x 155% ou mais) podem ser coloridos para esses fins:

  - Para fornecer apelo visual à assinatura do Visual Studio UI

  - Para chamar a atenção para uma área específica

  - Para oferecer alívio da cor de texto padrão do ambiente cinza escuro/preto

- A cor nos títulos deve aproveitar as cores existentes da marca Visual Studio, principalmente o roxo principal, #FF68217A.

- Ao usar cores em títulos, você deve seguir as [diretrizes de cor](https://msdn.microsoft.com/library/dn742482.aspx)do Windows, incluindo a razão de contraste e outras considerações de acessibilidade.

### <a name="font-size"></a>Tamanho da fonte
 Visual Studio UI design apresenta uma aparência mais leve com mais espaço em branco. Sempre que possível, as barras cromadas e de título foram reduzidas ou removidas. Embora a densidade de informações seja um requisito no Visual Studio, a tipografia continua sendo importante, com ênfase em espaçamento de linha mais aberta e uma variação de tamanhos e pesos de fontes.

 As tabelas abaixo incluem detalhes de design e exemplos visuais para as fontes de exibição usadas no Visual Studio. Algumas variações de fonte de exibição têm tanto o tamanho quanto o peso, como Semilight ou Light, codificados em sua aparência.

 Os trechos de código de implementação para todas as fontes de exibição podem ser encontrados na [referência Formatação (escala/negrito).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)

#### <a name="375-environment-font--light"></a>Fonte de ambiente de 375% + Luz

|||
|-|-|
|**Uso:** Raro. Somente a UI de marca única.<br /><br /> **Faça:**<br /><br /> - Use o caso da sentença<br />- Use sempre peso leve<br /><br /> **Não:**<br /><br /> - Use para iu diferente de iu assinatura, como Página inicial<br />- Negrito, itálico ou negrito itálico<br />- Uso para texto corporal<br />- Uso em janelas de ferramentas|**Aparece como:** 34 pt Segoe UI Light<br /><br /> **Exemplo visual:**<br /><br /> *Atualmente não usado. Pode ser usado na Página inicial.*|

#### <a name="310-environment-font--light"></a>Fonte de ambiente 310% + Luz

|||
|-|-|
|**Uso:**<br /><br /> - Título maior em diálogos de assinatura<br />- Título principal do relatório<br /><br /> **Faça:**<br /><br /> - Use o caso da sentença<br />- Use sempre peso leve<br /><br /> **Não:**<br /><br /> - Use para iu diferente de iu assinatura, como Página inicial<br />- Negrito, itálico ou negrito itálico<br />- Uso para texto corporal<br />- Uso em janelas de ferramentas|**Aparece como:** 28 pt Segoe UI Light<br /><br /> **Exemplo visual:**<br /><br /> ![Exemplo de 310% fonte de ambiente &#43; título Light](../../extensibility/ux-guidelines/media/0202-a-ef310.png "0202-a_EF310")|

#### <a name="200-environment-font--semilight"></a>Fonte 200% ambiente + Semilight

|||
|-|-|
|**Uso:**<br /><br /> - Subtítulos<br />- Títulos em diálogos de pequeno e médio porte<br /><br /> **Faça:**<br /><br /> - Use o caso da sentença<br />- Use sempre peso semileve<br /><br /> **Não:**<br /><br /> - Negrito, itálico ou negrito itálico<br />- Uso para texto corporal<br />- Uso em janelas de ferramentas|**Aparece como:** 18 pt Segoe UI Semillight<br /><br /> **Exemplo visual:**<br /><br /> ![Exemplo de fonte 200% Ambiente &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b-ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>Fonte de ambiente de 155%

|||
|-|-|
|**Uso:**<br /><br /> - Títulos de seção no documento bem UI<br />- Relatórios<br /><br /> **Faça:** Use o caso da sentença<br /><br /> **Não:**<br /><br /> - Negrito, itálico ou negrito itálico<br />- Uso para texto corporal<br />- Use em controles padrão do Visual Studio<br />- Uso em janelas de ferramentas|**Aparece como:** 14 pt Segoe UI<br /><br /> **Exemplo visual:**<br /><br /> ![Exemplo de 155% posição de fonte de ambiente](../../extensibility/ux-guidelines/media/0202-c-ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>Fonte de ambiente de 133%

|||
|-|-|
|**Uso:**<br /><br /> - Subtítulos menores em diálogos de assinatura<br />- Subtítulos menores no documento bem UI<br /><br /> **Faça:** Use o caso da sentença<br /><br /> **Não:**<br /><br /> - Negrito, itálico ou negrito itálico<br />- Uso para texto corporal<br />- Use em controles padrão do Visual Studio<br />- Uso em janelas de ferramentas|**Aparece como:** 12 pt Segoe UI<br /><br /> **Exemplo visual:**<br /><br /> ![Exemplo de 133% posição de fonte de ambiente](../../extensibility/ux-guidelines/media/0202-d-ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>Fonte de ambiente de 122%

|||
|-|-|
|**Uso:**<br /><br /> - Títulos de seção em diálogos de assinatura<br />- Nó superior na vista da árvore<br />- Navegação vertical de guias<br /><br /> **Faça:** Use o caso da sentença<br /><br /> **Não:**<br /><br /> - Negrito, itálico ou negrito itálico<br />- Uso para texto corporal<br />- Use em controles padrão do Visual Studio<br />- Uso em janelas de ferramentas|**Aparece como:** 11 pt Segoe UI<br /><br /> **Exemplo visual:**<br /><br /> ![Exemplo de 122% posição de fonte de ambiente](../../extensibility/ux-guidelines/media/0202-e-ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Fonte do ambiente + negrito

|||
|-|-|
|**Uso:**<br /><br /> - Rótulos e sub-cabeças em diálogos de assinatura<br />- Rótulos e sub-cabeças em relatórios<br />- Rótulos e sub-cabeças no documento bem UI<br /><br /> **Faça:**<br /><br /> - Use o caso da sentença<br />- Use peso ousado<br /><br /> **Não:**<br /><br /> - Itálico ou negrito itálico<br />- Uso para texto corporal<br />- Use em controles padrão do Visual Studio<br />- Uso em janelas de ferramentas|**Aparece como:** negrito 9 pt Segoe UI<br /><br /> **Exemplo visual:**<br /><br /> ![Exemplo de fonte de ambiente &#43; título em negrito](../../extensibility/ux-guidelines/media/0202-f-efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Fonte do ambiente

|||
|-|-|
|**Uso:** Todos os outros textos<br /><br /> **Faça:** Use o caso da sentença<br /><br /> **Não:** Itálico ou negrito itálico|**Aparece como:** 9 pt Segoe UI<br /><br /> **Exemplo visual:**<br /><br /> ![Exemplo de fonte de ambiente](../../extensibility/ux-guidelines/media/0202-g-ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Enchimento e espaçamento
 Os títulos requerem espaço ao seu redor para dar-lhes a ênfase apropriada. Este espaço varia dependendo do tamanho do ponto e do que mais está perto da posição, como uma regra horizontal ou uma linha de texto na fonte do ambiente.

- O preenchimento ideal para uma posição por si só deve ser 90% do espaço de altura do personagem capital. Por exemplo, uma posição Segoe UI Light de 28 pts tem uma altura de tampa de 26 pt, e o preenchimento deve ser de aproximadamente 23 pt, ou cerca de 31 pixels.

- O espaço mínimo em torno de uma posição deve ser de 50% da altura do personagem capital. Menos espaço pode ser usado quando uma posição é acompanhada por uma regra ou outro elemento de encaixe apertado.

- O texto da fonte do ambiente em negrito deve seguir o espaçamento e o preenchimento da altura da linha padrão.

## <a name="see-also"></a>Consulte Também
 [MSDN: Fontes (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742483\(v=vs.85\).aspx) [MSDN: Texto de Interface do Usuário (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)
