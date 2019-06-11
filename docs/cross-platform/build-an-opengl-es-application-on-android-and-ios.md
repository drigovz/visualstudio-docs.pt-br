---
title: Compilar um aplicativo OpenGL ES em Android e iOS | Microsoft Docs
ms.custom: ''
ms.date: 05/16/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: aa8ffe308f8a1181ed18af52ba7537c46007de94
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317644"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Criar um aplicativo OpenGL ES no Android e iOS

Você pode criar soluções e projetos do Visual Studio para aplicativos iOS e Android que compartilhem código comum. Este artigo o conduz pelo modelo de solução que cria tanto um aplicativo iOS simples quanto um aplicativo de Atividade Nativa do Android. Os aplicativos têm código C++ em comum que usa o OpenGL ES para exibir o mesmo cubo de rotação animado em cada plataforma. O OpenGL ES (GLES [OpenGL para Sistemas Incorporados]) é uma API gráfica 2D e 3D que tem suporte em vários dispositivos móveis.

## <a name="requirements"></a>Requisitos

Antes de criar um aplicativo OpenGL ES para iOS e Android, verifique se todos os requisitos do sistema foram atendidos. Se este não for o caso, instale a carga de trabalho do Desenvolvimento Móvel com C++ no Instalador do Visual Studio. Para criar para iOS, inclua as ferramentas opcionais de desenvolvimento de iOS para C++. Para criar para Android, instale as ferramentas de desenvolvimento do Android para C++ e as ferramentas de terceiros necessárias: Android NDK, Apache Ant, Google Android Emulator e Intel Hardware Accelerated Execution Manager. Em seguida, configure o Intel HAXM e o Android Emulator para serem executados no seu sistema. Para saber mais e obter instruções detalhadas, confira [Instalar o Visual C++ para desenvolvimento móvel de plataforma cruzada](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Para compilar e testar o aplicativo iOS, você precisará de um computador Mac configurado de acordo com as instruções de instalação. Para saber mais sobre como configurar para desenvolvimento do iOS, confira [Instalar e configurar ferramentas para compilar usando iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)

## <a name="create-a-new-opengles-application-project"></a>Criar um projeto de aplicativo OpenGLES

Neste tutorial, primeiro você criará um novo projeto de Aplicativo OpenGL ES e, em seguida, compilará e executará o aplicativo padrão no Emulador do Visual Studio para Android. Em seguida, você cria o aplicativo para iOS e executa o aplicativo em um dispositivo iOS.

1. No Visual Studio, escolha **Arquivo** > **Novo** > **Projeto**.

1. Na caixa de diálogo **Novo Projeto**, em **Modelos**, escolha **Visual C++**  > **Multiplataforma** e, em seguida, escolha o modelo **Aplicativo OpenGLES (Android, iOS)** .

1. Nomeie o aplicativo como `MyOpenGLESApp` e, em seguida, escolha **OK**.

   ![Novo projeto de Aplicativo OpenGLES](../cross-platform/media/cppmdd_opengles_newproj.PNG "CPPMDD_OpenGLES_NewProj")

   O Visual Studio cria a nova solução e abre o Gerenciador de Soluções.

   ![MyOpenGLESApp no Gerenciador de Soluções](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

   A nova solução de Aplicativo OpenGL ES inclui três projetos de biblioteca e dois projetos de aplicativo. A pasta de Bibliotecas inclui um projeto de código compartilhado e dois projetos específicos da plataforma que fazem referência ao código compartilhado:

- `MyOpenGLESApp.Android.NativeActivity` contém as referências e o código de cola que implementa seu aplicativo como uma Atividade Nativa no Android. Os pontos de entrada do código de associação são implementados em *main.cpp*, que inclui o código compartilhado comum em `MyOpenGLESApp.Shared`. Os cabeçalhos pré-compilados estão em *pch.h*. Esse projeto de aplicativo de Atividade Nativa é compilado em um arquivo ( *.so*) de biblioteca compartilhada que é obtido pelo projeto de `MyOpenGLESApp.Android.Packaging`.

- `MyOpenGLESApp.iOS.StaticLibrary` cria um arquivo ( *.a*) da biblioteca estática do iOS que contém o código compartilhado no `MyOpenGLESApp.Shared`. Ele está vinculado ao aplicativo criado pelo projeto `MyOpenGLESApp.iOS.Application`.

- `MyOpenGLESApp.Shared` contém o código compartilhado que funciona em várias plataformas. Ele utiliza macros de pré-processador para compilação condicional do código específico da plataforma. O código compartilhado é escolhido pela referência de projeto no `MyOpenGLESApp.Android.NativeActivity` e no `MyOpenGLESApp.iOS.StaticLibrary`.

A solução tem dois projetos para compilar aplicativos para as plataformas Android e iOS:

- `MyOpenGLESApp.Android.Packaging` cria o arquivo *.apk* para implantação em um emulador ou dispositivo Android. Esse arquivo contém os recursos e o arquivo AndroidManifest.xml no qual as propriedades do manifesto são definidas. Também contém o arquivo *build.xml* que controla o processo de build Ant. Ele é definido como o projeto de inicialização por padrão, para que possa ser implantado e executado diretamente no Visual Studio.

- **MyOpenGLESApp.iOS.Application** contém os recursos e o código de associação Objective-C para criar um aplicativo iOS vinculado ao código de biblioteca estática C++ em `MyOpenGLESApp.iOS.StaticLibrary`. Esse projeto cria um pacote de build que é transferido para seu Mac pelo Visual Studio e pelo agente remoto. Quando você compila este projeto, o Visual Studio envia os arquivos e os comandos para compilar e implantar seu aplicativo no Mac.

## <a name="build-and-run-the-android-app"></a>Criar e executar o aplicativo Android

A solução criada pelo modelo define o aplicativo Android como o projeto padrão.  Você pode compilar e executar esse aplicativo para verificar sua instalação e configuração. Para um teste inicial, execute o aplicativo em um dos perfis de dispositivo instalados pelo emulador para Android. Se você preferir testar seu aplicativo em outro destino, poderá carregar o emulador de destino ou conectar o dispositivo ao computador.

### <a name="to-build-and-run-the-android-native-activity-app"></a>Para compilar e executar o aplicativo de Atividade Nativa Android

1. Se ainda não estiver selecionado, escolha **x86** na lista suspensa **Plataformas da Solução**.

   ![Definir a Plataforma de Solução como x86](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")

   Use x86 para ter o emulador como destino. Para ter um dispositivo como destino, escolha a plataforma de solução com base no processador do dispositivo. Se a lista **Plataformas da Solução** não for exibida, escolha **Plataformas da Solução** na lista **Adicionar/Remover Botões** e, em seguida, escolha sua plataforma.

1. No **Gerenciador de Soluções**, abra o menu de atalho do projeto `MyOpenGLESApp.Android.Packaging` e, em seguida, escolha **Compilar**.

   ![Compilar um projeto de empacotamento Android](../cross-platform/media/cppmdd_opengles_andbuild.png "CPPMDD_OpenGLES_AndBuild")

   A janela Saída exibe a saída do processo de build para a biblioteca compartilhado Android e o aplicativo Android.

   ![Saída de build para projetos Android](../cross-platform/media/cppmdd_opengles_andoutput.png "CPPMDD_OpenGLES_AndOutput")

1. Escolha um dos perfis de dispositivos Android emulados como seu destino de implantação.

   ![Escolha o destino da implantação](../cross-platform/media/cppmdd_opengles_pickemulator.png "CPPMDD_OpenGLES_PickEmulator")

   Se você tiver instalado outros emuladores ou conectado um dispositivo Android, poderá escolhê-los na lista suspensa de destino de implantação. Para executar o aplicativo, a Plataforma de Solução compilada deverá corresponder à plataforma do dispositivo de destino.

1. Pressione F5 para iniciar a depuração ou Shift+F5 para iniciar sem depuração.

   O Visual Studio inicia o emulador, que leva vários segundos para carregar e implantar o código. Confira aqui como o aplicativo aparece no emulador:

   ![Aplicativo em execução no Emulador do Android](../cross-platform/media/cppmdd_opengles_andemulator.png "CPPMDD_OpenGLES_AndEmulator")

   Quando o aplicativo tiver sido iniciado, você poderá definir pontos de interrupção e usar o depurador para executar o código em etapas, examinar os locais e inspecionar os valores.

1. Pressione **Shift**+**F5** para parar a depuração.

   O emulador é um processo separado que continua sendo executado. É possível editar, compilar e implantar o código várias vezes no mesmo emulador. Seu aplicativo aparece na coleção de aplicativo no emulador e pode ser iniciado diretamente de lá.

   Os projetos de biblioteca e o aplicativo de Atividade Nativa do Android gerados colocam o código C++ compartilhados em uma biblioteca dinâmica que inclui o código de "associação" para fazer interface com a plataforma Android. A maioria do código do aplicativo está na biblioteca e o manifesto, os recursos e as instruções de build estão no projeto de empacotamento. O código compartilhado é chamado de main.cpp no projeto NativeActivity. Para obter mais informações sobre como programar uma Atividade Nativa do Android, consulte a página [Conceitos](https://developer.android.com/ndk/guides/concepts.html) do NDK do Android Developer.

   O Visual Studio compila projetos de Atividade Nativa do Android usando o NDK do Android, que usa Clang como o conjunto de ferramentas de plataforma. O Visual Studio mapeia as propriedades no projeto NativeActivity para as opções usadas para compilar, vincular e depurar na plataforma de destino. Para obter detalhes, abra a caixa de diálogo **Páginas de Propriedade** para o projeto MyOpenGLESApp.Android.NativeActivity. Para saber mais sobre as opções de linha de comando, consulte o [Manual do usuário do compilador Clang](http://clang.llvm.org/docs/UsersManual.html).

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>Criar e executar o aplicativo iOS em um dispositivo iOS

O projeto de aplicativo iOS é criado e editado no Visual Studio, porém, devido a restrições de licença, deve ser compilado e implantado em um Mac. O Visual Studio comunica-se com um agente remoto em execução no Mac para transferir arquivos de projeto e executar comandos de build, implantação e depuração. Instale e configure seu Mac e o Visual Studio para comunicação antes de compilar o aplicativo iOS. Para obter instruções detalhadas, confira [Instalar e configurar as ferramentas para compilar usando iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Depois que o agente remoto estiver em execução no Mac e emparelhado com o Visual Studio, você poderá compilar e executar o aplicativo iOS para verificar sua instalação e configuração.

Para implantar um aplicativo iOS em um dispositivo iOS, você também deve configurar a assinatura automática no Xcode no Mac. A assinatura automática gerencia automaticamente a assinatura de aplicativos e cria um perfil de provisionamento para assinar uma compilação do aplicativo.

### <a name="to-set-up-automatic-signing-on-xcode"></a>Para configurar a assinatura automática no Xcode

1. Se ainda não o fez, instale o [Xcode](https://developer.apple.com/xcode/downloads/) versão 10.2.1 ou posterior no seu Mac.

1. Abra o aplicativo Xcode no seu Mac.

1. Crie um novo projeto Xcode **Aplicativo de Modo de Exibição Único**. Preencha os campos obrigatórios durante a criação do projeto. Os valores podem ser arbitrários, pois o projeto é usado apenas para criar um perfil de provisionamento usado posteriormente para assinar uma compilação do aplicativo.

1. Adicione sua ID da Apple que está inscrita em uma conta do [Programa de Desenvolvedor da Apple](https://developer.apple.com/programs/) no Xcode. Sua ID da Apple é usada como uma identidade de assinatura para assinar aplicativos. Para adicionar a identidade de assinatura no Xcode, abra o menu do **Xcode** e escolha **Preferências**. Selecione **Contas** e clique no botão Adicionar (+) para adicionar sua ID da Apple. Para obter instruções detalhadas, confira [Adicionar sua conta de ID da Apple](https://help.apple.com/xcode/mac/current/#/devaf282080a).

1. A partir das configurações "Gerais" do projeto Xcode, altere o valor do **Identificador de Pacote** para `com.<NameOfVSProject>`, onde `<NameOfVSProject>` é o mesmo nome do projeto de solução do Visual Studio que você criou. Por exemplo, se você criou um projeto chamado `MyOpenGLESApp` no Visual Studio, configure **Identificador de Pacote** como `com.MyOpenGLESApp`.

   ![Identificador de pacote Xcode](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "CPPMDD_OpenGLES_iOSXcodeId")

1. Para habilitar a assinatura automática, selecione. Gerencie a assinatura automaticamente**.

   ![Assinatura automática do Xcode](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "CPPMDD_OpenGLES_iOSXcodeSign")

1. Selecione o nome da equipe da ID da Apple que você adicionou como a **Equipe** de desenvolvimento.

   ![Equipe do Xcode](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "CPPMDD_OpenGLES_iOSXcodeTeam")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>Criar e executar o aplicativo iOS em um dispositivo iOS

1. Execute o agente remoto no seu Mac e verifique se o Visual Studio está emparelhado com o agente remoto. Para iniciar o agente remoto, abra uma janela do aplicativo Terminal e digite `vcremote`. Para obter mais informações, consulte [Configurar o agente remoto no Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).

   ![Janela do Terminal Mac executando vcremote](../cross-platform/media/cppmdd_common_vcremote.png "CPPMDD_common_vcremote")

1. Anexe um dispositivo iOS ao seu Mac. Quando você conecta seu dispositivo a um computador pela primeira vez, um alerta pergunta se você confia no computador para acessar seu dispositivo. Habilite o dispositivo para confiar no computador Mac.

1. No Visual Studio, se ainda não estiver selecionado, escolha a plataforma de solução na lista suspensa **Plataformas de Solução** com base no processador do dispositivo. Neste exemplo, é um processador **ARM64**.

   ![Definir a Plataforma de Solução como ARM64](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "CPPMDD_OpenGLES_SolutionPlatARM64")

1. No Gerenciador de Soluções, abra o menu de atalho para o projeto MyOpenGLESApp.iOS.Application e escolha **Descarregar Projeto** para descarregar o projeto.

1. Novamente, abra o menu de atalho para o projeto MyOpenGLESApp.iOS.Application descarregado e escolha **Editar project.pbxproj** para editar o arquivo do projeto. No arquivo `project.pbxproj`, procure o atributo `buildSettings` e adicione `DEVELOPMENT_TEAM` usando sua ID de equipe da Apple. A captura de tela abaixo mostra um valor de exemplo de `123456ABC` para a ID de equipe da Apple. Você pode encontrar o valor da sua ID de equipe da Apple no Xcode. Vá para **Configurações da Compilação** e passe o mouse sobre o nome da equipe de desenvolvimento para mostrar uma dica de ferramenta. A dica de ferramenta mostra a ID da equipe.

   ![Definir a equipe de desenvolvimento](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "CPPMDD_OpenGLES_iOSDevelopmentTeam")

1. Feche o arquivo `project.pbxproj`, abra o menu de atalho para o projeto MyOpenGLESApp.iOS.Application e escolha **Recarregar Projeto** para recarregar o projeto.

1. Agora crie o projeto MyOpenGLESApp.iOS.Application abrindo o menu de atalho do projeto e escolhendo **Compilar**.

   ![Compilar o projeto de Aplicativo iOS](../cross-platform/media/cppmdd_opengles_iosbuild.png "CPPMDD_OpenGLES_iOSBuild")

   A janela Saída exibe a saída do processo de build para a biblioteca estática do iOS e o aplicativo iOS. No Mac, a janela Terminal executando o agente remoto mostra a atividade de comando e transferência de arquivo.

   No seu computador Mac, você pode ser solicitado a permitir que o codesign acesse seu conjunto de chaves. Escolha **Permitir** para continuar.

1. Escolha o seu dispositivo iOS na barra de ferramentas para executar o aplicativo no seu dispositivo conectado ao seu Mac. Se o aplicativo não iniciar, verifique se o dispositivo dá permissão para que o aplicativo implantado seja executado no dispositivo. Essa permissão pode ser definida acessando **Configurações** > **Geral** > **Gerenciamento de Dispositivo** no dispositivo. Selecione sua conta de Aplicativo de Desenvolvedor, insira sua conta e verifique o aplicativo. Tente executar o aplicativo novamente no Visual Studio.

   ![Aplicativo iOS no dispositivo iOS](../cross-platform/media/cppmdd-opengles-iosdevice.png "CPPMDD_OpenGLES_iOSDevice")
   
   Quando seu aplicativo tiver sido iniciado, você poderá definir pontos de interrupção e usar o depurador do Visual Studio para examinar locais, consultar a pilha de chamadas e inspecionar os valores.

   ![Depurador no ponto de interrupção no aplicativo iOS](../cross-platform/media/cppmdd_opengles_iosdebug.png "CPPMDD_OpenGLES_iOSDebug")

1. Pressione **Shift**+**F5** para parar a depuração.

   Os projetos de aplicativo e biblioteca do iOS gerados colocam o código C++ em uma biblioteca estática que implementa somente o código compartilhado. A maior parte do código do aplicativo esta no projeto de `Application`. As chamadas para o código de biblioteca compartilhada neste projeto de modelo são feitas no arquivo *GameViewController.m*. Para compilar seu aplicativo iOS, o Visual Studio usa o conjunto de ferramentas de plataforma do Xcode, que exige a comunicação com um cliente remoto em execução em um Mac.

   O Visual Studio transfere os arquivos de projeto e envia comandos para o cliente remoto para compilar o aplicativo usando Xcode. O cliente remoto envia informações de status de build de volta ao Visual Studio. Quando o aplicativo tiver sido compilado com êxito, você poderá usar o Visual Studio para enviar comandos para executar e depurar o aplicativo. O depurador no Visual Studio controla o aplicativo em execução no seu dispositivo iOS conectado ao seu Mac. O Visual Studio mapeia as propriedades no projeto StaticLibrary para as opções usadas para compilar, vincular e depurar na plataforma de destino iOS. Para obter detalhes de opção de linha de comando do compilador, abra a caixa de diálogo **Páginas de Propriedade** para o projeto MyOpenGLESApp.iOS.StaticLibrary.

## <a name="customize-your-apps"></a>Personalizar seus aplicativos

Você pode modificar o código C++ compartilhado para adicionar ou alterar funcionalidade comum. Você deve alterar as chamadas para o código compartilhado para corresponder aos projetos `MyOpenGLESApp.Android.NativeActivity` e `MyOpenGLESApp.iOS.Application`. Você pode usar macros de pré-processador para especificar seções específicas de plataforma no seu código comum. A macro do pré-processador `__ANDROID__` é predefinida ao compilar para Android. A macro do pré-processador `__APPLE__` é predefinida ao compilar para iOS.

Para ver o IntelliSense para uma plataforma de projeto específica, escolha o projeto na lista suspensa do seletor de contexto na barra de Navegação na parte superior da janela do editor.

![Lista suspensa do seletor de contexto do projeto no editor](../cross-platform/media/cppmdd_opengles_contextswitcher.png)

Problemas do IntelliSense no código que é usado pelo projeto atual são marcados com uma linha ondulada vermelha. Problemas em outros projetos são marcados com uma linha ondulada roxa. O Visual Studio não dá suporte à coloração de código nem a arquivos IntelliSense para Java ou Objective-C. No entanto, você ainda pode modificar os arquivos de origem e alterar os recursos para definir o nome, o ícone e outros detalhes de implementação do aplicativo.
