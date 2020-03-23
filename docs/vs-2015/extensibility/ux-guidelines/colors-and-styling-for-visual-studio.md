---
title: Cores e estilos
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0330ef80fc1127893590ef8d326cb5b8e0cf0160
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302437"
---
# <a name="colors-and-styling-for-visual-studio"></a>Cores e estilo para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="using-color-in-visual-studio"></a>Usando cor no Visual Studio
 No Visual Studio, a cor é usada principalmente como uma ferramenta de comunicação, não apenas como decoração. Use a cor minimamente e reserve-a para situações em que você deseja:

- Comunicar significado ou afiliação (por exemplo, modificadores de plataforma ou idioma)

- Atrair atenção (por exemplo, indicando uma mudança de status)

- Melhore a legibilidade e forneça pontos turísticos para navegar na UI

- Aumentar a desejabilidade

  Existem várias opções para atribuir cores a elementos de IA no Visual Studio. Às vezes pode ser difícil descobrir qual opção você deve usar, ou como usá-la corretamente. Este tópico irá ajudá-lo:

1. Entenda os diferentes serviços e sistemas utilizados para definir cores no Visual Studio.

2. Selecione a opção correta para um determinado elemento.

3. Use corretamente a opção escolhida.

   **IMPORTANTE:** Nunca code hex, RGB ou cores do sistema para seus elementos de IA. O uso dos serviços permite flexibilidade na tonalidade de ajuste. Além disso, sem o serviço, você não poderá aproveitar os recursos de comutação de tema do [Serviço VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Métodos para atribuir cor aos elementos de interface do Visual Studio
 Escolha o método mais adequado aos seus elementos de IA.

|Sua ui|Método|O que é que eles são?|
|-------------|------------|--------------------|
|Você tem caixas de diálogo incorporadas ou autônomas.|**Cores do sistema**|Nomes do sistema que permitem que o sistema operacional defina a cor e a aparência dos elementos da IU, como para controles comuns de diálogo.|
|Você tem uma ia de uso personalizada que deseja ser consistente com o ambiente VS global e você tem elementos de IU que correspondem à categoria e ao significado semântico dos tokens compartilhados.|**Cores compartilhadas comuns**|Nomes de token de cor predefinidos existentes para elementos específicos de IU|
|Você tem um recurso individual ou um grupo de recursos e não há cor compartilhada para elementos semelhantes.|**Cores personalizadas**|Nomes de token de cor que são específicos para uma área e não devem ser compartilhados com outras ui|
|Você deseja permitir que o usuário final personalize a ui ou conteúdo (por exemplo, para editores de texto ou janelas de designer especializadas).|**Personalização do usuário final**<br /><br /> **(Diálogo ferramentas > opções)**|Configurações definidas na página "Fontes e cores" da caixa de diálogo **Ferramentas > Opções** ou uma página especializada específica para um recurso de IA.|

### <a name="visual-studio-themes"></a>Temas do Visual Studio
 O Visual Studio apresenta três temas de cores diferentes: claro, escuro e azul. Ele também detecta o modo High Contrast, que é um tema de cores em todo o sistema projetado para acessibilidade.

 Os usuários são solicitados a selecionar um tema durante o primeiro uso do Visual Studio e são capazes de mudar de temas mais tarde indo para **Ferramentas > Opções > Ambiente > Geral** e escolhendo um novo tema no menu suspenso "tema de cor".

 Os usuários também podem usar o Painel de Controle para mudar seus sistemas inteiros em um dos vários temas do Alto Contraste. Se um usuário selecionar um tema de Alto Contraste, o seletor de cores do Visual Studio não afetará mais as cores no Visual Studio, embora quaisquer alterações de tema sejam salvas para quando o usuário sair do modo High Contrast. Para obter mais informações sobre o modo High Contrast, consulte [Escolhendo cores de alto contraste](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>O serviço VSColor
 O Visual Studio oferece um serviço de cores de ambiente, conhecido como serviço VSColor, que permite vincular os valores de cor de seus elementos de IU a uma entrada nomeada contendo valores de cor para cada tema do Visual Studio. Isso garante que suas cores serão automaticamente mudadas para refletir o tema ou o modo de alto contraste selecionado pelo usuário atual. O uso do serviço significa que a implementação de todas as alterações de cor relacionadas ao tema é tratada em um só lugar, e se você estiver usando cores compartilhadas comuns do serviço, sua iu refletirá automaticamente novos temas em versões futuras do Visual Studio.

### <a name="implementation"></a>Implementação
 O código-fonte do Visual Studio inclui vários arquivos de definição de pacoteque contêm listas de nomes de tokens e os respectivos valores de cor para cada tema. O serviço de cores lê as CORES definidas nestes arquivos de definição de pacote. Essas cores são referenciadas na marcação XAML ou em código e, em seguida, carregadas através do método **IVsUIShell5.GetThemedColor** ou um mapeamento DynamicResource.

### <a name="system-colors"></a>Cores do sistema
 Controles comuns fazem referência às cores do sistema por padrão. Se você quiser que sua ia usar cores do sistema, como quando você está criando um diálogo incorporado ou autônomo, você não precisa fazer nada.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Cores compartilhadas comuns no serviço VSColor
 Seus elementos de interface devem refletir o ambiente geral do Visual Studio. Ao reutilizar as cores compartilhadas comuns que são apropriadas para o componente de interface de interface que você está projetando, você garante que sua interface é consistente com outras interfaces do Visual Studio e que suas cores serão atualizadas automaticamente quando os temas forem adicionados ou atualizados.

 Antes de usar cores comuns compartilhadas, certifique-se de que você entenda como usá-las corretamente. O uso incorreto de cores compartilhadas comuns pode resultar em uma experiência inconsistente, frustrante ou confusa para seus usuários.

### <a name="user-customizable-colors"></a>Cores personalizáveis do usuário
 Veja: [Expondo cores para usuários finais](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

 Às vezes, você vai querer permitir que o usuário final personalize sua iu de usuário, como quando você está criando um editor de código ou superfície de design. Os componentes de IU personalizáveis são encontrados na seção **Fontes e Cores** da caixa de diálogo Ferramentas > **Opções,** onde os usuários podem optar por alterar a cor do primeiro plano, a cor do plano de fundo ou ambos.

 ![Ferramentas &#62; diálogo opções no Visual Studio](../../extensibility/ux-guidelines/media/0301-a-toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")

 **Diálogo ferramentas>opções**

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>O serviço VSColor
 O Visual Studio oferece um serviço de cores de ambiente, também chamado de serviço VSColor ou serviço de cores shell. Este serviço permite vincular os valores de cor de seus elementos de IU a um conjunto de cores de valor de nome contendo cores para cada tema. O serviço VSColor deve ser usado para todos os elementos de IA, de modo que as cores mudem automaticamente para refletir o tema selecionado pelo usuário atual, e para que a UI vinculada ao serviço de cores do ambiente se integre com novos temas em versões futuras do Visual Studio.

### <a name="how-the-service-works"></a>Como funciona o serviço
 O serviço de cores do ambiente lê VSCores definidas no .pkgdef para o componente UI. Esses VSColors são então referenciados em marcação ou código XAML e são carregados através do **IVsUIShell5.GetThemedColor** ou de um mapeamento DynamicResource.

 ![Arquitetura de serviço de cores do ambiente](../../extensibility/ux-guidelines/media/0302-a-environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")

 **Arquitetura de serviço de cores do ambiente**

### <a name="accessing-the-service"></a>Acessando o serviço
 Existem várias maneiras diferentes de acessar o serviço VSColor, dependendo do tipo de tokens de cor que você está usando e que tipo de código você tem.

#### <a name="predefined-environment-colors"></a>Cores do ambiente predefinidas

##### <a name="from-native-code"></a>Do código nativo
 O shell fornece um serviço que dá acesso ao COLORREF das cores. O serviço/interface é:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

 No arquivo VSShell80.idl, a **enumeração __VSSYSCOLOREX** tem constantes de cor shell. Para usá-lo, passe como o valor do índice um dos valores do enum __VSSYSCOLOREX documentado no MSDN ou um número de índice regular que a API do sistema Windows, **GetSysColor,** aceita. Fazendo isso, obtém de volta o valor RGB da cor que deve ser usada no segundo parâmetro.

 Se armazenar uma caneta ou pincel com uma nova cor, você deve aconselhar BroadcastMessages (fora do shell do Visual Studio) e ouvir WM_SYSCOLORCHANGE e WM_THEMECHANGED mensagens.

```
// To access the color service in native code, you'll make a call that resembles this:
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);

```

 **NOTA:** Os valores COLORREF retornados por **GetVSSysColorEx()** contêm apenas componentes R,G,B de uma cor temática. Se uma entrada de tema usar transparência, o valor do canal alfa será descartado antes de retornar. Portanto, se a cor do ambiente de interesse precisa ser usada em um lugar onde o canal de transparência é importante, você deve usar IVsUIShell5.GetThemedColor em vez de IVsUIShell2::GetVSSysColorEx, como descrito posteriormente neste tópico.

##### <a name="from-managed-code"></a>Do código gerenciado
 Acessar o serviço VSColor através de código nativo é bastante simples. Se você está trabalhando através de código gerenciado, no entanto, determinar como usar o serviço pode ser complicado. Com isso em mente, aqui está um trecho de código C# demonstrando este processo:

```
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

 Se você estiver trabalhando no Visual Basic, use:

```
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Da WPF UI
 Você pode vincular-se às cores do Visual Studio através de valores exportados para o Dicionário de Recursos do aplicativo. Abaixo está um exemplo de uso de recursos da tabela de cores, bem como vinculação aos dados da fonte do ambiente em XAML.

```
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>Aulas de ajudante e métodos para código gerenciado
 Para código gerenciado, a biblioteca Managed Package Framework da Shell (Microsoft.VisualStudio.Shell.12.0.dll) contém algumas classes de ajudantes facilitando o uso de cores temáticas.

 Os métodos auxiliares na classe **Microsoft.VisualStudio.Shell.VsColors** no MPF incluem **GetThemedGDIColor()** e **GetThemedWPFColor()**. Esses métodos auxiliares retornam o valor de cor de uma entrada temática como System.Drawing.Color ou System.Windows.Media.Color, a ser usado em WinForms ou WPF UI.

```
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

```

 A classe também pode ser usada para obter identificadores VSCOLOR para uma determinada chave de recurso de cor WPF, ou vice-versa.

```
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

 Os métodos da classe **VsColors** consultam o serviço VSColor para retornar o valor de cor cada vez que forem invocados. Para obter um valor de cor como **System.Drawing.Color**, uma alternativa com melhor desempenho é usar os métodos da classe **Microsoft.VisualStudio.PlatformUI.VSThemeColor,** que armazena os valores de cor obtidos no serviço VSColor. A classe se inscreve internamente em eventos de mensagens de difusão de shell e descarta o valor armazenado em cache quando ocorre um evento de alteração de tema. Além disso, a classe fornece um . Evento amigável da NET para assinar mudanças temáticas. Use o evento **ThemeChanged** para adicionar um novo manipulador e use o método **GetThemedColor()** para obter valores de cor para as Teclas de interesse **ThemeResourceKeys.** Um código de amostra pode ser assim:

```
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>Escolhendo cores de alto contraste

### <a name="overview"></a>Visão geral
 O Windows usa vários temas de alto contraste no nível do sistema que aumentam o contraste de cores de texto, fundos e imagens, fazendo com que os elementos pareçam mais distintos na tela. Por razões de acessibilidade, é importante que os elementos de interface do Visual Studio respondam corretamente quando os usuários mudam para um tema de Alto Contraste.

 Apenas um punhado de cores do sistema pode ser usado para temas de Alto Contraste. Ao escolher os nomes de cores do sistema, lembre-se das seguintes dicas:

1. **Escolha cores do sistema que tenham o mesmo significado semântico** que o elemento que você está colorindo. Por exemplo, se você estiver escolhendo uma cor de alto contraste para texto dentro de uma janela, use WindowText e não ControlText.

2. **Escolha os pares de primeiro plano/fundo** juntos ou você não estará confiante de que sua escolha de cor funcionará em todos os temas do Alto Contraste.

3. **Determine quais partes da sua iu de ida e garanta que as áreas de conteúdo se destaquem.** Você perderá muitos detalhes que diferenças sutis na tonalidade de cor normalmente distinguem, de modo que o uso de cores de borda fortes é comum para definir áreas de conteúdo, pois não há variantes de cor para diferentes áreas de conteúdo.

### <a name="system-color-set"></a>Conjunto de cores do sistema
 A tabela no [WPF Team Blog: SystemColors Reference](https://devblogs.microsoft.com/wpf/systemcolors-reference/) indica o conjunto completo de nomes de cores do sistema e as tonalidades correspondentes exibidas em cada tema.

 Ao aplicar este conjunto limitado de cores à sua ia, *espera-se que você perca detalhes sutis que estavam presentes nos temas "normais".* Aqui está um exemplo de UI com cores cinzentas sutis que são usadas para distinguir áreas dentro de uma janela de ferramenta. Quando emparelhado com a mesma janela exibida no modo High Contrast, você pode ver que todos os fundos são da mesma tonalidade e as bordas dessas áreas são indicadas apenas pela borda:

 ![Janela Propriedades](../../extensibility/ux-guidelines/media/030303-a-propertieswindow.png "030303-a_PropertiesWindow")

 **Exemplo de como detalhes sutis são perdidos quando em Alto Contraste**

#### <a name="choosing-text-colors-in-an-editor"></a>Escolhendo cores de texto em um editor
 O texto colorido é usado em um editor ou em uma superfície de design para indicar significado, como permitir a identificação fácil de grupos de itens semelhantes. Em um tema de Alto Contraste, no entanto, você não tem a capacidade de diferenciar entre mais de três cores de texto. WindowText, GrayText e HotTrackText são as únicas cores disponíveis nas superfícies do WindowBackground. Uma vez que você não pode usar mais de três cores, escolha cuidadosamente as diferenças mais importantes que você deseja exibir quando estiver no modo High Contrast.

 Matizes para cada um dos nomes de token permitidos em uma superfície de editor, como eles aparecem em cada tema de Alto Contraste:

 ![Comparação com editor de alto contraste](../../extensibility/ux-guidelines/media/030303-b-hceditorcomparison.png "030303-b_HCEditorComparison")

 **Comparação com editor de alto contraste**

 Exemplos da superfície do editor no tema Azul:

 ![Editor em Tema Azul](../../extensibility/ux-guidelines/media/030303-c-editorblue.png "030303-c_EditorBlue")

 **Editor em Tema Azul**

 ![Editor em tema de Alto Contraste](../../extensibility/ux-guidelines/media/030303-d-editorhc1.png "030303-d_EditorHC1")

 **Editor em Alto Contraste #1 tema**

### <a name="usage-patterns"></a>Padrões de uso
 Muitos elementos comuns da UI já têm cores de alto contraste definidas. Você pode referenciar esses padrões de uso ao escolher os nomes de cores do seu próprio sistema, de modo que seus elementos de ida e volta sejam consistentes com componentes semelhantes.

|Cor do sistema|Uso|
|------------------|-----------|
|Activecaption|- IDE ativo e glifos de botão de janela rafted em pairar e pressionar<br />- Fundo da barra de título para IDE e janelas de rafted<br />- Fundo da barra de status padrão|
|Activecaptiontext|- IDE ativo e janelas de rafted para o primeiro plano da barra de títulos (texto e glifos)<br />- Fundo e borda dos botões de janela ativos em pairar e pressionar|
|Control|- Caixa de combo, lista de paradas e padrão de controle de pesquisa e desativação de fundo, incluindo botão de lista de parada<br />- Fundo do botão de destino de doca<br />- Fundo da barra de comando<br />- Fundo da janela da ferramenta|
|Controldark|- Fundo IDE<br />- Separadores de menu e barra de comando<br />- Fronteira da barra de comando<br />- Sombras do menu<br />- Padrão da guia da janela da ferramenta e borda e separador de hover<br />- Documente o fundo do botão de estouro do poço<br />- Borda do glifo alvo das docas|
|Controldarkdark|- Janela de guia de documento desfocada e selecionada|
|Controllight|- Borda de guia de ocultação automática<br />- Caixa de combo e borda da lista de paradas<br />- Fundo de destino do cadeado e fronteira|
|Controllightlight|- Fronteira provisória selecionada e focada|
|Controltext|- Caixa de combo e glifo da lista de gotas<br />- Texto de guia não selecionado da janela da ferramenta|
|Graytext|- Caixa de combo e lista de itens suspensos desativados borda, glifo suspenso, texto e texto do menu<br />- Texto de menu desativado<br />- Texto de cabeçalho de 'opções de pesquisa' de controle de pesquisa<br />- Separador da seção de controle de pesquisa|
|Realçar|- Todos os fundos e bordas de fundo e de fundo pressionados, exceto o fundo do botão de encaixe da caixa combo e a borda do botão de estouro do documento<br />- Fundos de itens selecionados|
|Highlighttext|- Todos os prefáisticos e pressionados (texto e glifos)<br />- Janela de ferramenta focada e controle da janela da guia de documento em primeiro plano<br />- Borda da barra da barra da barra da janela da janela da ferramenta focada<br />- Foco, guia provisória selecionada em primeiro plano<br />- Documente a borda do botão de transbordamento do poço no hover e pressione<br />- Borda do ícone selecionada|
|Hottrack|- Fundo de polegar de barra de rolagem e borda na prensa<br />- Glifo de seta de barra de rolagem na prensa|
|Inactivecaption|- IDE inativo e glifos de botão de janela rafted no pairar<br />- Fundo da barra de título para IDE e janelas de rafted<br />- Fundo de controle de pesquisa desativado|
|Inactivecaptiontext|- IDE inativo e barra de título de janelas de rafted em primeiro plano (texto e glifos)<br />- Fundo dos botões de janela inativos e borda no hover<br />- Fundo e borda do botão da janela da ferramenta desfocado<br />- Controle de busca desativado em primeiro plano|
|Menu|- Plano de fundo do menu suspenso<br />- Verificação e desativação do plano de fundo da marca de verificação|
|Menutext|- Borda do menu suspenso<br />- Verificação de marca de marca<br />- Glifos de menu<br />- Texto do menu suspenso<br />- Borda do ícone selecionada|
|Scrollbar|- Fundo de seta de scrollbar e scrollbar, todos os estados|
|Janela|- Ocultar automaticamente o plano de fundo da guia<br />- Barra de menu e fundo de prateleira de comando<br />- Fundo de guia de guia de documento não focado ou não selecionado e borda do documento, para guias abertas e provisórias<br />- Fundo da barra de título da janela da ferramenta desfocada<br />- Plano de fundo da guia da janela da ferramenta, selecionado e não selecionado|
|Windowframe|- Fronteira IDE|
|Windowtext|- Primeiro plano de guia de ocultação automática<br />- Primeiro plano da guia da janela da ferramenta selecionada<br />- Guia de janela de documento desfocada e primeiro plano de guia provisória desfocado ou não selecionado<br />- Visualização de árvore em primeiro plano padrão e pairar sobre o glifo não selecionado<br />- Janela de ferramenta selecionada borda de guia<br />- Fundo do polegar da barra de rolagem, borda e glifo|

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>Expondo cores para usuários finais

### <a name="overview"></a>Visão geral
 Às vezes, você vai querer permitir que o usuário final personalize sua iu de usuário, como quando você está criando um editor de código ou superfície de design. A maneira mais comum de fazer isso é usando o diálogo **Ferramentas > Opções.** A menos que você tenha uma iu altamente especializada que exija controles especiais, a maneira mais fácil de apresentar a personalização é através da página **Fontes e Cores** na seção **Ambiente** da caixa de diálogo. Para cada elemento que você expõe para personalização, o usuário pode optar por alterar a cor do primeiro plano, a cor do plano de fundo ou ambos.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Construindo um VSPackage para suas cores personalizáveis
 Um VSPackage pode controlar as fontes e cores através de categorias personalizadas e exibir itens na página de propriedade Fontes e Cores. Ao usar esse mecanismo, o VSPackages deve implementar a interface [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) e suas interfaces associadas.

 Em princípio, esse mecanismo pode ser usado para modificar todos os itens de exibição existentes e as categorias que os contêm. No entanto, ele não deve ser usado para modificar a categoria Editor de texto ou seus itens de exibição. Para obter mais informações sobre a categoria Editor de texto, consulte [Visão geral de fonte e cor](https://msdn.microsoft.com/library/bb165065.aspx).

 Para implementar categorias personalizadas ou exibir itens, um VSPackage deve:

- **Crie ou identifique categorias no registro.** A implementação do IDE da página de propriedade **Fontes e Cores** usa essas informações para consultar corretamente o serviço que suporta uma determinada categoria.

- **Criar ou identificar grupos no registro (opcional).** Pode ser útil definir um grupo, que representa a união de duas ou mais categorias. Se um grupo for definido, o IDE mescla automaticamente subcategorias e distribui itens de exibição dentro do grupo.

- **Implementar suporte iDE.**

- **Lidar com as alterações de fonte e cor.**

#### <a name="to-create-or-identify-categories"></a>Para criar ou identificar categorias
 Construa um tipo especial de registro de categoria em [HKLM\SOFTWARE\Microsoft \Visual\\ Studio<versão\>do Visual Studio \FontAndColors\\<Category\>]. \<Categoria> é o nome não localizado da Categoria.

 Preencha o registro com dois valores:

|Nome|Type|Dados|Descrição|
|----------|----------|----------|-----------------|
|Categoria|REG_SZ|GUID|Um GUID criado para identificar a categoria|
|Pacote|REG_SZ|GUID|O GUID do serviço VSPackage que suporta a categoria|

 O serviço especificado no registro deve fornecer uma implementação de [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) para a categoria correspondente.

#### <a name="to-create-or-identify-groups"></a>Para criar ou identificar grupos
 Construa um tipo especial de entrada de registro de categorias\\ em [HKLM\SOFTWARE\Microsoft \Visual Studio<versão\>do Visual Studio \FontAndColors\\<grupo\>]. \<grupo> é o nome não localizado do grupo.

 Preencha o registro com dois valores:

|Nome|Type|Dados|Descrição|
|----------|----------|----------|-----------------|
|Categoria|REG_SZ|GUID|Um GUID criado para identificar a categoria|
|Pacote|REG_SZ|GUID|O GUID do serviço VSPackage que suporta a categoria|

 O serviço especificado no registro deve fornecer uma implementação de **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** para o grupo correspondente.

 ![IVsfontandColorGroup](../../extensibility/ux-guidelines/media/0304-a-fontandcolorgroup.png "0304-a_FontAndColorGroup")

### <a name="to-implement-ide-support"></a>Para implementar o suporte ao IDE
 Implemente [getobject](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), que retorna uma interface [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) ou uma interface **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** para o IDE para cada categoria ou grupo GUID fornecido.

 Para cada categoria que ele suporta, um VSPackage implementa uma instância separada da interface [IVsFontAndColorDefaults.](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)

 Os métodos implementados através do [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) devem fornecer ao IDE:

- Listas de itens de exibição na categoria

- Nomes localizados para itens de exibição

- Exibir informações para cada membro da categoria

  **NOTA:** Cada categoria deve conter pelo menos um item de exibição.

  O IDE usa a interface **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** para definir uma união de várias categorias.

  Sua implementação fornece o IDE com:

- Uma lista das Categorias que compõem um determinado grupo

- Acesso a instâncias de [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) suportando cada categoria dentro do grupo

- Nomes de grupos localizados

#### <a name="updating-the-ide"></a>Atualizando o IDE
 O IDE armazena informações sobre configurações de Fonte e Cor. Portanto, após qualquer modificação da configuração de Fonte e Cor Do IDE, garantir que o cache esteja atualizado é uma prática recomendada.

 A atualização do cache é feita através da interface [IvsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) e pode ser realizada globalmente ou apenas em itens selecionados.

### <a name="handling-font-and-color-changes"></a>Manipulação de mudanças de fonte e cor
 Para suportar adequadamente a colorização do texto exibido por um VSPackage, o serviço de colorização que suporta o VSPackage deve responder às alterações iniciadas pelo usuário feitas através da página De propriedades Fontes e Cores.

 Para fazer isso, um VSPackage deve:

- **lidar com eventos gerados** pelo IDE implementando a interface [IVsFontAndColorEvents.](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) O IDE chama o método apropriado após modificações do usuário da página Fontes e Cores. Por exemplo, ele chama o método [OnFontChanged](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) se uma nova fonte for selecionada.

  **Ou**

- **enquete o IDE para mudanças**. Isso pode ser feito através da interface [IVsFontAndColorStorage,](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) implementada pelo sistema. Embora principalmente para suporte à persistência, o método [GetItem](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) pode obter informações de fonte e cores para itens de exibição. Para obter mais informações sobre as configurações de fonte e cor, consulte o artigo MSDN [acessando as configurações de fonte e cor armazenadas](https://msdn.microsoft.com/library/bb166382.aspx).

  **NOTA:** Para garantir que os resultados da votação estejam corretos, use a interface [IVsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) para determinar se um flush e atualização de cache são necessários antes de chamar os métodos de recuperação da interface [IVsFontAndColorStorage.](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx)

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrando a categoria de fonte e cor personalizada sem implementar interfaces
 O exemplo de código a seguir demonstra como registrar a categoria de fonte e cor personalizada sem implementar interfaces:

```xml
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

 **Nota:**

- "NameID" = o ID de recurso do nome da categoria localizada em seu pacote

- "ToolWindowPackage" = Guia do pacote

- "Categoria"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}" é apenas um exemplo e o valor real pode ser um novo GUID fornecido pelo implementador.

### <a name="set-the-font-and-color-property-category-guid"></a>Defina a categoria de propriedade Fonte e Cor GUID
 O exemplo de código abaixo demonstra a configuração de GUIDs de categoria.

```cs
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
  IVsTextEditorPropertyContainer spPropContainer;
  Guid GUID_EditPropCategory_View_MasterSettings =
  new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
  hr = spPropCatContainer.GetPropertyCategory(
  ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer);
  if(hr == 0)
  {
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID);
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID);
  }
}
```
