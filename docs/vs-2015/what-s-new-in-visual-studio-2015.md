---
title: Novidades no Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
caps.latest.revision: 364
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7065967ec86f7cde63c90de816fca95afce2171
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851496"
---
# <a name="what39s-new-in-visual-studio-2015"></a>Novidades no Visual Studio 2015
[!INCLUDE[vs2017banner](./includes/vs2017banner.md)]

Bem-vindo ao Visual Studio 2015, um pacote integrado de ferramentas de produtividade do desenvolvedor, de serviços de nuvem e de extensões que permitem que você e sua equipe criem ótimos aplicativos e jogos para a Web, para a Windows Store, para a área de trabalho, para Android e para iOS.

Esta página realça alguns dos recursos mais importantes que são novos desde a Visual Studio 2013 RTM, incluindo os recursos introduzidos pela primeira vez em uma das atualizações de Visual Studio 2013. Para obter uma lista completa do que há de novo no Visual Studio 2015, consulte as [notas de versão](https://www.visualstudio.com/news/vs2015-vs).

Para saber mais sobre os vários aprimoramentos e novos recursos do Visual Studio ALM, consulte [novidades do TFS 2015](/azure/devops/server/whats-new#tfs-2015).

## <a name="a-new-setup-experience"></a>Uma nova experiência de instalação
 [!INCLUDE[downloadvs](./includes/downloadvs-md.md)]

 A experiência de instalação do Visual Studio 2015 foi componented para que você só precise instalar as partes necessárias. Isso torna a instalação mais rápida para muitos cenários comuns que envolvem desenvolvimento em .NET ou Web. Se você fizer outros tipos de desenvolvimento, como o desenvolvimento móvel de plataforma cruzada, ou se trabalhar C++ no F#ou, escolha instalação **personalizada** e, em seguida, escolha os componentes e SDKs opcionais de terceiros necessários. Você também pode instalar qualquer um dos componentes personalizados mais tarde. Por exemplo, se você escolher instalação básica e tentar criar um novo C++ projeto, será solicitado que você baixe as ferramentas de C++ desenvolvimento.

 ![Caixa de diálogo de instalação do Visual Studio 2015](./ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

## <a name="sign-in-across-multiple-accounts"></a>Entrar através de várias contas
 Com o Visual Studio 2015, a nova experiência de entrada simplificada foi projetada para simplificar bastante o acesso a recursos online, mesmo quando você tem várias contas do Visual Studio. Depois de entrar no Visual Studio, você será automaticamente conectado a todas as instâncias do Visual Studio 2015 e do Blend em seu computador. Conectar-se automaticamente inicia as configurações de roaming para você. No Visual Studio 2015, sua conta é compartilhada entre recursos, desde que você tenha um bom token, você pode acessar suas contas de Visual Studio Team Services de **Team Explorer**e recursos e sites da sua assinatura do Microsoft Azure no Gerenciador de servidores. Você também verá os recursos do Azure na caixa de diálogo novo projeto para projetos de Application Insights e verá suas contas de [desenvolvedor](https://developer.salesforce.com/) do Azure Mobile, armazenamento do azure, [Microsoft Office 365](https://msdn.microsoft.com/office/aa905340.aspx) e Saleforce.com na caixa de diálogo novo **Adicionar um serviço conectado** .

 Você pode trabalhar com várias contas de usuário no Visual Studio adicionando-as à sua volta ou ao novo Gerenciador de contas. Em seguida, você pode alternar entre essas contas imediatamente ao conectar-se a serviços ou acessar recursos online. O Visual Studio lembra as contas adicionadas para que você possa usá-las de qualquer instância do Visual Studio ou do Blend. O Visual Studio também fará roaming da lista de contas (ainda que não vamos enmover suas credenciais valiosas) com sua conta de personalização para que você possa começar rapidamente a trabalhar com uma dessas contas em outro dispositivo. É claro que você pode remover contas da caixa de diálogo de configurações de conta a qualquer momento. Para começar, consulte [trabalhar com várias contas de usuário](./ide/work-with-multiple-user-accounts.md).

 ![Gerente de contas](./ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="choose-your-target-platforms"></a>Escolher sua (s) plataforma (ões) de destino
 O Visual Studio 2015 dá suporte ao desenvolvimento de dispositivos móveis de plataforma cruzada. Você pode escrever aplicativos e jogos destinados a iOS, Android e Windows e compartilhar uma base de código comum, tudo no IDE do Visual Studio. Você verá todos esses novos tipos de projeto na caixa de diálogo arquivo novo projeto.

 E, é claro, o suporte para aplicativos de área de trabalho clássicas é melhor do que nunca, com vários aprimoramentos em linguagens, bibliotecas e ferramentas.

### <a name="cross-platform-mobile-apps-in-c-with-xamarin-for-visual-studio"></a>Aplicativos móveis de plataforma cruzada C# no com Xamarin para Visual Studio
 O Xamarin é uma estrutura móvel que permite que você escreva código C# no que seja ligado nativamente às APIs do IOS e Android. A Microsoft estabeleceu uma parceria com o Xamarin em sua versão do Xamarin para Visual Studio, uma extensão que permite desenvolver para Android, iOS e Windows Phone em uma única solução com código compartilhado. Com o Xamarin, você usará uma linguagem e uma base de código com deltas mínimos entre as plataformas.  O Xamarin para Visual Studio tem suporte no Visual Studio 2010 e posterior. A edição inicial do Xamarin está incluída no Visual Studio 2015. Para começar, consulte [compilar aplicativos com interface do usuário nativa usando o Xamarin no Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md).

### <a name="cross-platform-mobile-apps-in-htmljavascript-with-apache-cordova"></a>Aplicativos móveis de plataforma cruzada em HTML/JavaScript com Apache Cordova
 Ferramentas do Visual Studio para Apache Cordova é o resultado da colaboração de fechamento entre a Microsoft e a comunidade de Apache Cordova de código aberto. As ferramentas permitem o desenvolvimento móvel de plataforma cruzada usando HTML, CSS e JavaScript (ou typescript). Você pode direcionar para Android, iOS e Windows com uma única base de código e aproveitar a riqueza do IDE do Visual Studio, incluindo JavaScript IntelliSense, explorador do DOM, console do JavaScript, pontos de interrupção, inspeções, locais, Apenas Meu Código e muito mais.  Com Ferramentas do Visual Studio para Apache Cordova, seus aplicativos têm acesso aos recursos do dispositivo nativo em todas as plataformas por meio de plug-ins que fornecem uma API JavaScript comum. Para começar, consulte Introdução [ao ferramentas do Visual Studio para Apache Cordova](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42).

### <a name="cross-platform-mobile-games-in-c-with-unity"></a>Jogos móveis de plataforma cruzada C# no Unity
 O Unity é uma plataforma amplamente usada para desenvolvimento de jogos 2D e 3D de várias plataformas. Você pode escrever seu jogo em C# e executá-lo nativamente no Android, iOS, Windows Phone e muitas outras plataformas. Ferramentas do Visual Studio para Unity é uma extensão que integra o Unity ao IDE do Visual Studio. Com essa extensão, você obtém todos os recursos do IDE do Visual Studio e do depurador, além de recursos de produtividade projetados para desenvolvedores do Unity. Ferramentas do Visual Studio para Unity 2,0 Preview 2 adiciona suporte para o Visual Studio 2015, além de vários novos recursos, como uma visualização melhor para objetos nas janelas locais e de inspeção. A Microsoft adquiriu recentemente SyntaxTree, os criadores de Ferramentas do Visual Studio para Unity. Para baixar Ferramentas do Visual Studio para Unity 2,0 Preview 2 e para obter mais informações sobre Ferramentas do Visual Studio para Unity, consulte [Ferramentas do Visual Studio para Unity 2,0](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad).

### <a name="cross-platform-apps-and-libraries-for-native-c"></a>Aplicativos e bibliotecas de plataforma cruzada para nativoC++
 C++o é um idioma disponível nativamente na maioria dos dispositivos móveis. Você pode usá-lo para escrever bibliotecas de código compartilhado entre plataformas que podem ser criadas para vários destinos da plataforma móvel. Você pode até mesmo criar aplicativos móveis inteiros C++no. O C++ Visual fornece as ferramentas para editar, compilar, implantar e depurar o código de plataforma cruzada. Além dos modelos para aplicativos do Windows, você pode criar projetos de modelos para aplicativos de atividade nativa do Android, aplicativos iOS ou projetos de biblioteca de código compartilhado para várias plataformas que incluem aplicativos do Xamarin híbrido. O IntelliSense específico da plataforma permite que você explore as APIs e gere o código correto para destinos do Android, iOS ou Windows. Você pode configurar sua compilação para plataformas x86 ou ARM nativo e implantar seu código em um simulador de iOS ou em dispositivos iOS em um Mac anexado à rede, para dispositivos Android conectados diretamente ou usar o Emulador do Microsoft Visual Studio para Android de alto desempenho para teste. Você pode definir pontos de interrupção, inspecionar variáveis, exibir a pilha e C++ percorrer o código no depurador do Visual Studio. Você pode compartilhar tudo, exceto o código mais específico da plataforma em várias plataformas de aplicativos, e compilar para todos eles com uma solução no Visual Studio.

 Para começar a usar a plataforma C++cruzada, consulte [criar aplicativos móveis de plataforma cruzada C++ com o Visual](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)

### <a name="universal-windows-apps-for-any-windows-10-device"></a>Aplicativos universais do Windows para qualquer dispositivo Windows 10
 Com a Plataforma Universal do Windows e nosso único núcleo do Windows, é possível executar o mesmo aplicativo em qualquer dispositivo Windows 10, de telefones a áreas de trabalho. Crie esses aplicativos Universais do Windows com o Visual Studio 2015 e as ferramentas de Desenvolvimento de Aplicativos Universais do Windows.

 ![Plataforma Universal do Windows](./cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 Execute seu aplicativo em um telefone Windows 10, área de trabalho do Windows 10 ou Xbox. É o mesmo pacote do aplicativo! Com a introdução do núcleo único e unificado do Windows 10, um pacote do aplicativo pode ser executado em todas as plataformas. Várias plataformas têm SDKs de Extensão que podem ser adicionados ao aplicativo para aproveitar comportamentos específicos à plataforma. Por exemplo, o SDK de uma extensão para dispositivos móveis manipula o botão Voltar pressionado em um Windows Phone. Se você referenciar um SDK de Extensão em seu projeto, basta adicionar verificações em runtime para testar se esse SDK está disponível nessa plataforma. É assim que você pode ter o mesmo pacote do aplicativo para cada plataforma!

 Use C#, Visual Basic C++ ou JavaScript para criar esses [aplicativos universais do Windows](https://msdn.microsoft.com/library/dn975273.aspx).

### <a name="web"></a>Web
 O ASP.NET 5 é uma importante atualização para MVC, WebAPI e Signalr, e é executado no Windows, Mac e Linux.  O ASP.NET 5 foi projetado desde o início para fornecer uma pilha .NET Lean e combinável para a criação de aplicativos modernos baseados em nuvem. As ferramentas do Visual Studio 2015 são mais bem integradas a ferramentas de desenvolvimento para a web populares, como Bower e Grunt. Para começar, consulte as várias Postagens de blog no [blog de ferramentas e desenvolvimento da Web de rede](https://devblogs.microsoft.com/aspnet/).

### <a name="classic-desktop-and-windows-store"></a>Área de trabalho clássica e Windows Store
 O Visual Studio 2015 continua a oferecer suporte à área de trabalho clássica e ao desenvolvimento da Windows Store. À medida que o Windows evolui, o Visual Studio irá evoluir junto com ele.  No Visual Studio 2015, as bibliotecas e linguagens para .NET, bem C++ como foram feitas avanços significativos que se aplicam a todas as versões do Windows.

#### <a name="the-net-framework"></a>O .NET Framework
 O Microsoft [!INCLUDE[net_v46](./includes/net-v46-md.md)] oferece cerca de 150 novas APIs e 50 APIs atualizadas para permitir mais cenários. Por exemplo, mais coleções agora implementam <xref:System.Collections.Generic.IReadOnlyCollection%601> tornando-as mais fáceis de usar. Além disso, o ASP.NET 5, mencionado anteriormente, oferece uma plataforma .NET Lean para a criação de aplicativos modernos baseados em nuvem.

 Os aplicativos da Windows Store C# escritos no .NET Framework podem agora aproveitar .net Native, que compilam aplicativos para código nativo em vez de Il, e [!INCLUDE[net_v46](./includes/net-v46-md.md)] também adiciona RyuJIT, um compilador JIT (just-in-time) de 64 bits.

 Os compiladores novos C# e VB ("Roslyn") aceleram significativamente os tempos de compilação e fornecem APIs abrangentes de análise de código. O Visual Studio 2015 aproveita o Roslyn para fornecer mais refatoração, incluindo renomeação embutido, analisadores e correções rápidas.

 As C# linguagens e Visual Basic contêm muitos aprimoramentos pequenos na linguagem principal e no suporte a IDE. Todos esses aprimoramentos se somam para tornar sua experiência de codificação .NET ainda mais intuitiva, conveniente e produtiva.

 Para obter mais informações, consulte [o que há de novo](https://msdn.microsoft.com/library/1d971dd7-10fc-4692-8dac-30ca308fc0fa) e o [blog do .net](https://devblogs.microsoft.com/dotnet/).

#### <a name="c"></a>C++
 O C++ Visual fornece avanços significativos em conformidade com o idioma c++ 11/14, suporte para desenvolvimento de dispositivo móvel multiplataforma, suporte para funções retomáveis e Await (atualmente planejado para padronização no c++ 17), melhorias e correções de bugs nas implementações C++ da biblioteca de tempo de execução C (CRT) e da STL (standard library), caixas de diálogo redimensionáveis no MFC, novas otimizações de compilador, melhor desempenho de compilação, novos recursos de diagnóstico e

 Para obter mais informações, consulte [What ' s New C++ for Visual](https://msdn.microsoft.com/library/1cc09fad-85a2-43c2-b022-bb99f5fe0ad7) and The [ C++ Visual blog](https://devblogs.microsoft.com/cppblog/).

## <a name="device-preview-menu-bar"></a>Barra de menus de visualização do dispositivo
 Em projetos Plataforma Universal do Windows, a barra de menu Visualização do dispositivo permite que você veja como sua interface do usuário baseada em XAML será renderizada em vários tamanhos de tela.

 ![Menu Visualização do dispositivo](./ide/media/vs2015-device-preview.png "vs2015_device_preview")

## <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos do Visual Studio
 Desde Visual Studio 2013, o Visual Studio Diagnóstico de Gráficos adicionou muitos recursos novos, incluindo análise de quadros, suporte a Windows Phone, edição de sombreador & aplicar e ferramentas de captura de linha de comando. Ele também adicionou suporte para depurar aplicativos DirectX12. Para obter mais informações, consulte [Visual Studio diagnóstico de gráficos](./debugger/visual-studio-graphics-diagnostics.md).

## <a name="connect-to-services"></a>Conectar aos serviços
 O Visual Studio 2015 torna mais fácil do que nunca conectar seu aplicativo aos serviços.  O assistente para adicionar novo serviço conectado configura seu projeto, adiciona o suporte de autenticação necessário e baixa os pacotes NuGet necessários para que você comece a codificar em seu serviço de forma rápida e sem complicações. O assistente para adicionar serviço conectado também se integra ao novo Gerenciador de contas para facilitar o trabalho com várias contas de usuário e assinaturas. No Visual Studio 2015, o suporte para os seguintes serviços é fornecido prontamente (supondo que você tenha uma conta):

1. Serviços móveis do Azure

2. Armazenamento do Azure

3. Office 365 (email, contatos, calendários, arquivos, usuários & grupos)

4. Salesforce

   Novos serviços serão adicionados continuamente e você poderá descobri-los clicando no link "localizar novos serviços" no assistente.

   ![Caixa de diálogo Adicionar serviços conectados](./ide/media/vs2015-addconnectedservicedialog.png "VS2015_AddConnectedServiceDialog")

## <a name="design-your-ui"></a>Criar sua interface do usuário
 A experiência de fusão para a criação de interfaces de usuário XAML foi significativamente aprimorada. O Blend foi completamente reprojetado para fornecer uma interface do usuário mais intuitiva, recursos de edição XAML mais eficientes, incluindo o IntelliSense, e melhor integração com o Visual Studio. Consulte [Criando o XAML no Visual Studio e no Blend para Visual Studio](./designers/designing-xaml-in-visual-studio.md) para obter mais informações.

## <a name="cross-platform-debugging-support"></a>Suporte à depuração entre plataformas
 Você pode usar o Visual Studio para criar e depurar aplicativos móveis nativos que são executados em dispositivos Windows, iOS e Android. Use o [emulador do Visual Studio para Android](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/)ou conecte um dispositivo e depure seu código diretamente no Visual Studio.

- **JavaScript/Cordova**. Use o [Ferramentas do Visual Studio para Apache Cordova](https://msdn.microsoft.com/library/dn879821\(v=vs.140\).aspx) para compilar aplicativos nativos para Windows, Ios e Android com JavaScript.

     [Depure seu aplicativo](https://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1) na biblioteca MSDN é uma visão detalhada do suporte à depuração do Visual Studio para Cordova.

- **C# /Xamarin**. Use o [Xamarin](https://msdn.microsoft.com/library/dn879698\(v=vs.140\).aspx) para criar aplicativos nativos para Windows, Ios e Android no Visual Studio com C#o.

     A [depuração](https://docs.microsoft.com/xamarin/ios/deploy-test/debugging-in-xamarin-ios?tabs=windows) (Ios) e a [depuração no dispositivo](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-device?tabs=windows) nos [guias de desenvolvedor do Xamarin](https://docs.microsoft.com/xamarin/) descrevem a experiência de depuração.

- **C++ /Android**. Use o [Visual C++ para modelos de desenvolvimento móvel de plataforma cruzada](cross-platform/visual-cpp-for-cross-platform-mobile-development.md) junto com ferramentas de terceiros como o [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html) para criar aplicativos nativos para Windows e Android.

## <a name="debugging-and-diagnostics"></a>Depuração e Diagnóstico

Para obter informações sobre as novidades do diagnóstico, consulte [novidades do ferramentas de criação de perfil](./profiling/what-s-new-in-profiling-tools.md).

A seguir estão as ferramentas novas ou aprimoradas que executam diferentes tipos de diagnóstico e análise em seu código:

### <a name="perftips"></a>PerfTips
 PerfTips exibem o tempo de execução dos métodos durante a depuração, permitindo que você identifique rapidamente os afunilamentos sem precisar invocar o criador de perfil. Para começar, consulte [PerfTips: informações de desempenho imediatas durante depuração com o Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)

### <a name="error-list"></a>Lista de Erros
 A lista de erros agora dá suporte à filtragem em qualquer coluna. Ele também mostra uma exibição dinâmica de erros, avisos e análise de código em toda C# a sua solução ou Visual Basic à medida que você digita, mesmo quando uma alteração de código produz milhares de avisos. O novo Lista de Erros é de back-Compatible com o uso existente. Para obter mais informações, consulte [lista de erros janela](./ide/reference/error-list-window.md).

### <a name="gpu-usage-tool"></a>Ferramenta de uso de GPU
 A ferramenta de uso de GPU ajuda a coletar e analisar dados de uso de GPU em aplicativos e jogos do DirectX e a solucionar problemas de gargalos de desempenho na CPU ou GPU. Para começar a usar a ferramenta, consulte a [postagem no blog da C++ equipe Visual](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/).

## <a name="live-code-analysis-light-bulbs"></a>Análise de código ao vivo (lâmpadas)
 O novo compilador Roslyn para C# e Visual Basic não apenas oferece tempos de compilação mais rápidos — ele também permite cenários completamente novos, como a análise de código ao vivo, que fornece comentários avançados e personalizáveis e sugestões diretamente dentro do editor de códigos conforme você digita. No Visual Studio 2015, lâmpadas leves são exibidas na margem esquerda (ao usar o teclado) ou uma dica de ferramenta (ao focalizar um erro com o mouse). A lâmpada diz em tempo real que o compilador (possivelmente usando um conjunto de regras personalizado) detectou um problema em seu código e também tem uma sugestão de como corrigir o problema. Quando você vir uma lâmpada, clique nela para obter sugestões acionáveis.

 ![Lâmpadas no editor de Visual Studio Code](./ide/media/vs2015-lightbulbs.png "VS2015_LightBulbs")

## <a name="enjoy-these-additional-ide-improvements"></a>Aproveite essas melhorias de IDE adicionais

### <a name="synchronized-settings-roaming-settings"></a>Configurações sincronizadas (configurações de roaming)
 Visual Studio 2013 introduziu configurações sincronizadas para algumas das configurações mais comumente definidas, como editor de texto, associações de teclas, fontes de & de tema & cores, inicialização e aliases de ambiente.  O Visual Studio 2015 aprimora essa experiência sincronizando mais de suas configurações e sincronizando as configurações na família de aplicativos Visual Studio, como Professional, Enterprise, Express SKUs e Blend. Ao entrar no Visual Studio 2015 pela primeira vez com a mesma conta usada no Visual Studio 2013, você verá as configurações sincronizadas aplicadas de Visual Studio 2013. Você pode acessar suas configurações digitando "sincronizar" no **início rápido**ou navegando até **ferramentas > opções > ambiente > configurações sincronizadas**.

### <a name="automatic-extension-updates"></a>Atualizações automáticas de extensão
 Suas extensões do Visual Studio instaladas agora serão atualizadas automaticamente quando uma nova versão estiver disponível na galeria do Visual Studio. Consulte [localizando e usando as extensões do Visual Studio](./ide/finding-and-using-visual-studio-extensions.md) para obter detalhes sobre como você pode personalizar as atualizações de extensão automáticas.

### <a name="title-case-menus"></a>Menus de casos de título
 Você falou, nós ouvimos. Os menus do Visual Studio são, mais uma vez, o caso de título, por padrão. No entanto, se você gostar do estilo ALL CAPS, poderá defini-lo na inicialização ou na página **ferramentas > opções > geral** de propriedades:

 ![Comandos do menu principal de caso de título do Visual Studio 2015](./ide/media/vs2015-mainmenu.png "VS2015_MainMenu")

### <a name="high-resolution-images-and-touch-support"></a>Imagens de alta resolução e suporte ao toque
 O IDE do Visual Studio agora tem imagens reais de alta resolução em exibições mais densas (em áreas como menus, menus de contexto, barras de comando da janela de ferramentas e em alguns projetos no Gerenciador de Soluções). E, em uma tela sensível ao toque na janela do editor de código do Visual Studio, agora você pode usar gestos como tocar e segurar, pinçar, tocar e assim por diante para aplicar zoom, rolar, selecionar texto e invocar menus de contexto.

 ![Suporte ao touch no editor](./ide/media/vs2015-touchsupport.png "VS2015_TouchSupport")

### <a name="custom-layouts"></a>Layouts personalizados
 Você pode criar layouts de janela personalizada de armazenamento e roaming. Por exemplo, você pode definir um layout preferencial para uso em seu computador desktop e um layout diferente para uso em um laptop ou dispositivo de tela pequena. Ou você pode preferir um layout para um projeto de interface do usuário e outro para um projeto de banco de dados. As associações de chave permitem alternar rapidamente entre layouts. Esses layouts estão disponíveis em qualquer instância do Visual Studio quando você está conectado. Para obter mais informações, consulte [criar layouts de janela personalizados](./misc/create-custom-window-layouts.md).

 ![Item de menu de layout personalizado do Visual Studio](./ide/media/vs2015-customlayout.png "VS2015_CustomLayout")

### <a name="notification-hub"></a>Hub de notificação
 A interface do usuário do hub de notificação foi simplificada para facilitar a verificação rapidamente. Tipos adicionais de notificações foram adicionados, incluindo problemas de desempenho, problemas de renderização e falhas, e agora você pode informar ao Visual Studio para parar de mostrar uma notificação. Para obter mais informações, consulte [Notificações do Visual Studio](./ide/visual-studio-notifications.md).

### <a name="codelens-find-what-happened-to-your-code-enterprise-and-professional-editions-only"></a>CodeLens: Encontre o que aconteceu com seu código (somente nas edições Enterprise e Professional)
 Fique concentrado em seu trabalho enquanto você encontra informações sobre seu código, sem sair do editor. Você pode examinar as alterações e outros históricos de itens de trabalho, bugs, revisões de código e assim por diante para o código armazenado no Visual Studio Team Services (VSTS) ou no Team Foundation Server (TFS).

 Em Visual Studio Enterprise e Visual Studio Professional, agora você pode:

- Obtenha o histórico de um arquivo de código inteiro no editor do Visual Studio.

   ![CodeLens: obter detalhes do arquivo de código](./ide/media/codelensfilelevel.png "CodeLensFileLevel")

- Consulte um grafo que mostra as pessoas que alteraram seu código. Isso pode ajudá-lo a encontrar padrões nas alterações da sua equipe e avaliar o impacto delas.

   ![CodeLens: consulte o histórico de alterações de código como um grafo](./ide/media/codelens.png "CodeLens")

- Veja facilmente quando seu código foi alterado pela última vez.

- Localize alterações em outras ramificações que afetam seu código.

  Consulte [CodeLens](./ide/find-code-changes-and-other-history-with-codelens.md).

### <a name="design-and-modeling-tools-enterprise-edition-only"></a>Ferramentas de design e modelagem (somente Enterprise Edition)
 **Mapas de código e gráficos de dependência**

 Em Visual Studio Enterprise, quando você quiser entender dependências específicas em seu código, visualize-as criando mapas de código. Assim, você pode navegar entre essas relações usando o mapa que aparece ao lado do código. Os mapas de código também podem ajudar a saber em que parte do código você está enquanto trabalha ou depura código, para que seja necessário ler menos código enquanto examina o design do código.

 Nesta versão, fizemos os menus de atalho para elementos de código e links muito mais fáceis de usar agrupando comandos em seções relacionadas à seleção, edição, gerenciamento de grupos e alteração do layout do conteúdo do grupo. Observe também que os projetos de teste são exibidos em um estilo diferente de outros projetos e que atualizamos os ícones de elementos no mapa para versões mais adequadas.

 ![Mostrar itens selecionados em um novo mapa de código](./ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Outros aprimoramentos incluem:

- **Diagramas de cima para baixo melhorados**. Para soluções médias a grandes do Visual Studio, agora você pode usar um menu de arquitetura simplificado para obter mapas de códigos mais eficientes para sua solução. Os assemblies da solução são agrupados pelas pastas da solução para que você possa vê-los no contexto e usufruir do esforço que empregou para estruturar a solução. Você verá imediatamente referências de projeto e assembly e, em seguida, aparecerão os tipos de link. Além disso, os assemblies que estiverem externos à solução serão agrupados de uma maneira mais compacta.

- **Os projetos de teste têm estilo diferente e podem ser filtrados**. Agora você pode identificar projetos de teste com mais facilidade e rapidez no MAP, pois eles têm um estilo diferente. Eles também podem ser filtrados para que você possa se concentrar no código de trabalho do aplicativo.

- **Links de dependência externa simplificados**. Os links de dependência não representam mais a herança de System.Object, System.ValueType, System.Enum e System.Delegate, o que facilita a visualização das dependências externas no mapa de códigos.

- **O 'Aprofundamento nos links de dependência' leva os filtros em consideração**. Você obtém um diagrama simples e útil quando o expande para compreender as contribuições a um link de dependência. O diagrama é menos desorganizado e leva em consideração as opções de filtragem de link que você selecionou.

- **Os elementos de código são adicionados a um mapa de código com seus contextos**. Como os diagramas agora aparecem com contexto (até o assembly e a pasta de solução, que podem ser filtrados, se necessário), você pode obter diagramas mais eficientes ao arrastar e soltar elementos de código do Gerenciador de Soluções, do Modo de Exibição de Classe e do Pesquisador de Objetos ou ao solicitar elementos no Gerenciador de Soluções e escolher Exibir no Mapa de Códigos.

- **Obtenha mapas de código reativos mais rapidamente**. As operações de arrastar e soltar produzem um resultado imediato, e os links entre os nós são criados com muito mais rapidez, sem afetar as operações posteriores iniciadas pelo usuário, como expandir um nó ou solicitar mais nós. Quando você cria mapas de código sem compilar a solução, todos os casos de canto, como quando os assemblies não são compilados, são agora compilados.

- **Ignorar a recriação da sua solução.** Fornece melhor desempenho ao criar e editar diagramas.

- **Filtrar nós e grupos de elemento de código**. Você pode organizar rapidamente seus mapas ao exibir ou ocultar elementos de código com base na categoria e ao agrupar elementos de código por pastas de solução, assemblies, namespaces, pastas de projeto e tipos.

- **Filtre relações para tornar os diagramas mais fáceis de ler**. Agora, a filtragem de links também se aplica a links de grupos cruzados, o que torna o trabalho com a janela de filtros menos intrusivo do que era nas versões anteriores.

- **Criar diagramas do Modo de Exibição de Classe e do Pesquisador de Objetos**. Arraste e solte arquivos e assemblies em um mapa novo ou existente nas janelas Modo de Exibição de Classe e Pesquisador de Objetos.

  Consulte [mapear dependências em suas soluções](./modeling/map-dependencies-across-your-solutions.md).

  **Outras alterações de design e modelagem nesta versão:**

- **Diagramas de camada**. Atualize esses diagramas usando Modo de Exibição de Classe e pesquisador de objetos. Para atender aos requisitos de design de software, use diagramas de camada para descrever as dependências desejadas para seu software. Mantenha o código consistente com esse design encontrando um código que não atenda a essas restrições e validando código futuro com essa linha de base.

- **Diagramas de UML**. Não é mais possível criar diagramas de classe UML e diagramas de sequência por meio do código. Mas ainda é possível criar esses diagramas usando novos elementos UML.

- **Architecture Explorer**. Não é mais possível usar o Architecture Explorer para criar diagramas. Mas ainda é possível usar o Gerenciador de Soluções.

## <a name="visual-studio-extensibility-tools"></a>Ferramentas de Extensibilidade do Visual Studio
 Nunca foi tão fácil instalar o Ferramentas de Extensibilidade do Visual Studio (SDK do VS e modelos), pois eles agora são incluídos como um componente opcional durante a instalação.  As ferramentas de extensibilidade permitem que os desenvolvedores gravem extensões para personalizar e adicionar recursos ao Visual Studio. Para obter mais informações sobre a extensibilidade do Visual Studio, consulte [Visual Studio SDK](./extensibility/visual-studio-sdk.md)

 Se você quiser incluir as ferramentas de extensibilidade com sua instalação personalizada, poderá encontrá-las em **recursos/ferramentas comuns/ferramentas de extensibilidade do Visual Studio**.  Você também pode instalar as ferramentas de extensibilidade em um momento posterior abrindo a caixa de diálogo **novo projeto** e selecionando o item **instalar ferramentas de extensibilidade do Visual Studio** em  **C# Visual/extensibilidade**.

## <a name="please-give-feedback"></a>Forneça comentários
 Por que enviar comentários à equipe do Visual Studio? Porque nós levamos a sério os comentários dos clientes. Na verdade, revisamos cada parte dos comentários que entram em nosso sistema de comentários. Seus comentários impulsionam muito o que fazemos.

### <a name="send-a-smile"></a>Enviar um sorriso
 Informando o que você gosta nos ajuda a entender quando atendemos ou superamos suas expectativas. Quando estamos projetando e implementando novos recursos, usamos dados sobre os recursos que você deseja para ajudar com nossas decisões de design. Portanto, se você gostar de um recurso no Visual Studio, conte-nos sobre ele. É fácil e você pode fazê-lo diretamente de dentro do IDE.

 Basta clicar no rosto de Smiley amarelo na barra de título, nos dizer o que você gostou e clicar no botão **enviar um Smiley** .

 Isso é tudo! Vamos rotear seus comentários para a equipe correta onde eles se desaparecerão em seguida, começará rapidamente a pensar nas maneiras de fascinam-lo ainda mais.

### <a name="send-a-frown"></a>Enviar um Rosto Triste
 Ouvir onde precisamos fazer melhorias no produto nos ajuda a gerenciar nossa lista de pendências concentrando-se primeiro nas coisas mais importantes para nossos clientes. Se houver algo que esteja sendo depurado, conte-nos sobre ele usando o recurso **enviar um rosto triste** diretamente dentro do IDE. Também fizemos isso um processo extremamente simples:

 Clique no rosto de Smiley amarelo na barra de título e, em seguida, clique em **enviar um rosto triste**. Diga-nos o que você não gostou e clique no botão enviar um rosto triste. Para obter mais informações, consulte [Fale conosco](./ide/talk-to-us.md).

### <a name="report-crashes-hangs-and-performance-issues"></a>Relatar falhas, travamentos e problemas de desempenho
 Às vezes, uma observação rápida em um cara só não é suficiente para transmitir o impacto total de algo que você não gosta. Para os momentos em que há um problema de interrupção, falha ou desempenho, você pode compartilhar facilmente etapas de reprodução, despejos de memória e arquivos de rastreamento usando a caixa de diálogo que é exibida depois de enviar um rosto triste.

 Primeiro, envie um rosto triste conforme descrito acima. Na caixa de diálogo exibida, você pode marcar seus comentários com uma das marcas padrão ou criar sua própria marca. As marcas nos ajudam a rotear seus comentários para a equipe de recursos apropriada. Na lista suspensa **escolher uma categoria** , selecione a opção que representa o problema que você está relatando e siga as etapas para reproduzir o problema. Também estão disponíveis etapas detalhadas sobre como usar o Visual Studio para relatar comentários. Para obter mais informações, consulte [o Visual Studio enviar instruções de Smiley](https://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b).

## <a name="see-also"></a>Veja também

* [Criar aplicativos multiplataforma com o Apache Cordova](https://msdn.microsoft.com/library/34d3c1be-22b3-4812-97fb-10b4e8ad2134)
* [Criar aplicativos com interface do usuário nativa usando o Xamarin no Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)
* [Compilar aplicativos de plataforma cruzada com o Visual C++](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)
* [Gerar testes de unidade para seu código com IntelliTest](./test/generate-unit-tests-for-your-code-with-intellitest.md)
* [Trabalhar com várias contas de usuário](./ide/work-with-multiple-user-accounts.md)
* [Criar layouts de janela personalizados](./misc/create-custom-window-layouts.md)
* [Realizar ações rápidas com lâmpadas](./ide/perform-quick-actions-with-light-bulbs.md)
* [Novidades no Visual Studio 2017](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)
