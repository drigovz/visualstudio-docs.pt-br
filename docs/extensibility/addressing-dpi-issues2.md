---
title: Abordando problemas de DPI2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740097"
---
# <a name="address-dpi-issues"></a>Endereçar problemas de DPI
Um número crescente de dispositivos está enviando com telas de "alta resolução". Essas telas normalmente têm mais de 200 pixels por polegada (ppi). Trabalhar com um aplicativo nesses computadores exigirá que o conteúdo seja ampliado para atender às necessidades de visualização do conteúdo a uma distância normal de visualização para o dispositivo. A partir de 2014, o principal alvo para displays de alta densidade são dispositivos de computação móvel (tablets, laptops e telefones).

O Windows 8.1 ou superior contém vários recursos para permitir que essas máquinas trabalhem com displays e ambientes onde a máquina está conectada tanto a displays de alta densidade quanto a densidade padrão ao mesmo tempo.

- O Windows pode permitir que você dimensione o conteúdo para o dispositivo usando a configuração "Faça texto e outros itens maiores ou menores" (disponível desde o Windows XP).

- O Windows 8.1 ou superior irá escalar automaticamente o conteúdo para que a maioria dos aplicativos seja consistente quando movido entre displays de densidades de pixels diferentes. Quando o display principal é de alta densidade (200% de escala) e o display secundário é de densidade padrão (100%), o Windows dimensionará automaticamente o conteúdo da janela do aplicativo para baixo no display secundário (1 pixel exibido para cada 4 pixels renderizados pelo aplicativo).

- O Windows será padrão para o dimensionamento certo para a densidade de pixels e a distância de visualização para o display (Windows 7 e superior, configurável por OEM).

- O Windows pode dimensionar automaticamente conteúdo em até 250% em novos dispositivos que excedam 280 ppi (a partir do Windows 8.1 S14).

  O Windows tem uma maneira de lidar com a escala ção da iu para aproveitar o aumento da contagem de pixels. Um aplicativo opta por esse sistema declarando-se "consciente do DPI do sistema". Os aplicativos que não fazem isso são dimensionados pelo sistema. Isso pode resultar em uma experiência de usuário "difusa", onde todo o aplicativo é uniformemente esticado por pixels. Por exemplo:

  ![Problemas de DPI Fuzzy](../extensibility/media/dpi-issues-fuzzy.png "Problemas de DPI Fuzzy")

  O Visual Studio opta por ser consciente de dimensionamento de DPI e, portanto, não é "virtualizado".

  O Windows (e o Visual Studio) utilizam várias tecnologias de IA, que têm maneiras diferentes de lidar com fatores de escala definidos pelo sistema. Por exemplo:

- O WPF mede os controles de forma independente do dispositivo (unidades, não pixels). O WPF UI é dimensionado automaticamente para o DPI atual.

- Todos os tamanhos de texto, independentemente do framework da UI, são expressos em pontos, e por isso são tratados pelo sistema como independente de DPI. Texto em Win32, WinForms e WPF já são dimensionados corretamente quando atraídos para o dispositivo de exibição.

- Os diálogos e janelas Win32/WinForms têm meios para ativar o layout que redimensiona com texto (por exemplo, através de painéis de grade, fluxo e layout de tabela). Isso permite evitar locais de pixels codificados em código rígido que não são dimensionados quando os tamanhos da fonte são aumentados.

- Os ícones fornecidos pelo sistema ou recursos com base em métricas do sistema (por exemplo, SM_CXICON e SM_CXSMICON) já estão ampliados.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Win32 mais antigo (GDI, GDI+) e IU baseado em WinForms
Embora o WPF já esteja com alto conhecimento de DPI, grande parte do nosso código baseado em Win32/GDI não foi originalmente escrito com a consciência de DPI em mente. O Windows forneceu APIs de dimensionamento de DPI. As correções para problemas do Win32 devem usá-las de forma consistente em todo o produto. O Visual Studio forneceu uma biblioteca de classe auxiliar para evitar duplicar a funcionalidade e garantir a consistência em todo o produto.

## <a name="high-resolution-images"></a>Imagens de alta resolução
Esta seção é principalmente para desenvolvedores que estendem o Visual Studio 2013. Para o Visual Studio 2015, use o serviço de imagem que é incorporado ao Visual Studio. Você também pode achar que você precisa suportar/segmentar muitas versões do Visual Studio e, portanto, usar o serviço de imagem em 2015 não é uma opção, já que ele não existe em versões anteriores. Esta seção também é para você, então.

