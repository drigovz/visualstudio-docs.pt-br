---
title: Serviço de Imagem e Catálogo | Microsoft Docs
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e1ccfad2a678656bcf09e37852532a8b28eb0e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710386"
---
# <a name="image-service-and-catalog"></a>Serviço de imagem e catálogo
Este livro de receitas contém orientações e práticas recomendadas para a adoção do Visual Studio Image Service and Image Catalog introduzido no Visual Studio 2015.

 O serviço de imagem introduzido no Visual Studio 2015 permite que os desenvolvedores obtenham as melhores imagens para o dispositivo e o tema escolhido pelo usuário para exibir a imagem, incluindo o tema correto para o contexto em que são exibidos. A adoção do serviço de imagem ajudará a eliminar os principais pontos de dor relacionados à manutenção de ativos, dimensionamento hdpi e tema.

|||
|-|-|
|**Problemas hoje**|**Soluções**|
|Mistura de cores de fundo|Mistura alfa incorporada|
|Temática (algumas) imagens|Metadados temáticos|
|Modo de alto contraste|Recursos alternativos de alto contraste|
|Precisa de vários recursos para diferentes modos de DPI|Recursos selecionáveis com recuo baseado em vetores|
|Imagens duplicadas|Um identificador por conceito de imagem|

 Por que adotar o serviço de imagem?

- Sempre obtenha a imagem mais recente "pixel-perfeito" do Visual Studio

- Você pode enviar e usar suas próprias imagens

- Não há necessidade de testar suas imagens quando o Windows adiciona novo dimensionamento de DPI

- Aborde antigos obstáculos arquitetônicos em suas implementações

  A barra de ferramentas shell do Visual Studio antes e depois de usar o serviço de imagem:

  ![Serviço de imagem antes e depois](../extensibility/media/image-service-before-and-after.png "Serviço de imagem antes e depois")

## <a name="how-it-works"></a>Como ele funciona
 O serviço de imagem pode fornecer uma imagem bitmapapped adequada para qualquer estrutura de ia de ia suportada:

- WPF: BitmapSource

- WinForms: System.Drawing.Bitmap

- Win32: HBITMAP

  Diagrama de fluxo de serviço de imagem

  ![Diagrama de fluxo de serviço de imagem](../extensibility/media/image-service-flow-diagram.png "Diagrama de fluxo de serviço de imagem")

  **Apelidos de imagem**

  Um apelido de imagem (ou apelido para abreviar) é um par GUID/ID que identifica exclusivamente um ativo de imagem ou lista de imagens na biblioteca de imagens.

  **Apelidos conhecidos**

  O conjunto de apelidos de imagem contidos no Catálogo de Imagens do Visual Studio e consumíveis publicamente por qualquer componente ou extensão do Visual Studio.

  **Arquivos manifestos de imagem**

  Manifesto de imagem *(.imagemanifest)* arquivos são arquivos XML que definem um conjunto de ativos de imagem, os apelidos que representam esses ativos e a imagem real ou imagens que representam cada ativo. Os manifestos de imagem podem definir imagens independentes ou listas de imagens para suporte à ui legado. Além disso, existem atributos que podem ser definidos no ativo ou nas imagens individuais por trás de cada ativo para mudar quando e como esses ativos são exibidos.

  **Esquema de manifesto de imagem**

  Um manifesto de imagem completo se parece com isso:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Import, Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Símbolos**

 Como um auxílio de legibilidade e manutenção, o manifesto de imagem pode usar símbolos para valores de atributo. Os símbolos são definidos assim:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Subelemento**|**Definição**|
|Importar|Importa os símbolos do arquivo manifesto dado para uso no manifesto atual|
|Guid|O símbolo representa um GUID e deve corresponder à formatação GUID|
|ID|O símbolo representa um ID e deve ser um inteiro não negativo|
|String|O símbolo representa um valor de corda arbitrário|

 Os símbolos são sensíveis a maiúsculas e outras referências usando a sintaxe de $(nome símbolo):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Alguns símbolos são predefinidos para todos os manifestos. Estes podem ser usados \<no atributo Uri do elemento> Fonte ou \<Importação> para referenciar caminhos na máquina local.

|||
|-|-|
|**Símbolo**|**Descrição**|
|CommonProgramFiles|O valor da variável ambiente %CommonProgramFiles%|
|LocalAppData|O valor da variável ambiente %LocalAppData%|
|Pasta de manifesto|A pasta contendo o arquivo manifesto|
|Mydocuments|O caminho completo da pasta Meus documentos do usuário atual|
|ProgramFiles|O valor da variável ambiente %ProgramFiles%|
|Sistema|A pasta *Windows\System32*|
|Windir|O valor da variável ambiente %WinDir%|

 **Imagem**

 O \<elemento Imagem> define uma imagem que pode ser referenciada por um apelido. O GUID e o ID juntos formam o apelido da imagem. O apelido para a imagem deve ser único em toda a biblioteca de imagens. Se mais de uma imagem tem um nome dado, a primeira encontrada durante a construção da biblioteca é a que é retida.

 Deve conter pelo menos uma fonte. Fontes neutras de tamanho darão os melhores resultados em uma ampla gama de tamanhos, mas eles não são necessários. Se o serviço for solicitado para uma imagem \<de um tamanho não definido no elemento Imagem> e não houver uma fonte neutra de tamanho, o serviço escolherá a melhor fonte específica de tamanho e dimensionará-a para o tamanho solicitado.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Atributo**|**Definição**|
