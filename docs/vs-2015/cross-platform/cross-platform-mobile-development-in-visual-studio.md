---
title: Desenvolvimento móvel multiplataforma
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: 1efc8ea7f40c3098e681cc80ac90789b629630a9
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302486"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Desenvolvimento Móvel Multiplataforma no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

É possível criar aplicativos para dispositivos Android, iOS e Windows usando o Visual Studio.  Ao projetar seu aplicativo, use as ferramentas do Visual Studio para adicionar serviços conectados com facilidade, como Office 365, Serviço de Aplicativo do Azure e Application Insights.

 Compile seus aplicativos usando o C# e o .NET Framework, HTML e JavaScript ou o C++. Compartilhe código, cadeias de caracteres, imagens e, em alguns casos, até mesmo a interface do usuário.

 Se você desejar criar um jogo ou aplicativo gráfico imersivo, instale as ferramentas do Visual Studio para Unity e aproveite todos os recursos de produtividade avançados do Visual Studio com o Unity, o mecanismo popular de jogos/elementos gráficos multiplataforma e o ambiente de desenvolvimento para aplicativos executados no iOS, Android, Windows e em outras plataformas.

 **Neste artigo:**

- [Crie um aplicativo para Android, iOS e Windows (.NET Framework)](#NET)

  - [Segmente Android, iOS e Windows a partir de uma única base de código](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Ter dispositivos Windows 10 como destino](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Compilar um aplicativo para o Android, iOS e Windows (HTML/JavaScript)](#HTML)

- [Compilar um aplicativo para o Android e o Windows (C++)](#CPP)

- [Compilar um jogo multiplataforma para o Android, o iOS e o Windows usando as ferramentas do Visual Studio para Unity](#Unity)

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a><a name="NET"></a> Compilar um aplicativo para o Android, iOS e Windows (.NET Framework)
 ![Dispositivos](../cross-platform/media/homedevices.png "HomeDevices")

 Com o Xamarin, é possível ter o Android, iOS e Windows como destino na mesma solução, compartilhando o código e até mesmo a interface do usuário.

|**Saiba mais**|
|--------------------|
|[Instalar o Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Saiba mais sobre o Xamarin no Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio e Xamarin](../cross-platform/visual-studio-and-xamarin.md) (Biblioteca MSDN)|
|[ALM (Gerenciamento do Ciclo de Vida do Aplicativo) com aplicativos Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (Biblioteca MSDN)|
|[Saiba mais sobre aplicativos universais do Windows no Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Saiba mais sobre as semelhanças entre o Swift e o C#](https://aka.ms/scposter) (download.microsoft.com)|
|[Saiba mais sobre o Emulador do Visual Studio para Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a> Ter o Android, iOS e Windows como destino por meio de uma única base de código
 É possível criar aplicativos nativos para Android, iOS e Windows usando o C# ou o F# (no momento, não há suporte para o Visual Basic).  Para começar, instale o Visual Studio 2015, selecione a opção **Personalizado** do instalador e marque a caixa em **Desenvolvimento Móvel Multiplataforma > C#/.NET (Xamarin)**. Você também pode começar com o [Instalador do Xamarin](https://www.xamarin.com/download), que é necessário para instalar o Xamarin para Visual Studio 2013.

 Se você já tiver o Visual Studio 2015 instalado, execute o instalador por meio do **Painel de Controle > Programas e Recursos** e selecione a mesma opção **Personalizado** para o Xamarin acima.

 Quando terminar, os modelos de projeto aparecem na caixa de diálogo **Projeto** Novo. A maneira mais fácil de encontrar modelos do Xamarin é simplesmente pesquisar em “Xamarin”.

 O Xamarin expõe a funcionalidade nativa do Android, iOS e Windows como objetos do .NET. Assim, seus aplicativos têm acesso completo a APIs nativas e controles de usuário nativos e são tão dinâmicos quanto aplicativos escritos nas linguagens de plataforma nativa.

 Depois de criar um projeto, você aproveitará todos os recursos de produtividade do Visual Studio. Por exemplo, você usará um designer para criar suas páginas e o IntelliSense para explorar a API nativa das plataformas móveis. Quando estiver pronto para executar o aplicativo e ver a aparência dele, você poderá usar o Emulador do Visual Studio para Android ou o emulador do SDK do Android, executar aplicativos Windows nativamente ou executar aplicativos Windows no emulador do Windows Phone. Também é possível usar dispositivos Android e Windows vinculados diretamente. Para projetos do iOS, conecte-se a um Mac em rede e inicie o emulador de Mac no Visual Studio ou conecte-se a um dispositivo vinculado.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Criar um conjunto de páginas que são renderizadas em todos os dispositivos usando o Xamarin.Forms
 Dependendo da complexidade do design dos aplicativos, você pode considerar criá-lo usando os modelos do *Xamarin.Forms* no grupo **Aplicativos Móveis** dos modelos do projeto. O Xamarin.Forms é um kit de ferramentas de interface do usuário que permite criar uma única interface que pode ser compartilhada entre o Android, iOS e Windows.  Ao compilar uma solução do Xamarin.Forms, você terá um aplicativo Android, um aplicativo iOS e um aplicativo Windows. Para obter mais detalhes, consulte [Saiba mais sobre desenvolvimento móvel com o Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a> Compartilhar código entre aplicativos Android, iOS e Windows
 Se você não estiver usando o Xamarin.Forms e optar por criar cada plataforma individualmente, poderá compartilhar a maior parte do código não interface do usuário entre projetos de plataforma (Android, iOS e Windows). Isso inclui qualquer lógica de negócios, integração de nuvem, acesso a banco de dados ou qualquer outro código destinado ao .NET Framework. O único código que não é possível compartilhar é aquele destinado a uma plataforma específica.

 ![Compartilhar código entre Windows, iOs e Android UI's](../cross-platform/media/sharecode.png "ShareCode")

 Você pode compartilhar o código usando um projeto compartilhado, um projeto de Biblioteca de Classes Portátil ou ambos. Você pode achar que alguns códigos ficam melhores em um projeto compartilhado e outros em um projeto de Biblioteca de Classes Portátil.

|**Saiba mais**|
|--------------------|
|Escolha se deseja compartilhar o código usando projetos compartilhados, projetos de Biblioteca de Classes Portátil ou ambos.<br /><br /> [Compartilhando código entre plataformas](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (blog do .NET Framework)<br /><br /> [Opções de compartilhamento de código](/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [Opções de compartilhamento de código com o .NET Framework](https://msdn.microsoft.com/library/dn720832.aspx) (Biblioteca MSDN)|

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Destino aos dispositivos Windows 10
 ![Dispositivos Windows](../cross-platform/media/windowsdevices.png "WindowsDevices")

 Se você desejar criar um único aplicativo que se destina a toda a amplitude de dispositivos Windows 10, crie um aplicativo universal do Windows. Você criará o aplicativo usando um único projeto e as páginas serão renderizadas corretamente, independentemente de qual dispositivo é usado para exibi-las.

 Comece com um modelo de projeto de aplicativo universal do Windows. Crie as páginas visualmente e, em seguida, abra-as em uma janela de visualização para ver como são exibidas em vários tipos de dispositivos. Se você não gostar de como uma página é exibida em um dispositivo, poderá otimizá-la para que ela se ajuste melhor ao tamanho da tela, à resolução ou a várias orientações, como modo paisagem ou retrato. Você pode fazer tudo isso usando as janelas de ferramentas intuitivas e as opções de menu facilmente acessíveis no Visual Studio. Quando você estiver pronto para executar seu aplicativo e passar por seu código, você encontrará todos os emuladores e simuladores de dispositivos para diferentes tipos de dispositivos juntos em uma lista de paradas que está localizada na barra de ferramentas **Padrão.**

 O Windows 10 é relativamente novo e, portanto, você também encontrará modelos de projeto que têm como destino o Windows 8.1. É possível usar esses modelos de projeto, se desejar e seu aplicativo será executado em telefones, tablets e computadores Windows 10. No entanto, todos os dispositivos que executam o Windows 8.1 receberão uma atualização automática para o Windows 10; portanto, a menos que você tenha motivos específicos para ter o Windows 8.1 como destino, recomendamos o uso dos modelos de projeto que têm o Windows 10 como destino.

|**Saiba mais**|
|--------------------|
|[Saiba mais sobre aplicativos universais do Windows](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Centro de Desenvolvimento do Windows)|
|[Compilar seu primeiro aplicativo](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Centro de Desenvolvimento do Windows)|
|[Desenvolver aplicativos para a UWP (Plataforma Universal do Windows)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrar aplicativos para a UWP (Plataforma Universal do Windows)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Construa um aplicativo para Android, iOS e Windows (HTML/JavaScript)
 ![Dispositivos](../cross-platform/media/homedevices.png "HomeDevices")

 Se você for um desenvolvedor da Web e estiver familiarizado com HTML e JavaScript, poderá ter como destino o Windows, Android e iOS usando as Ferramentas do Visual Studio para Apache Cordova. Esses aplicativos podem se destinar a todas as três plataformas e você pode criá-los usando as habilidades e os processos com os quais você está mais familiarizado.

 O Apache Cordova é uma estrutura que inclui um modelo de plug-in. Esse modelo de plug-in fornece uma única API do JavaScript que pode ser usada para acessar as funcionalidades de dispositivo nativas de todas as três plataformas (Android, iOS e Windows).

 Como essas APIs são multiplataforma, é possível compartilhar a maior parte do que você escreve entre todas as três plataformas. Isso reduz os custos de desenvolvimento e manutenção. Além disso, não é necessário começar do zero. Se você criou outros tipos de aplicativos Web, poderá compartilhar os arquivos com o aplicativo Cordova sem precisar modificar ou criá-los novamente de alguma forma.

 ![Aplicativos híbridos de dispositivos multi&#45;](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Para começar, instale o Visual Studio 2015 e escolha o recurso **HTML/JavaScript (Apache Cordova)** durante a instalação. Se você estiver usando o Visual Studio 2013, instale a extensão Ferramentas do Visual Studio para Apache Cordova. De qualquer forma, as ferramentas do Cordova instalam automaticamente todos os softwares de terceiros necessários para criar seu aplicativo multiplataforma.

 Depois de instalar a extensão, abra o Visual Studio e crie um projeto **de Aplicativo em Branco (Apache Cordova).** Em seguida, é possível desenvolver seu aplicativo usando o JavaScript ou o Typescript. Também é possível adicionar plug-ins para estender a funcionalidade do aplicativo e as APIs de plug-ins são exibidas no IntelliSense à medida que o código é escrito.

 Quando estiver pronto para executar o aplicativo e executar o código em etapas, escolha um emulador, como o emulador Apache Ripple ou o Emulador do Visual Studio (Android ou Windows Phone), um navegador ou um dispositivo que você conectou diretamente ao computador. Em seguida, inicie o aplicativo. Se você estiver desenvolvendo seu aplicativo em um computador Windows, poderá até mesmo executá-lo nele. Todas essas opções são criadas no Visual Studio como parte das Ferramentas do Visual Studio para Apache Cordova.

 Modelos de projeto para a criação de aplicativos universais do Windows ainda estão disponíveis no Visual Studio. Portanto, sinta-se à vontade para usá-los se pretender ter somente dispositivos Windows como destino. Se você decidir ter como destino o Android e o iOS posteriormente, poderá portar o código para um projeto do Cordova. Há versões de software livre de WinJS APIs, para que você possa reutilizar qualquer código que utiliza essas APIs. Dito isso, se você pretende ter como destino outras plataformas no futuro, recomendamos começar com as Ferramentas do Visual Studio para Apache Cordova.

|**Saiba mais**|
|--------------------|
|[Instalar o Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Introdução às Ferramentas do Visual Studio para Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (taco.visualstudio.com)|
|[Saiba mais sobre o Emulador do Visual Studio para Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

## <a name="build-an-app-for-android-and-windows-c"></a><a name="CPP"></a>Construa um aplicativo para Android e Windows (C++)
 ![Use&#43;&#43; C para construir para Android, iOS e Windows](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 Primeiro, instale o Visual Studio 2015 e as ferramentas do Visual C++ para Desenvolvimento Móvel Multiplataforma. Em seguida, é possível criar um aplicativo de atividade nativa para o Android ou um aplicativo que se destina ao Windows. Modelos C++ que se destinam ao iOS ainda não estão disponíveis. É possível ter o Android e o Windows como destino na mesma solução, se desejar e, em seguida, compartilhar o código entre eles usando uma biblioteca compartilhada estática ou dinâmica multiplataforma.

 Se você precisar criar um aplicativo para o Android que precisa de algum tipo de manipulação avançada de elementos gráficos, como um jogo, poderá usar o C++ para fazer isso. Comece com o projeto **Aplicativo de Atividade Nativa (Android)**. Este projeto tem suporte completo na cadeia de ferramentas Clang.

 ![Modelo de projeto de atividade nativa](../cross-platform/media/cross-plat-cpp-native.png "Plat_CPP_Native")

 Quando estiver pronto para executar o aplicativo e ver a aparência dele, use o Emulador do Visual Studio para Android. É rápido, confiável e fácil de instalar e configurar.

 Você também pode criar um aplicativo que se destina a toda a amplitude de dispositivos Windows 10 usando o C++ e um modelo de projeto de aplicativo universal do Windows. Leia mais sobre isso na seção [Ter dispositivos Windows 10 como destino](#WindowsHTML) mostrada anteriormente neste tópico.

 É possível compartilhar o código C++ entre o Android e o Windows criando uma biblioteca compartilhada estática ou dinâmica.

 ![Bibliotecas estáticas e dinâmicas compartilhadas](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 É possível consumir essa biblioteca em um projeto do Windows ou do Android, como aqueles descritos anteriormente nesta seção. Você pode também consumi-la em um aplicativo compilado usando o Xamarin, Java ou qualquer linguagem que permite invocar funções em uma DLL não gerenciada.

 Ao escrever o código nessas bibliotecas, é possível usar o IntelliSense para explorar as APIs nativas das plataformas Android e Windows. Esses projetos de biblioteca são totalmente integrados com o depurador do Visual Studio, para que você defina pontos de interrupção, execute o código em etapas, encontre e corrija problemas usando todos os recursos avançados do depurador.

|**Saiba mais**|
|--------------------|
|[Baixe Visual Studio.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Instalar as ferramentas do Visual C++ para Desenvolvimento Móvel Multiplataforma.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Biblioteca MSDN)|
|[Saiba mais sobre como usar o C++ para ter várias plataformas como destino.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Instalar o que você precisa e, em seguida, criar um aplicativo de atividade nativa para Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Biblioteca MSDN)|
|[Saiba mais sobre o Emulador do Visual Studio para Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|
|[Saiba mais sobre o compartilhamento de código C++ com aplicativos Android e Windows](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[Exemplos de desenvolvimento móvel multiplataforma para C++](https://msdn.microsoft.com/library/dn707596.aspx) (Biblioteca MSDN)|
|[Exemplos adicionais de desenvolvimento móvel multiplataforma para C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a><a name="Unity"></a>Construa um jogo multiplataforma para Android, iOS e Windows usando ferramentas do Visual Studio para unity
 Visual Studio Tools for Unity é uma extensão gratuita para o Visual Studio que integra as poderosas ferramentas de edição, produtividade e depuração de códigos do Visual Studio com o *Unity*, o popular mecanismo de jogos/gráficos entre plataformas e ambiente de desenvolvimento para aplicativos imersivos que visam windows, iOS, Android e outras plataformas, incluindo a web.

 ![Ambiente de desenvolvimento VSTU](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Com o VSTU (Ferramentas do Visual Studio para Unity), é possível usar o Visual Studio para escrever scripts de jogo e editor em C# e, em seguida, usar seu depurador avançado para encontrar e corrigir erros. A última versão do VSTU traz suporte para o Unity 5 e inclui a coloração de sintaxe da linguagem de sombreador ShaderLab do Unity, melhor sincronização com o Unity, depuração mais avançada e geração de código aprimorada para o assistente MonoBehavior. O VSTU também leva seus arquivos de projeto do Unity, mensagens do console e a capacidade de iniciar seu jogo para o Visual Studio, para que você possa gastar menos tempo mudando do e para o Editor do Unity durante a escrita do código.

 Comece a criar seu jogo com o Unity e as Ferramentas do Visual Studio para Unity hoje mesmo.

|**Saiba mais**|
|--------------------|
|[Saiba mais sobre como criar jogos do Unity com o Visual Studio](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Leia mais sobre as Ferramentas do Visual Studio para Unity](../cross-platform/visual-studio-tools-for-unity.md) (Biblioteca MSDN)|
|[Começar a usar as Ferramentas do Visual Studio para Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (Biblioteca MSDN)|
|[Leia mais sobre as últimas melhorias à Visualização das Ferramentas do Visual Studio para Unity 2.0](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog do Visual Studio)|
|[Assista a um vídeo de introdução à Visualização das Ferramentas do Visual Studio para Unity 2.0](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (Vídeo)|
|[Saiba mais sobre o Unity](https://unity.com/) (site do Unity)|

## <a name="see-also"></a>Consulte Também

- [Adicione API's do Office 365 a um projeto do Visual Studio](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Serviços móveis do Azure](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)