## <a name="scaling-up-images-that-are-too-small"></a>Dimensionamento de imagens que são muito pequenas
Imagens muito pequenas podem ser dimensionadas e renderizadas em GDI e WPF usando alguns métodos comuns. As classes de ajuda de DPI gerenciadas estão disponíveis para integradores internos e externos do Visual Studio para abordar ícones de dimensionamento, bitmaps, imagens e listas de imagens. Os ajudantes C/C++, baseados no Win32, estão disponíveis para dimensionar hicon, HBITMAP, HIMAGELIST e VsUI::GdiplusImage. O dimensionamento de um bitmap normalmente só requer uma alteração de uma linha depois de incluir uma referência à biblioteca auxiliar. Por exemplo:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

O dimensionamento de uma lista de imagens depende se a lista de imagens está completa no tempo de carga ou se é anexada no tempo de execução. Se estiver concluído na `LogicalToDeviceUnits()` hora da carga, ligue com a lista de imagens como você faria um bitmap. Quando o código precisar carregar um bitmap individual antes de compor a lista de imagens, certifique-se de dimensionar o tamanho da imagem da lista de imagens:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

Em código nativo, as dimensões podem ser dimensionadas ao criar a lista de imagens da seguinte forma:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

As funções na biblioteca permitem especificar o algoritmo de redimensionamento. Ao dimensionar imagens a serem colocadas em listas de imagens, certifique-se de especificar a cor de fundo usada para transparência ou usar o dimensionamento NearestNeighbor (que causará distorções em 125% e 150%).

Consulte <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> a documentação sobre MSDN.

A tabela a seguir mostra exemplos de como as imagens devem ser dimensionadas em fatores de dimensionamento de DPI correspondentes. As imagens descritas em laranja denotam nossa melhor prática como do Visual Studio 2013 (100%-200% de escala de DPI):

![Dimensionamento de problemas de DPI](../extensibility/media/dpi-issues-scaling.png "Dimensionamento de problemas de DPI")

## <a name="layout-issues"></a>Problemas de layout
Problemas comuns de layout podem ser evitados principalmente mantendo pontos na ia dimensionado e em relação um ao outro, em vez de usar locais absolutos (especificamente, em unidades de pixel). Por exemplo:

- As posições de layout/texto precisam ser ajustadas para explicar as imagens dimensionadas.

- As colunas nas grades precisam ter larguras ajustadas para o texto ampliado.

- Tamanhos codificados ou espaço entre elementos também precisarão ser ampliados. Tamanhos baseados apenas em dimensões de texto são tipicamente finos, porque as fontes são automaticamente dimensionadas.

  As funções do ajudante <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> estão disponíveis na classe para permitir o dimensionamento no eixo X e Y:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsUnitsY (as funções permitem o dimensionamento no eixo X/Y)

- espaço int = DpiHelper.LogicalToDeviceUnitsX (10);

- altura do int = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);

  Existem sobrecargas LogicalToDeviceUnits para permitir o dimensionamento de objetos como Rect, Point e Size.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Usando a biblioteca/classe do DPIHelper para dimensionar imagens e layout
A biblioteca auxiliar de DPI do Visual Studio está disponível em formulários nativos e gerenciados e pode ser usada fora do shell do Visual Studio por outras aplicações.