|Guid|[Necessário] A parte GUID do apelido de imagem|
|ID|[Necessário] A parte de ID do apelido de imagem|
|Inversão de cores permitida|[Opcional, padrão verdadeiro] Indica se a imagem pode ter suas cores programáticamente invertidas quando usada em um fundo escuro.|

 **Fonte**

 O \<elemento Source> define um único recurso de fonte de imagem (XAML e PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Atributo**|**Definição**|
|Uri|[Necessário] Um URI que define de onde a imagem pode ser carregada. Pode ser um dos seguintes:<br /><br /> - Um [Pacote URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) usando a autoridade application:///<br />- Uma referência absoluta de recursos componentes<br />- Um caminho para um arquivo contendo um recurso nativo|
|Segundo plano|[Opcional] Indica o que em tipo de fundo a fonte deve ser usada.<br /><br /> Pode ser um dos seguintes:<br /><br /> *Luz:* A fonte pode ser usada em um fundo leve.<br /><br /> *Escuro:* A fonte pode ser usada em um fundo escuro.<br /><br /> *Alto contraste:* A fonte pode ser usada em qualquer plano de fundo no modo High Contrast.<br /><br /> *Luz de alto contraste:* A fonte pode ser usada em um fundo leve no modo High Contrast.<br /><br /> *HighContrastDark:* A fonte pode ser usada em um fundo escuro no modo High Contrast.<br /><br /> Se o atributo Fundo for omitido, a fonte poderá ser usada em qualquer plano de fundo.<br /><br /> Se O fundo é *claro,* *escuro,* *highcontrastlight*ou *highcontrastdark,* as cores da fonte nunca são invertidas. Se O Fundo de Fundo for omitido ou definido como *HighContrast,* a inversão das cores da fonte será controlada pelo atributo **AllowColorInversion** da imagem.|

Um \<elemento> Fonte pode ter exatamente um dos seguintes subelementos opcionais:

||||
|-|-|-|
|**Elemento**|**Atributos (todos necessários)**|**Definição**|
|\<tamanho>|Valor|A fonte será usada para imagens do tamanho dado (em unidades do dispositivo). A imagem será quadrada.|
|\<tamanho>|MinSize|A fonte será usada para imagens de MinSize a MaxSize (em unidades de dispositivos) inclusivamente. A imagem será quadrada.|
|\<Dimensões>|Largura, Altura|A fonte será usada para imagens da largura e altura dada (em unidades do dispositivo).|
|\<> dimensionrange|MinWidth, MinHeight,<br /><br /> Largura máxima, MaxHeight|A fonte será usada para imagens desde a largura/altura mínima até a largura/altura máxima (em unidades do dispositivo) inclusivamente.|

 Um \<elemento> fonte também \<pode ter um subelemento \<de> nativo opcional, que define uma fonte> que é carregada a partir de um conjunto nativo em vez de um conjunto gerenciado.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Atributo**|**Definição**|
|Type|[Necessário] O tipo de recurso nativo, xaml ou PNG|
|ID|[Necessário] A parte de ID inteiro do recurso nativo|

 **Imagelist**

 O \<elemento ImageList> define uma coleção de imagens que podem ser devolvidas em uma única tira. A tira é construída sob demanda, conforme necessário.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Atributo**|**Definição**|
|Guid|[Necessário] A parte GUID do apelido de imagem|
|ID|[Necessário] A parte de ID do apelido de imagem|
|Externo|[Opcional, padrão falso] Indica se o apelido da imagem faz referência a uma imagem no manifesto atual.|

 O apelido para a imagem contida não precisa fazer referência a uma imagem definida no manifesto atual. Se a imagem contida não puder ser encontrada na biblioteca de imagens, uma imagem de espaço reservado em branco será usada em seu lugar.

## <a name="using-the-image-service"></a>Usando o serviço de imagem

### <a name="first-steps-managed"></a>Primeiros passos (gerenciados)
 Para usar o serviço de imagem, você precisa adicionar referências a algumas ou todas as seguintes assembléias ao seu projeto:

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Necessário se você usar o catálogo de imagens incorporado **KnownMonikers**.

- *Microsoft.VisualStudio.Imaging.dll*

  - Necessário se você usar **CrispImage** e **ImageThemingUtilities** em sua UI WPF.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - Necessário se você usar os tipos **ImageMoniker** e **ImageAttributes.**

  - **EmbedInteropTypes** deve ser definido como verdadeiro.

- *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime*

  - Necessário se você usar o tipo **IVsImageService2.**

  - **EmbedInteropTypes** deve ser definido como verdadeiro.

- *Microsoft.VisualStudio.Utilities.dll*

  - Necessário se você usar o **BrushToColorConverter** para **o ImageThemingUtilities.ImageBackgroundColor** em sua UI WPF.

- *Microsoft.VisualStudio.shell. \<VSVersion>.0*

  - Necessário se você usar o tipo **IVsUIObject.**

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - Necessário se você usar os ajudantes de ia relacionados ao WinForms.

  - **EmbedInteropTypes** deve ser definido como verdadeiro

### <a name="first-steps-native"></a>Primeiros passos (nativo)
 Para usar o serviço de imagem, você precisa incluir alguns ou todos os seguintes cabeçalhos ao seu projeto:

- **KnownImageIds.h**

  - Necessário se você usar o catálogo de imagens incorporado **KnownMonikers,** mas não puder usar o tipo **ImageMoniker,** como ao retornar valores de chamadas **IVsHierarchy GetGuidProperty** ou **GetProperty.**

- **KnownMonikers.h**

  - Necessário se você usar o catálogo de imagens incorporado **KnownMonikers**.

- **Parâmetros de imagem140.h**

  - Necessário se você usar os tipos **ImageMoniker** e **ImageAttributes.**

- **VSShell140.h**

  - Necessário se você usar o tipo **IVsImageService2.**

- **ImageThemingUtilities.h**

  - Necessário se você não puder deixar o serviço de imagem lidar com o tema para você.

  - Não use este cabeçalho se o serviço de imagem puder lidar com o tema da imagem.

::: moniker range="vs-2017"
- **VSUIDPIHelper.h**

  - Necessário se você usar os ajudantes de DPI para obter o DPI atual.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - Necessário se você usar os ajudantes de conscientização do DPI para obter o DPI atual.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Como escrevo novas UI WPF?

1. Comece adicionando as referências de montagem necessárias na seção de primeiros passos acima ao seu projeto. Você não precisa adicionar todos eles, então adicione apenas as referências que você precisa. (Nota: se você estiver usando ou tiver acesso a **Cores** em vez de **Pincéis,** então você pode pular a referência aos **Utilitários,** já que você não precisará do conversor.)

2. Selecione a imagem desejada e obtenha seu apelido. Use um **KnownMoniker**ou use o seu próprio se você tiver suas próprias imagens e apelidos personalizados.

3. Adicione **CrispImages** ao seu XAML. (Veja abaixo o exemplo.)

4. Defina a **propriedade ImageThemingUtilities.ImageBackgroundColor** em sua hierarquia de IA. (Isso deve ser definido no local onde a cor de fundo é conhecida, não necessariamente no **CrispImage**.) (Veja abaixo o exemplo.)

```xaml
<Window
  x:Class="WpfApplication.MainWindow"
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">
  <Window.Resources>
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>
  </Window.Resources>
  <StackPanel Background="White" VerticalAlignment="Center"
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />
  </StackPanel>
</Window>
```

 **Como atualizo o WPF UI existente?**

 A atualização da UI WPF existente é um processo relativamente simples que consiste em três etapas básicas:

1. Substitua \<todos os elementos \<de> de imagem em sua interface do usuário por elementos> CrispImage.

2. Alterar todos os atributos de Origem para atributos De Moniker.

    - Se a imagem nunca mudar e você estiver usando **KnownMonikers,** então ligue estaticamente essa propriedade ao **KnownMoniker**. (Veja o exemplo acima.)

    - Se a imagem nunca mudar e você estiver usando sua própria imagem personalizada, então se vincule estáticamente ao seu próprio apelido.

    - Se a imagem puder mudar, vincule o atributo Moniker a uma propriedade de código que notifica as alterações de propriedade.

3. Em algum lugar da hierarquia de IA, defina **ImageThemingUtilities.ImageBackgroundColor** para garantir que a inversão de cores funcione corretamente.

    - Isso pode exigir o uso da classe **BrushToColorConverter.** (Veja o exemplo acima.)

## <a name="how-do-i-update-win32-ui"></a>Como atualizo a UI Win32?
 Adicione o seguinte ao seu código sempre que apropriado para substituir o carregamento bruto de imagens. Alterne os valores para o retorno de HBITMAPs versus HICONs versus HIMAGELIST conforme necessário.

 **Obter o serviço de imagem**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Solicitando a imagem**

::: moniker range="vs-2017"

```cpp
ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

::: moniker range=">=vs-2019"

```cpp
UINT dpiX, dpiY;
HWND hwnd = // get the HWND where the image will be displayed
VsUI::CDpiAwareness::GetDpiForWindow(hwnd, &dpiX, &dpiY);

ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = dpiX;
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

## <a name="how-do-i-update-winforms-ui"></a>Como atualizo o WinForms UI?
 Adicione o seguinte ao seu código sempre que apropriado para substituir o carregamento bruto de imagens. Alterne os valores para retornar Bitmaps versus Ícones conforme necessário.

 **Útil usando a declaração**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Obter o serviço de imagem**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Solicite a imagem**

::: moniker range="vs-2017"

```csharp
ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiHelper.DeviceDpiX;
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

::: moniker range=">=vs-2019"

```csharp
Control control = // get the control where the image will be displayed

ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiAwareness.GetWindowDpi(control.Handle);
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Como uso apelidos de imagem em uma nova janela de ferramentas?
 O modelo do projeto do pacote VSIX foi atualizado para o Visual Studio 2015. Para criar uma nova janela de ferramenta, clique com o botão direito do mouse no projeto VSIX e **selecione Adicionar** > **novo item** **(Ctrl**+**Shift**+**A).** No nó Extensibility para o idioma do projeto, selecione **Janela de ferramenta personalizada,** dê um nome à janela da ferramenta e pressione o botão **Adicionar.**

 Estes são os lugares-chave para usar apelidos em uma janela de ferramenta. Siga as instruções para cada um:

1. A guia da janela da ferramenta quando as guias ficam pequenas o suficiente (também usada no switcher de janela **ctrl**+**tab).**

    Adicione esta linha ao construtor para a classe derivada do tipo **ToolWindowPane:**

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. O comando para abrir a janela da ferramenta.

    No arquivo *.vsct* do pacote, edite o botão de comando da janela da ferramenta:

   ```xml
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->
     <Icon guid="ImageCatalogGuid" id="Blank" />
     <!-- Add this -->
     <CommandFlag>IconIsMoniker</CommandFlag>
     <Strings>
       <ButtonText>MyToolWindow</ButtonText>
     </Strings>
   </Button>
   ```

   **Como uso apelidos de imagem em uma janela de ferramenta existente?**

   Atualizar uma janela de ferramenta existente para usar apelidos de imagem é semelhante às etapas para criar uma nova janela de ferramenta.

   Estes são os lugares-chave para usar apelidos em uma janela de ferramenta. Siga as instruções para cada um:

3. A guia da janela da ferramenta quando as guias ficam pequenas o suficiente (também usada no switcher de janela **ctrl**+**tab).**

   1. Remova essas linhas (se elas existirem) no construtor para a classe derivada do tipo **ToolWindowPane:**

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Veja o passo #1 do "Como uso apelidos de imagem em uma nova janela de ferramentas?" seção acima.

4. O comando para abrir a janela da ferramenta.

   - Veja o passo #2 do "Como uso apelidos de imagem em uma nova janela de ferramentas?" seção acima.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Como faço para usar apelidos de imagem em um arquivo .vsct?
 Atualize seu arquivo *.vsct* conforme indicado pelas linhas comentadas abaixo:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!--  Include the definitions for images included in the VS image catalog -->
  <Include href="KnownImageIds.vsct"/>
  <Commands package="guidMyPackage">
    <Buttons>
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.
             In this case, we're using the Guid for the VS image catalog.
             Change the id attribute to be the ID of the desired image moniker. -->
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />
        <CommandFlag>DynamicVisibility</CommandFlag>
        <CommandFlag>DefaultInvisible</CommandFlag>
        <CommandFlag>DefaultDisabled</CommandFlag>
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>IconAndText</CommandFlag>
        <!-- Add the IconIsMoniker CommandFlag -->
        <CommandFlag>IconIsMoniker</CommandFlag>
        <Strings>
          <ButtonText>Quick Fixes...</ButtonText>
          <CommandName>Show Quick Fixes</CommandName>
          <CanonicalName>ShowQuickFixes</CanonicalName>
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>
        </Strings>
      </Button>
    </Buttons>
  </Commands>
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->
  <Symbols>
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">
      <IDSymbol name="cmdidMyCommand" value="0x9437" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```

 **E se meu arquivo .vsct também precisar ser lido por versões mais antigas do Visual Studio?**

 As versões mais antigas do Visual Studio não reconhecem o sinalizador de comando **IconIsMoniker.** Você pode usar imagens do serviço de imagem em versões do Visual Studio que o suportam, mas continuar a usar imagens antigas em versões mais antigas do Visual Studio. Para fazer isso, você deixaria o arquivo *.vsct* inalterado (e, portanto, compatível com versões mais antigas do Visual Studio) e criaria um arquivo CSV (valores separados por comma) que mapeia a partir de pares GUID/ID definidos em um bitmaps de \<arquivo *.vsct*> elemento para pares guid/ID de apelido de imagem.

 O formato do arquivo CSV de mapeamento é:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 O arquivo CSV é implantado com o pacote e sua localização é especificada pela propriedade **IconMappingFilename** do atributo **ProvideMenuResource:**

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 O **IconMappingFilename** é um caminho relativo implicitamente enraizado em $PackageFolder$ (como no exemplo acima) ou um caminho absoluto explicitamente enraizado em um diretório definido por uma variável de ambiente, como *@"%UserProfile%\dir1\dir2\MyMappingFile.csv"*.

## <a name="how-do-i-port-a-project-system"></a>Como porto um sistema de projeto?
 **Como fornecer ImageMonikers para um projeto**

1. Implementar **VSHPROPID_SupportsIconMonikers** na **Hierarquia de IVs**do projeto e retornar verdadeiro.

2. Implementar **VSHPROPID_IconMonikerImageList** (se o projeto original utilizou **VSHPROPID_IconImgList)** ou **VSHPROPID_IconMonikerGuid,** **VSHPROPID_IconMonikerId,** **VSHPROPID_OpenFolderIconMonikerGuid,** **VSHPROPID_OpenFolderIconMonikerId** (se o projeto original usou **VSHPROPID_IconHandle** e **VSHPROPID_OpenFolderIconHandle).**

3. Altere a implementação dos VSHPROPIDs originais para que os ícones criem versões "herdadas" dos ícones se os pontos de extensão os solicitarem. **O iVsImageService2** fornece funcionalidade necessária para obter esses ícones

   **Requisitos extras para sabores de projeto VB/C#**

   Só implemente **VSHPROPID_SupportsIconMonikers** se você detectar que seu projeto é o **sabor mais externo**. Caso contrário, o sabor mais externo real pode não suportar apelidos de imagem na realidade, e seu sabor base pode efetivamente "esconder" imagens personalizadas.

   **Como uso apelidos de imagem no CPS?**

   A definição de imagens personalizadas no CPS (Common Project System) pode ser feita manualmente ou através de um modelo de item que vem com o Project System Extensibility SDK.

   **Usando o SDK de extensibilidade do sistema de projeto**

   Siga as instruções em [Fornecer ícones personalizados para o tipo tipo/item do projeto](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) para personalizar suas imagens CPS. Mais informações sobre o CPS podem ser encontradas na [documentação de extensibilidade do Visual Studio Project System](https://github.com/Microsoft/VSProjectSystem)

   **Use manualmente ImageMonikers**

4. Implemente e exporte a interface **IProjectTreeModifier** em seu sistema de projeto.

5. Determine qual **KnownMoniker** ou o apelido de imagem personalizado que você deseja usar.

6. No método **AplicarModificações,** faça o seguinte em algum lugar no método antes de retornar a nova árvore, semelhante ao exemplo abaixo:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Se você estiver criando uma nova árvore, você pode definir as imagens personalizadas passando os apelidos desejados para o método NewTree, semelhante ao exemplo abaixo:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,
                                                /*filePath*/<value>,
                                                /*browseObjectProperties*/<value>,
                                                icon,
                                                expandedIcon);
   ```

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Como faço para converter de uma tira de imagem real para uma tira de imagem baseada em apelidos?
 **Preciso apoiar os HIMAGELISTs.**

 Se houver uma tira de imagem já existente para o seu código que você deseja atualizar para usar o serviço de imagem, mas você está limitado por APIs que requerem passar em torno de listas de imagens, você ainda pode obter os benefícios do serviço de imagem. Para criar uma tira de imagem baseada em apelidos, siga os passos abaixo para criar um manifesto a partir de apelidos existentes.

1. Execute a ferramenta **ManifestFromResources,** passando-a pela tira de imagem. Isso vai gerar um manifesto para a tira.

   - Recomendação: forneça um nome não padrão para o manifesto se adequar ao seu uso.

2. Se você estiver usando apenas **KnownMonikers,** então faça o seguinte:

   - Substitua \<a seção Imagens> do manifesto por \<Imagens/>.

   - Remova todos os IDs de \<subimagem (qualquer coisa com o nome de viagem de imagens>_##).

   - Recomendado: renomeie o símbolo assetsGuid e o símbolo da tira de imagem para se adequar ao seu uso.

   - Substitua cada GUID do **ContainedImage**por $(ImageCatalogGuid), substitua cada\<ID do **ContainedImage**por $(>) e adicione o atributo Externo="verdadeiro" a cada **ContainedImage**

       - \<> deve ser substituído pelo **KnownMoniker** que corresponde à imagem, mas com os "KnownMonikers". removido do nome.

   - Adicionar\\ <Importar Manifesto="$(Pasta de manifesto)\><Caminho relativo de instalação dir\* para * \Microsoft.VisualStudio.ImageCatalog.imagemanifest" /> na parte superior da \<seção Símbolos>.

       - O caminho relativo é determinado pelo local de implantação definido na configuração de autoria do manifesto.

3. Execute a ferramenta **ManifestToCode** para gerar invólucros para que o código existente tenha um apelido que possa ser usado para consultar o serviço de imagem da tira de imagem.

   - Recomendação: forneça nomes não padrão para os invólucros e espaços de nome para se adequar ao seu uso.

4. Faça todos os acréscimos, a autoria/implantação de configuração e outras alterações de código para trabalhar com o serviço de imagem e os novos arquivos.

   Manifesto de amostra, incluindo imagens internas e externas para ver como deve ser:

```xml
<?xml version="1.0"?>
<ImageManifest
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">

  <Symbols>
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest
         where $(ManifestFolder) is the deployed location of this manifest. -->
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />
    <ID Name="MyImage_0" Value="100" />
    <ID Name="MyImage_1" Value="101" />
    <ID Name="InternalList" Value="1001" />
    <ID Name="ExternalList" Value="1002" />
  </Symbols>

  <Images>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">
      <Source Uri="$(Resources)/MyImage_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">
      <Source Uri="$(Resources)/MyImage_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>

  <ImageLists>
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />
    </ImageList>
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />
    </ImageList>
  </ImageLists>

</ImageManifest>
```

 **Não preciso apoiar os HIMAGELISTs.**

1. Determine o conjunto de **KnownMonikers** que correspondem às imagens em sua tira de imagem ou crie seus próprios apelidos para as imagens em sua tira de imagem.

2. Atualize qualquer mapeamento que você usou para obter a imagem no índice necessário na tira de imagem para usar os apelidos em vez disso.

3. Atualize seu código para usar o serviço de imagem para solicitar apelidos através do mapeamento atualizado. (Isso pode significar atualizar para **o CrispImages** para código gerenciado ou solicitar HBITMAPs ou HICONs do serviço de imagem e passá-los para código nativo.)

## <a name="testing-your-images"></a>Testando suas imagens
 Você pode usar a ferramenta Visualizador de Biblioteca de Imagens para testar os manifestos de sua imagem para garantir que tudo seja de autoria corretamente. Você pode encontrar a ferramenta no [Visual Studio 2015 SDK](visual-studio-sdk.md). A documentação para esta ferramenta e outras podem ser encontradas [aqui.](/visualstudio/extensibility/internals/vssdk-utilities?view=vs-2015)

## <a name="additional-resources"></a>Recursos adicionais

### <a name="samples"></a>Exemplos
 Várias das amostras do Visual Studio no GitHub foram atualizadas para mostrar como usar o serviço de imagem como parte de vários pontos de extensibilidade do Visual Studio.

 Verifique [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) as últimas amostras.

### <a name="tooling"></a>Ferramentas
 Um conjunto de ferramentas de suporte para o Serviço de Imagem foi criado para ajudar na criação/atualização da ui que funciona com o Serviço de Imagem. Para obter mais informações sobre cada ferramenta, verifique a documentação que vem com as ferramentas. As ferramentas estão incluídas como parte do [Visual Studio 2015 SDK](visual-studio-sdk.md).

 **ManifestFromResources**

 A ferramenta Manifest from Resources pega uma lista de recursos de imagem (PNG ou XAML) e gera um arquivo manifesto de imagem para usar essas imagens com o serviço de imagem.

 **ManifestToCode**

 A ferramenta Manifest to Code pega um arquivo manifesto de imagem e gera um arquivo de invólucro para referenciar os valores manifestos em arquivos de código (C++, C#ou VB) ou *.vsct.*

 **ImageLibraryViewer**

 A ferramenta Image Library Viewer pode carregar manifestos de imagem e permite que o usuário os manipule da mesma forma que o Visual Studio faria para garantir que o manifesto seja de autoria corretamente. O usuário pode alterar o plano de fundo, tamanhos, configuração de DPI, Alto Contraste e outras configurações. Ele também exibe informações de carregamento para encontrar erros nos manifestos e exibe informações de origem para cada imagem no manifesto.

## <a name="faq"></a>Perguntas frequentes

- Existem dependências que você deve \<incluir ao carregar referência Include="Microsoft.VisualStudio.*. Interop.14.0.DesignTime" />?

  - Defina EmbedInteropTypes="true" em todas as DLLs interop.

- Como faço para implantar um manifesto de imagem com a minha extensão?

  - Adicione o arquivo *.imagemanifest* ao seu projeto.

  - Definir "Incluir em VSIX" para True.

- Estou atualizando meu sistema de projetos cps. O que aconteceu com **ImageName** e **StockIconService**?

  - Estes foram removidos quando o CPS foi atualizado para usar apelidos. Você não precisa mais chamar o **StockIconService,** basta passar o **KnownMoniker** desejado para o método ou propriedade usando o método de extensão **ToProjectSystemType()** nos utilitários CPS. Você pode encontrar um mapeamento de **ImageName** para **KnownMonikers** abaixo:

    |||
    |-|-|
    |**ImageName**|**Moniker conhecido**|
    |Nome da imagem.OfflineWebApp|KnownImageIds.Web|
    |ImageName.WebReferencesPasta|KnownImageIds.Web|
    |Legenda do nome de imagem.openReferenceFolder|KnownImageIds.FolderAberto|
    |ImageName.ReferenceFolder|KnownImageIds.Reference|
    |ImageName.Reference|KnownImageIds.Reference|
    |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|
    |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|
    |Nome de imagem.pasta|KnownImageIds.FolderClosed|
    |ImageName.OpenFolder|KnownImageIds.FolderAberto|
    |Nome de imagem.Pasta excluída|KnownImageIds.HiddenFolderClosed|
    |ImageName.OpenExcludedfolder|KnownImageIds.HiddenFolderAberto|
    |Nome da imagem.Arquivo excluído|KnownImageIds.HiddenFile|
    |Nome de imagem.DependentFile|KnownImageIds.GenerateFile|
    |Nome da imagem.Arquivo ausente|KnownImageIds.DocumentWarning|
    |Nome da imagem.WindowsForm|KnownImageIds.WindowsForm|
    |Nome da imagem.Controle de usuário do WindowsUser|KnownImageIds.UserControl|
    |Nome de imagem.WindowsComponent|KnownImageIds.ComponentFile|
    |Nome da imagem.XmlSchema|KnownImageIds.XMLSchema|
    |ImageName.XmlFile|KnownImageIds.XMLFile|
    |Nome da imagem.WebForm|KnownImageIds.Web|
    |ImageName.WebService|KnownImageIds.WebService|
    |Nome de imagem.WebUserControl|KnownImageIds.WebUserControl|
    |Nome de imagem.WebCustomUserControl|KnownImageIds.WebCustomControl|
    |ImageName.AspPage|KnownImageIds.ASPFile|
    |Nome de imagem.GlobalApplicationClass|KnownImageIds.SettingsFile|
    |ImageName.WebConfig|KnownImageIds.ConfigurationFile|
    |ImageName.htmlPage|KnownImageIds.HTMLFile|
    |Nome de imagem.Folha de estilos|KnownImageIds.StyleSheet|
    |Nome de imagem.arquivo de script|KnownImageIds.JSScript|
    |Nome de imagem.arquivo de texto|KnownImageIds.Document|
    |Nome da imagem.configuraçõesArquivo|KnownImageIds.Configurações|
    |ImageName.Resources|KnownImageIds.DocumentGroup|
    |ImageName.Bitmap|KnownImageIds.Image|
    |ImageName.Icon|KnownImageIds.IconFile|
    |ImageName.Image|KnownImageIds.Image|
    |ImageName.ImageMap|KnownImageIds.ImageMapFile|
    |ImageName.XWorld|KnownImageIds.XWorldFile|
    |ImageName.Audio|KnownImageIds.Sound|
    |ImageName.Video|KnownImageIds.Media|
    |ImageName.Cab|KnownImageIds.CABProject|
    |ImageName.Jar|KnownImageIds.JARFile|
    |ImageName.dataEnvironment|KnownImageIds.DataTable|
    |Arquivo de visualização de nome de imagem.visualização|KnownImageIds.Report|
    |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|
    |ImageName.XsltFile|KnownImageIds.XSLTransform|
    |ImageName.Cursor|KnownImageIds.CursorFile|
    |ImageName.AppDesignerFolder|KnownImageIds.Property|
    |ImageName.Data|KnownImageIds.Database|
    |Nome da imagem.aplicativo|KnownImageIds.Application|
    |Nome de imagem.conjunto de dados|KnownImageIds.DatabaseGroup|
    |Nome da imagem.Pfx|KnownImageIds.Certificate|
    |ImageName.Snk|KnownImageIds.Rule|
    |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|
    |ImageName.CSharpProject|KnownImageIds.CSProjectNode|
    |Nome da imagem.vazio|KnownImageIds.Blank|
    |Nome da imagem.pasta ausente|KnownImageIds.FolderOffline|
    |ImageName.SharedImportReference|KnownImageIds.SharedProject|
    |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|
    |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|
    |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|
    |Nome de imagem.CSharpCodeFile|KnownImageIds.CSFileNode|
    |Nome da imagem.VisualBasicCodeFile|KnownImageIds.VBFileNode|

  - Estou atualizando meu provedor de lista de conclusão. O **que os KnownMonikers** combinam com os antigos valores **StandardGlyphGroup** e **StandardGllyph?**

    ||||
    |-|-|-|
    |GlifoGroupClass|GlifoPublic|ClassePública|
    |GlifoGroupClass|Glifo-de-tempoInterno|ClassInternal|
    |GlifoGroupClass|GlifoAmigo|ClassInternal|
    |GlifoGroupClass|GlifoProtegido|ClassProtected|
    |GlifoGroupClass|GlifoPrivado|ClassPrivate|
    |GlifoGroupClass|GlyphItemAtalho|Atalho de classe|
    |GlifoGroupConstant|GlifoPublic|ConstantPublic|
    |GlifoGroupConstant|Glifo-de-tempoInterno|ConstantInternal|
    |GlifoGroupConstant|GlifoAmigo|ConstantInternal|
    |GlifoGroupConstant|GlifoProtegido|ConstantProtected|
    |GlifoGroupConstant|GlifoPrivado|ConstantPrivate|
    |GlifoGroupConstant|GlyphItemAtalho|Atalho de constante|
    |GliphGroupDelegate|GlifoPublic|DelegadoPúblico|
    |GliphGroupDelegate|Glifo-de-tempoInterno|DelegadoInterno|
    |GliphGroupDelegate|GlifoAmigo|DelegadoInterno|
    |GliphGroupDelegate|GlifoProtegido|DelegadaProtegida|
    |GliphGroupDelegate|GlifoPrivado|DelegadoPrivado|
    |GliphGroupDelegate|GlyphItemAtalho|DelegateAtalho|
    |GlifoGroupEnum|GlifoPublic|EnumeraçãoPublic|
    |GlifoGroupEnum|Glifo-de-tempoInterno|EnumeraçãoInterna|
    |GlifoGroupEnum|GlifoAmigo|EnumeraçãoInterna|
    |GlifoGroupEnum|GlifoProtegido|EnumeraçãoProtegida|
    |GlifoGroupEnum|GlifoPrivado|EnumeraçãoPrivada|
    |GlifoGroupEnum|GlyphItemAtalho|Atalho de enumeração|
    |Membro do GllyphGroupEnum|GlifoPublic|EnumeraçãoItemPublic|
    |Membro do GllyphGroupEnum|Glifo-de-tempoInterno|EnumeraçãoItemInternal|
    |Membro do GllyphGroupEnum|GlifoAmigo|EnumeraçãoItemInternal|
    |Membro do GllyphGroupEnum|GlifoProtegido|EnumeraçãoItemProtegido|
    |Membro do GllyphGroupEnum|GlifoPrivado|EnumeraçãoItemPrivado|
    |Membro do GllyphGroupEnum|GlyphItemAtalho|EnumeraçãoItemAtalho|
    |GliphGroupEvent|GlifoPublic|EventPublic|
    |GliphGroupEvent|Glifo-de-tempoInterno|EventInternal|
    |GliphGroupEvent|GlifoAmigo|EventInternal|
    |GliphGroupEvent|GlifoProtegido|EventProtected|
    |GliphGroupEvent|GlifoPrivado|EventoPrivado|
    |GliphGroupEvent|GlyphItemAtalho|Atalho de evento|
    |GliphGroupException|GlifoPublic|ExceçãoPública|
    |GliphGroupException|Glifo-de-tempoInterno|ExceçãoInterna|
    |GliphGroupException|GlifoAmigo|ExceçãoInterna|
    |GliphGroupException|GlifoProtegido|ExceçãoProtegida|
    |GliphGroupException|GlifoPrivado|ExceçãoPrivada|
    |GliphGroupException|GlyphItemAtalho|Atalho de exceção|
    |GliphGroupField|GlifoPublic|FieldPublic|
    |GliphGroupField|Glifo-de-tempoInterno|FieldInternal|
    |GliphGroupField|GlifoAmigo|FieldInternal|
    |GliphGroupField|GlifoProtegido|FieldProtected|
    |GliphGroupField|GlifoPrivado|FieldPrivate|
    |GliphGroupField|GlyphItemAtalho|Atalho de campo|
    |GliphGroupInterface|GlifoPublic|InterfacePública|
    |GliphGroupInterface|Glifo-de-tempoInterno|InterfaceInterna|
    |GliphGroupInterface|GlifoAmigo|InterfaceInterna|
    |GliphGroupInterface|GlifoProtegido|InterfaceProtegida|
    |GliphGroupInterface|GlifoPrivado|InterfacePrivada|
    |GliphGroupInterface|GlyphItemAtalho|Atalho de interface|
    |GlifoGroupMacro|GlifoPublic|MacroPúblico|
    |GlifoGroupMacro|Glifo-de-tempoInterno|MacroInternal|
    |GlifoGroupMacro|GlifoAmigo|MacroInternal|
    |GlifoGroupMacro|GlifoProtegido|MacroProtegido|
    |GlifoGroupMacro|GlifoPrivado|MacroPrivate|
    |GlifoGroupMacro|GlyphItemAtalho|Atalho de macro|
    |GliphGroupMap|GlifoPublic|MapPublic|
    |GliphGroupMap|Glifo-de-tempoInterno|MapInternal|
    |GliphGroupMap|GlifoAmigo|MapInternal|
    |GliphGroupMap|GlifoProtegido|MapaProtegido|
    |GliphGroupMap|GlifoPrivado|MapaPrivate|
    |GliphGroupMap|GlyphItemAtalho|MapAtalho|
    |GlifoGroupMapItem|GlifoPublic|MapItemPublic|
    |GlifoGroupMapItem|Glifo-de-tempoInterno|MapItemInternal|
    |GlifoGroupMapItem|GlifoAmigo|MapItemInternal|
    |GlifoGroupMapItem|GlifoProtegido|MapItemProtegido|
    |GlifoGroupMapItem|GlifoPrivado|MapItemPrivado|
    |GlifoGroupMapItem|GlyphItemAtalho|MapItemAtalho|
    |GliphGroupMethod|GlifoPublic|MethodPublic|
    |GliphGroupMethod|Glifo-de-tempoInterno|Métodointerno|
    |GliphGroupMethod|GlifoAmigo|Métodointerno|
    |GliphGroupMethod|GlifoProtegido|MétodoProtegido|
    |GliphGroupMethod|GlifoPrivado|MétodoPrivado|
    |GliphGroupMethod|GlyphItemAtalho|Atalho de método|
    |GliphGroupOverload|GlifoPublic|MethodPublic|
    |GliphGroupOverload|Glifo-de-tempoInterno|Métodointerno|
    |GliphGroupOverload|GlifoAmigo|Métodointerno|
    |GliphGroupOverload|GlifoProtegido|MétodoProtegido|
    |GliphGroupOverload|GlifoPrivado|MétodoPrivado|
    |GliphGroupOverload|GlyphItemAtalho|Atalho de método|
    |GliphGroupModule|GlifoPublic|MóduloPúblico|
    |GliphGroupModule|Glifo-de-tempoInterno|MóduloInterno|
    |GliphGroupModule|GlifoAmigo|MóduloInterno|
    |GliphGroupModule|GlifoProtegido|MóduloProtegido|
    |GliphGroupModule|GlifoPrivado|MóduloPrivado|
    |GliphGroupModule|GlyphItemAtalho|Atalho de módulo|
    |GlifoGroupNamespace|GlifoPublic|NamespacePublic|
    |GlifoGroupNamespace|Glifo-de-tempoInterno|NamespaceInternal|
    |GlifoGroupNamespace|GlifoAmigo|NamespaceInternal|
    |GlifoGroupNamespace|GlifoProtegido|NamespaceProtegido|
    |GlifoGroupNamespace|GlifoPrivado|NamespacePrivate|
    |GlifoGroupNamespace|GlyphItemAtalho|Atalho de namespace|
    |GliphGroupOperator|GlifoPublic|OperadorPúblico|
    |GliphGroupOperator|Glifo-de-tempoInterno|OperadorInterno|
    |GliphGroupOperator|GlifoAmigo|OperadorInterno|
    |GliphGroupOperator|GlifoProtegido|OperadorProtegido|
    |GliphGroupOperator|GlifoPrivado|OperadorPrivado|
    |GliphGroupOperator|GlyphItemAtalho|Atalho de operador|
    |GliphGroupProperty|GlifoPublic|PropriedadePública|
    |GliphGroupProperty|Glifo-de-tempoInterno|PropriedadeInterna|
    |GliphGroupProperty|GlifoAmigo|PropriedadeInterna|
    |GliphGroupProperty|GlifoProtegido|PropriedadeProtegida|
    |GliphGroupProperty|GlifoPrivado|PropriedadePrivada|
    |GliphGroupProperty|GlyphItemAtalho|Atalho de propriedade|
    |GliphGroupStruct|GlifoPublic|EstruturaPública|
    |GliphGroupStruct|Glifo-de-tempoInterno|EstruturaInterna|
    |GliphGroupStruct|GlifoAmigo|EstruturaInterna|
    |GliphGroupStruct|GlifoProtegido|EstruturaProtegida|
    |GliphGroupStruct|GlifoPrivado|EstruturaPrivada|
    |GliphGroupStruct|GlyphItemAtalho|Atalho de estrutura|
    |Modelo de GlyphGroup|GlifoPublic|ModeloPúblico|
    |Modelo de GlyphGroup|Glifo-de-tempoInterno|Modelointerno|
    |Modelo de GlyphGroup|GlifoAmigo|Modelointerno|
    |Modelo de GlyphGroup|GlifoProtegido|Modeloprotegido|
    |Modelo de GlyphGroup|GlifoPrivado|ModeloPrivado|
    |Modelo de GlyphGroup|GlyphItemAtalho|Atalho de modelo|
    |GlifoGroupTypedef|GlifoPublic|Definição de tipoPúblico|
    |GlifoGroupTypedef|Glifo-de-tempoInterno|Definição de tipoInterna|
    |GlifoGroupTypedef|GlifoAmigo|Definição de tipoInterna|
    |GlifoGroupTypedef|GlifoProtegido|TypeDefinitionProtected|
    |GlifoGroupTypedef|GlifoPrivado|TipoDefiniçãoPrivada|
    |GlifoGroupTypedef|GlyphItemAtalho|Atalho de definição de tipo|
    |GlifoGroupType|GlifoPublic|TypePublic|
    |GlifoGroupType|Glifo-de-tempoInterno|TypeInternal|
    |GlifoGroupType|GlifoAmigo|TypeInternal|
    |GlifoGroupType|GlifoProtegido|TypeProtected|
    |GlifoGroupType|GlifoPrivado|TypePrivate|
    |GlifoGroupType|GlyphItemAtalho|Atalho de tipo|
    |GlifaGroupUnion|GlifoPublic|UnionPublic|
    |GlifaGroupUnion|Glifo-de-tempoInterno|SindicatoInterno|
    |GlifaGroupUnion|GlifoAmigo|SindicatoInterno|
    |GlifaGroupUnion|GlifoProtegido|UnionProtected|
    |GlifaGroupUnion|GlifoPrivado|UnionPrivate|
    |GlifaGroupUnion|GlyphItemAtalho|UnionShortcut|
    |GliphGroupVariable|GlifoPublic|FieldPublic|
    |GliphGroupVariable|Glifo-de-tempoInterno|FieldInternal|
    |GliphGroupVariable|GlifoAmigo|FieldInternal|
    |GliphGroupVariable|GlifoProtegido|FieldProtected|
    |GliphGroupVariable|GlifoPrivado|FieldPrivate|
    |GliphGroupVariable|GlyphItemAtalho|Atalho de campo|
    |GlyphGroupValueType|GlifoPublic|ValueTypePublic|
    |GlyphGroupValueType|Glifo-de-tempoInterno|ValueTypeInternal|
    |GlyphGroupValueType|GlifoAmigo|ValueTypeInternal|
    |GlyphGroupValueType|GlifoProtegido|ValueTypeProtected|
    |GlyphGroupValueType|GlifoPrivado|ValueTypePrivate|
    |GlyphGroupValueType|GlyphItemAtalho|Atalho de tipo de valor|
    |GlifoGrupoIntrínseco|GlifoPublic|ObjectPublic|
    |GlifoGrupoIntrínseco|Glifo-de-tempoInterno|Objetointerno|
    |GlifoGrupoIntrínseco|GlifoAmigo|Objetointerno|
    |GlifoGrupoIntrínseco|GlifoProtegido|Objetoprotegido|
    |GlifoGrupoIntrínseco|GlifoPrivado|ObjetoPrivado|
    |GlifoGrupoIntrínseco|GlyphItemAtalho|Atalho de objeto|
    |GliphGroupJSharpMethod|GlifoPublic|MethodPublic|
    |GliphGroupJSharpMethod|Glifo-de-tempoInterno|Métodointerno|
    |GliphGroupJSharpMethod|GlifoAmigo|Métodointerno|
    |GliphGroupJSharpMethod|GlifoProtegido|MétodoProtegido|
    |GliphGroupJSharpMethod|GlifoPrivado|MétodoPrivado|
    |GliphGroupJSharpMethod|GlyphItemAtalho|Atalho de método|
    |GlifoGroupJSharpField|GlifoPublic|FieldPublic|
    |GlifoGroupJSharpField|Glifo-de-tempoInterno|FieldInternal|
    |GlifoGroupJSharpField|GlifoAmigo|FieldInternal|
    |GlifoGroupJSharpField|GlifoProtegido|FieldProtected|
    |GlifoGroupJSharpField|GlifoPrivado|FieldPrivate|
    |GlifoGroupJSharpField|GlyphItemAtalho|Atalho de campo|
    |GlifoGroupJSharpClass|GlifoPublic|ClassePública|
    |GlifoGroupJSharpClass|Glifo-de-tempoInterno|ClassInternal|
    |GlifoGroupJSharpClass|GlifoAmigo|ClassInternal|
    |GlifoGroupJSharpClass|GlifoProtegido|ClassProtected|
    |GlifoGroupJSharpClass|GlifoPrivado|ClassPrivate|
    |GlifoGroupJSharpClass|GlyphItemAtalho|Atalho de classe|
    |GlifoGroupJSharpNamespace|GlifoPublic|NamespacePublic|
    |GlifoGroupJSharpNamespace|Glifo-de-tempoInterno|NamespaceInternal|
    |GlifoGroupJSharpNamespace|GlifoAmigo|NamespaceInternal|
    |GlifoGroupJSharpNamespace|GlifoProtegido|NamespaceProtegido|
    |GlifoGroupJSharpNamespace|GlifoPrivado|NamespacePrivate|
    |GlifoGroupJSharpNamespace|GlyphItemAtalho|Atalho de namespace|
    |GlifoGroupJSharpInterface|GlifoPublic|InterfacePública|
    |GlifoGroupJSharpInterface|Glifo-de-tempoInterno|InterfaceInterna|
    |GlifoGroupJSharpInterface|GlifoAmigo|InterfaceInterna|
    |GlifoGroupJSharpInterface|GlifoProtegido|InterfaceProtegida|
    |GlifoGroupJSharpInterface|GlifoPrivado|InterfacePrivada|
    |GlifoGroupJSharpInterface|GlyphItemAtalho|Atalho de interface|
    |GliphGroupError||StatusError|
    |Glifo-de-arquivo||Arquivo de classe|
    |GlyphAssembly||Referência|
    |Biblioteca Glifos||Biblioteca|
    |GliphVBProject||VBProjectNode|
    |GlyphCoolProject||CSProjectNode|
    |GliphCppProject||CPPProjectNode|
    |GlifoDialogId||caixa de diálogo|
    |GlifoPasta||PastaAberta|
    |Pasta-do-glifofechado||Pastafechada|
    |Glifa||Gotonext|
    |Arquivo GliphCSharp||CSFileNode|
    |Expansão glifo-nítida||Snippet|
    |Palavra-chave de glifos||IntellisensePalavra-chave|
    |Informações glifos||Informações sobre status|
    |GlifinaReferência||Referência de método de classe|
    |Glifracursiona||Recursão|
    |GlifoXmlItem||Marca|
    |Projeto GlifoSharp||DocumentCollection|
    |GliphJSharpDocument||Document|
    |GliphForwardType||Gotonext|
    |GlifoCallersGraph||Callto|
    |Glifográfico||Ligação|
    |GlifoAviso||StatusWarning|
    |GlifeMaybeReference||Marca de perguntas|
    |GlifoMaybeCaller||Callto|
    |GlifoMaybeCall||Ligação|
    |GliphExtensionMethod||Método de extensão|
    |GliphExtensionMethodInternal||Método de extensão|
    |GliphExtensionMethodFriend||Método de extensão|
    |GliphExtensionMethodProtegido||Método de extensão|
    |GliphExtensionMethodPrivate||Método de extensão|
    |Atalho de método de extensão gliférdica||Método de extensão|
    |GlifoXmlAttribute||XmlAttribute|
    |Glifo||XmlElement|
    |GlifoDescendente||XmlDescendente|
    |GliphXmlNamespace||XmlNamespace|
    |GliphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |GliphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlifoXmlChildQuestão||XmlElementLowConfidence|
    |GlifoXmlChildCheck||XmlElementHighConfidence|
    |GlifoXmlDescendenteQuestão||XmlDescendantLowConfidence|
    |GlifoXmlDescendenteCheck||XmlDescendantHighConfidence|
    |GlifoAviso de conclusão||IntellisenseAviso|