Para usar a biblioteca, vá para o [Visual Studio VSSDK amostras de extensibilidade](https://github.com/Microsoft/VSSDK-Extensibility-Samples) e clone a amostra de DPI_Images_Icons.

Nos arquivos de origem, inclua *VsUIDpiHelper.h* `VsUI::DpiHelper` e chame as funções estáticas da classe:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Não use as funções auxiliares em variáveis estáticas de nível de módulo ou de classe. A biblioteca também usa estática para sincronização de segmentos e você pode encontrar problemas de inicialização de pedidos. Converta essas estáticas em variáveis não estáticas ou enrole-as em uma função (para que sejam construídas no primeiro acesso).

Para acessar as funções de ajudante de DPI a partir de código gerenciado que será executado dentro do ambiente do Visual Studio:

- O projeto de consumo deve fazer referência à versão mais recente do Shell MPF. Por exemplo:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Certifique-se de que o projeto tenha referências ao **System.Windows.Forms,** **PresentationCore**e **PresentationUI**.

- Em código, use o **namespace microsoft.VisualStudio.PlatformUI** e chame funções estáticas da classe DpiHelper. Para tipos suportados (pontos, tamanhos, retângulos e assim por diante), existem funções de extensão fornecidas que retornam novos objetos dimensionados. Por exemplo:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Lidando com a difusão de imagem WPF em ui zoomable
No WPF, os bitmaps são redimensionados automaticamente pelo WPF para o nível atual de zoom de DPI usando um algoritmo bicúbico de alta qualidade (padrão), que funciona bem para imagens ou capturas de tela grandes, mas é inapropriado para ícones de itens de menu porque introduz a difusão percebida.

Recomendações:

- Para o trabalho artístico de <xref:System.Windows.Media.BitmapScalingMode> imagem de logotipo e banners, o modo de redimensionamento padrão poderia ser usado.

- Para itens de menu e imagens de iconografia, deve <xref:System.Windows.Media.BitmapScalingMode> ser usado quando não causar outros artefatos de distorção para eliminar a neblina (em 200% e 300%).

- Para grandes níveis de zoom não múltiplos de 100% (por exemplo, 250% ou 350%), dimensionar imagens de iconografia com resultados bicúbicos em ui difusa e lavada. Um resultado melhor é obtido primeiro dimensionando a imagem com o Neighbor mais próximo para o maior múltiplo de 100% (por exemplo, 200% ou 300%) e escalacom bicúbico de lá. Veja caso especial: pré-dimensionamento de imagens WPF para grandes níveis de DPI para obter mais informações.

  A classe DpiHelper no espaço de nome Microsoft.VisualStudio.PlatformUI fornece um membro <xref:System.Windows.Media.BitmapScalingMode> que pode ser usado para vinculação. Ele permitirá que o shell do Visual Studio controle o modo de dimensionamento do bitmap em todo o produto uniformemente, dependendo do fator de dimensionamento do DPI.

  Para usá-lo em XAML, adicione:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

O shell do Visual Studio já define essa propriedade em janelas e diálogos de alto nível. A ui baseada em WPF em execução no Visual Studio já a herdará. Se a configuração não se propagar para suas peças específicas de IU, ela pode ser definida no elemento raiz da UI XAML/WPF. Os lugares onde isso acontece incluem pop-ups, em elementos com os pais win32, e janelas de designer que ficam sem processo, como blend.

Algumas uI podem dimensionar independentemente do nível de zoom de DPI definido pelo sistema, como o editor de texto visual studio e designers baseados em WPF (WPF Desktop e Windows Store). Nestes casos, DpiHelper.BitmapScalingMode não deve ser usado. Para corrigir esse problema no editor, a equipe do IDE criou uma propriedade personalizada intitulada RenderOptions.BitmapScalingMode. Defina esse valor de propriedade como HighQuality ou NearestNeighbor, dependendo do nível de zoom combinado do sistema e da sua ia.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Caso especial: pré-dimensionamento de imagens WPF para grandes níveis de DPI
Para níveis de zoom muito grandes que não são múltiplos de 100% (por exemplo, 250%, 350%, e assim por diante), dimensionar imagens de iconografia com resultados bicúbicos em ui difusa e lavada. A impressão dessas imagens ao lado de texto nítido é quase como a de uma ilusão de ótica. As imagens parecem estar mais próximas do olho e fora de foco em relação ao texto. O resultado de escala neste tamanho ampliado pode ser melhorado primeiro dimensionando a imagem com o Neighbor mais próximo para o maior múltiplo de 100% (por exemplo, 200% ou 300%) e dimensionamento com bicúbico para o restante (adicional de 50%).

A seguir, um exemplo das diferenças nos resultados, onde a primeira imagem é dimensionada com o algoritmo de dupla escala melhorado 100%->200%->250%, e a segunda apenas com bicúbicos 100%->250%.

![DPI emite exemplo de dimensionamento duplo](../extensibility/media/dpi-issues-double-scaling-example.png "DPI emite exemplo de dimensionamento duplo")

Para permitir que a IA use essa dupla escala, a marcação XAML para exibir cada elemento de imagem precisará ser modificada. Os exemplos a seguir demonstram como usar o double-scaling no WPF no Visual Studio usando a biblioteca DpiHelper e o Shell.12/14.

Passo 1: Pré-dimensione a imagem para 200%, 300%, e assim por diante, usando o NearestNeighbor.

Pré-dimensione a imagem usando um conversor aplicado em uma vinculação ou com uma extensão de marcação XAML. Por exemplo:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Se a imagem também precisa ser temática (a maioria, se não todas, deve), a marcação pode usar um conversor diferente que primeiro faz o tema da imagem e, em seguida, pré-dimensionamento. A marcação pode <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>ser usada ou, dependendo da saída de conversão desejada.

```xaml
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />

<Image Width="16" Height="16">
  <Image.Source>
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">
      <Binding Path="Icon" />
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"
               RelativeSource="{RelativeSource Self}" />
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />
    </MultiBinding>
  </Image.Source>
</Image>
```

Passo 2: Certifique-se de que o tamanho final está correto para o DPI atual.

Como o WPF irá dimensionar a ID para o DPI atual usando a propriedade BitmapScalingMode definida no UIElement, um controle de imagem usando uma imagem pré-dimensionada como sua fonte será duas ou três vezes maior do que deveria. A seguir, algumas maneiras de contrariar esse efeito:

- Se você sabe a dimensão da imagem original em 100%, você pode especificar o tamanho exato do controle de imagem. Esses tamanhos refletirão o tamanho da ui antes da aplicação do dimensionamento.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Se o tamanho da imagem original não for conhecido, um LayoutTransform pode ser usado para reduzir o objeto final da Imagem. Por exemplo:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Habilitando o suporte ao HDPI para o WebOC
Por padrão, os controles do WebOC (como o controle do WebBrowser no WPF ou a interface IWebBrowser2) não permitem a detecção e o suporte do HDPI. O resultado será um controle incorporado com conteúdo de exibição muito pequeno em um display de alta resolução. O seguinte descreve como ativar o suporte a alta DPI em uma instância web WebOC específica.

Implemente a interface IDocHostUIHandler (consulte o artigo do MSDN no [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

```idl
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]
public interface IDocHostUIHandler
{
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowContextMenu(
        [In, MarshalAs(UnmanagedType.U4)] int dwID,
        [In] POINT pt,
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowUI(
        [In, MarshalAs(UnmanagedType.I4)] int dwID,
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,
        [In, MarshalAs(UnmanagedType.Interface)] object frame,
        [In, MarshalAs(UnmanagedType.Interface)] object doc);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int HideUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int UpdateUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ResizeBorder(
        [In] COMRECT rect,
        [In, MarshalAs(UnmanagedType.Interface)] object doc,
        bool fFrameWindow);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateAccelerator(
        [In] ref MSG msg,
        [In] ref Guid group,
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetOptionKeyPath(
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,
        [In, MarshalAs(UnmanagedType.U4)] int dw);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetDropTarget(
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateUrl(
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int FilterDataObject(
        IDataObject pDO,
        out IDataObject ppDORet);
    }
```

Opcionalmente, implemente a interface ICustomDoc (consulte o artigo do MSDN no [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Associe a classe que implementa o IDocHostUIHandler com o documento do WebOC. Se você implementou a interface ICustomDoc acima, então assim que a propriedade de documento do WebOC for válida, lance-a em um ICustomDoc e chame o método SetUIHandler, passando pela classe que implementa o IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Se você NÃO implementou a interface ICustomDoc, então assim que a propriedade de documento do WebOC for válida, `SetClientSite` você precisará lançá-la para um IOleObject e chamar o método, passando na classe que implementa o IDocHostUIHandler. Defina a bandeira DOCHOSTUIFLAG_DPI_AWARE no DOCHOSTUIINFO passada para a chamada do `GetHostInfo` método:

```csharp
public int GetHostInfo(DOCHOSTUIINFO info)
{
    // This is what the default site provides.
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;
    // Add the DPI flag to the defaults
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;
    return S_OK;
}
```

Isso deve ser tudo o que você precisa para obter o seu controle WebOC para suportar HPDI.

## <a name="tips"></a>Dicas

1. Se a propriedade do documento no controle weboc for alterada, talvez seja necessário reassociar o documento à classe IDocHostUIHandler.

2. Se o acima não funcionar, há um problema conhecido com o WebOC não pegar a alteração para a bandeira DPI. A maneira mais confiável de corrigir isso é alternar o zoom óptico do WebOC, o que significa duas chamadas com dois valores diferentes para a porcentagem de zoom. Além disso, se essa solução for necessária, pode ser necessário executá-la em cada chamada de navegação.

    ```csharp
    // browser2 is a SHDocVw.IWebBrowser2 in this case
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;
    if (cmdTarget != null)
    {
        object commandInput = zoomPercent;
        cmdTarget.Exec(IntPtr.Zero,
                       OLECMDID_OPTICAL_ZOOM,
                       OLECMDEXECOPT_DONTPROMPTUSER,
                       ref commandInput,
                       ref commandOutput);
    }
    ```
