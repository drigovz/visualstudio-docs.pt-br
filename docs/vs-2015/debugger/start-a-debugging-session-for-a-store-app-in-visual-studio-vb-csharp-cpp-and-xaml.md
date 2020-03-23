---
title: Inicie uma sessão de depuração para um aplicativo da Loja (VB, C#, C++ e XAML) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f12d6cde30dec9062dd67a18558bd0571e6fe6b1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302472"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Iniciar uma sessão de depuração de um aplicativo da Store no Visual Studio (VB, C#, C++ e XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplica-se ao Windows e Windows Phone(.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Este tópico descreve como iniciar uma sessão de depuração para aplicativos da Windows Store escritos em XAML e Visual C++, Visual C# ou Visual Basic. Depurar um aplicativo envolve configurar a sessão de depuração e escolher a maneira de iniciar o aplicativo.

> [!NOTE]
> Para aplicativos gravados em JavaScript e HTML, consulte [Iniciar uma sessão de depuração (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>Neste tópico
 [{1&amp;gt;A maneira fácil de iniciar a depuração&amp;lt;1}](#BKMK_The_easy_way_to_start_debugging)

 [Configurar a sessão de depuração](#BKMK_Configure_the_debugging_session)

- [Abrir a página de propriedades de depuração do projeto](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Escolher as opções de configuração de build](#BKMK_Choose_the_build_configuration_options)

- [{1&amp;gt;Escolher o destino de implantação&amp;lt;1}](#BKMK_Choose_the_deployment_target)

- [Escolha o depurador para usar](#BKMK_Choose_the_debugger_to_use)

- [{1&amp;gt;{2&amp;gt;(Opcional) Atrasar o início da sessão de depuração&amp;lt;2}&amp;lt;1}](#BKMK__Optional__Delay_starting_the_debug_session)

- [(Opcional) Desabilitar loopbacks de rede](#BKMK__Optional__Disable_network_loopbacks)

- [(Opcional) Reinstalar o aplicativo ao iniciar a depuração](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)

- [{1&amp;gt;{2&amp;gt;(Opcional) Desabilitar a requisição de autenticação para iniciar o depurador remoto&amp;lt;2}&amp;lt;1}](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)

  [Iniciar a sessão de depuração](#BKMK_Start_the_debugging_session)

- [{1&amp;gt;Iniciar a depuração (F5)&amp;lt;1}](#BKMK_Start_debugging__F5_)

- [{1&amp;gt;{2&amp;gt;Iniciar a depuração (F5), mas atrasar o início do aplicativo&amp;lt;2}&amp;lt;1}](#BKMK_Start_debugging__F5__but_delay_the_app_start)

- [{1&amp;gt;Iniciar um aplicativo instalado no depurador&amp;lt;1}](#BKMK_Start_an_installed_app_in_the_debugger)

- [Anexar o depurador a um aplicativo em execução](#BKMK_Attach_the_debugger_to_a_running_app_)

  - [Defina o aplicativo para ser executado no modo de depuração](#BKMK_Set_the_app_to_run_in_debug_mode)

  - [Anexar o depurador](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>A maneira mais fácil de começar a depurar

1. Abra a solução do aplicativo no Visual Studio.

2. {1&gt;Escolha {2&gt;F5&lt;2}.&lt;1}

   O Visual Studio compila e inicia o aplicativo com o depurador anexado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim. Para obter mais informações, consulte [Navegar em uma sessão de depuração (Xaml e C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Configure a sessão de depuração

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Abra a página de propriedade de depuração para o projeto

1. No Gerenciador de Soluções, selecione o projeto. No menu de atalho, escolha **Propriedades**.

2. Faça isso para abrir a página de propriedades de depuração do projeto:

    - Para os aplicativos Visual C# e Visual Basic, escolha **Debug**.

         ![C&#35; &#47; página de propriedade de debug do projeto VB](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    - Para aplicativos Visual C++, expanda o nó **Propriedades de configuração** e escolha **Depuração**.

         ![C&#43;&#43; página de depuração do aplicativo da Windows Store](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a>Escolha as opções de configuração de compilação

1. Na lista **Configuração,** escolha **Depurar** ou **(Ativo) Debug**.

2. Na lista **Plataforma,** escolha a plataforma de destino para criar. Na maioria dos casos, **qualquer CPU** **(Todas as plataformas** no Visual C++) é a melhor escolha.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Escolha o alvo de implantação
 ![Aplica-se apenas ao Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Você pode implantar e depurar um aplicativo da Windows Store no computador com Visual Studio, no simulador do Visual Studio no computador local ou em um dispositivo remoto.

- Para os aplicativos C# e Visual Basic, escolha o destino da lista de **dispositivos Target** na página de propriedade **Debug** para o projeto.

- Para aplicativos C++, escolha o destino do **Depurador para iniciar a** lista na página de propriedade **Depuração:**

  Escolha uma destas opções:

|||
|-|-|
|**Máquina local**|Depura o aplicativo na sessão atual no computador local. Consulte [Executar aplicativos do Windows Store na máquina local](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulador**|Depura o aplicativo no simulador do Visual Studio para aplicativos [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. O simulador é uma janela da área de trabalho que permite depurar recursos, como gestos de toque e rotação de dispositivos, que não estão disponíveis no computador local. Consulte [Executar aplicativos do Windows Store no simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Máquina remota**|Depura o aplicativo em um dispositivo conectado ao computador local por uma intranet ou diretamente por meio de um cabo Ethernet. Para depurar remotamente, as Ferramentas Remotas do Visual Studio devem estar instaladas e em execução no dispositivo remoto. Consulte [Executar aplicativos do Windows Store em uma máquina remota](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Se você escolher **Máquina remota,** especifique o nome ou endereço IP da máquina remota em uma dessas maneiras:

- Digite o nome ou endereço IP do computador remoto.

  - Para c# e aplicativos Visual Basic, digite o nome ou endereço IP na caixa **de máquina remota.**

  - Para aplicativos C++, digite o nome ou endereço IP na caixa Nome da **máquina.**

- Escolha a máquina remota na caixa de diálogo **Selecionar conexão de depurador remoto.**

   Para abrir a caixa de diálogo:

  - Para c# e aplicativos Visual Basic, escolha **Encontrar**.

  - Para os aplicativos C++, escolha a seta para baixo na caixa Nome da **máquina** e escolha ** \<Localizar...>**.

    ![Selecione caixa de diálogo Conexão de depurador remoto](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > A caixa de diálogo **Select Remote Debugger Connection** exibe máquinas que estão na sub-rede local e máquinas que estão diretamente conectadas à máquina do Visual Studio por um cabo Ethernet. Para especificar outra máquina, digite o nome na caixa **Nome da máquina.**

  ![Aplica-se apenas ao Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Você pode implantar e depurar um aplicativo da Windows Phone Store em um dispositivo ou em um dos emuladores de telefone do Visual Studio. Selecione o dispositivo ou emulador na lista **do dispositivo Alvo.**

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> Escolher o depurador a ser usado
 Por padrão, o Visual Studio depura o código gerenciado nos aplicativos em C# e Visual Basic.

 Para aplicativos em C# e Visual Basic, você pode optar por depurar o código gerenciado e o código C/C++ nativo. Selecione **a caixa de seleção Ativar depuração de código não gerenciada** para incluir código nativo na sessão de depuração.

 Por padrão, o Visual Studio depura o código nativo no aplicativo em C++.

 Para aplicativos em C++, você pode escolher depurar tipos específicos de código que estão em componentes do seu aplicativo em vez do código nativo ou além dele. Você especifica o código a ser depurado na lista **Tipo de depuração** na página de propriedade **Depuração** do projeto do aplicativo.

 Escolha um desses depuradores na lista de processos do **aplicativo:**

|||
|-|-|
|**{1&amp;gt;Somente Script&amp;lt;1}**|Depura o código JavaScript no aplicativo. O código gerenciado e o código nativo são ignorados.|
|**Somente nativo**|Depura o código C/C++ nativo no aplicativo. O código gerenciado e o código JavaScript são ignorados.|
|**Somente Gerenciado**|Depura o código gerenciado no aplicativo. O código JavaScript e o código C/C++ nativo são ignorados.|
|**Misto (Gerenciado e Nativo)**|Depura o código C/C++ nativo e o código gerenciado no aplicativo. O código JavaScript é ignorado.|
|**{1&amp;gt;{2&amp;gt;Somente GPU&amp;lt;2}&amp;lt;1}**|Depurar o código C++ nativo que é executado em uma GPU (unidade de processamento gráfico).|

 ![Aplica-se apenas ao Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

 Para aplicativos do Windows Store Phone, você também pode escolher o depurador para usar para processos em segundo plano do processo de **tarefa em segundo plano**.

### <a name="optional-delay-starting-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_the_debug_session"></a>(Opcional) Demore a iniciar a sessão de depuração
 Por padrão, o Visual Studio inicia o aplicativo imediatamente quando você começa a depuração. Você também pode iniciar uma sessão de depuração, mas atrasar o início do seu aplicativo. Quando você escolhe essa opção, o aplicativo é iniciado no depurador quando é executado na tela inicial ou por um contrato de ativação ou quando é iniciado por outro processo ou método. Você também atrasa o início do aplicativo quando deseja depurar uma tarefa em segundo plano quando o aplicativo em si não está em execução.

 Para atrasar a inicialização do aplicativo, você pode fazer o seguinte:

- Para os aplicativos Visual C# e Visual Basic, selecione **Não inicie, mas depura rastize meu código quando ele começar** na página de propriedade **Debug.**

- Para os aplicativos Visual C++, escolha **Sim** na lista **de aplicativos** de lançamento na página de propriedade **Depuração.**

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>(Opcional) Desativar loopbacks de rede
 ![Aplica-se apenas ao Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Por motivos de segurança, um aplicativo da Windows Store instalado da maneira padrão não pode efetuar chamadas de rede para o dispositivo em que está instalado. Por padrão, a implantação do Visual Studio cria uma isenção dessa regra para o aplicativo implantado. Essa isenção permite que você teste procedimentos de comunicação em um único computador. Antes de enviar seu aplicativo para o Windows Store, você deve testá-lo sem a isenção.

 Para remover a isenção de loopback de rede:

- Para os aplicativos Visual C# e Visual Basic, limpe a caixa de seleção **Allow Network Loopback** na página de propriedade **Debug.**

- Para aplicativos Visual C++, escolha **Não** na lista **'Permitir loopback de rede'** na página de propriedade **Depuração.**

### <a name="optional-reinstall-the-app-when-you-start-debugging"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>(Opcional) Reinstale o aplicativo quando você começar a depurar
 Para diagnosticar problemas com a instalação e a configuração inicial do seu aplicativo Visual C# ou Visual Basic, escolha **Desinstalar e, em seguida, reinstalar meu pacote** na página de propriedade **Debug** para recriar uma instalação original quando você começar a depurar. Essa opção não está disponível para projetos do Visual C++.

### <a name="optional-disable-authentication-requirement-to-start-the-remote-debugger"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>(Opcional) Desativar o requisito de autenticação para iniciar o depurador remoto
 ![Aplica-se apenas ao Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Por padrão, você deve fornecer credenciais para executar o depurador remoto.

> [!IMPORTANT]
> Você também pode optar por executar o depurador remoto no Modo Sem Autenticação, mas isso é altamente desaconselhável. Nesse modo, não há nenhuma segurança de rede. Escolha o Modo Sem Autenticação somente se você tiver certeza de que a rede não corre risco de tráfego mal-intencionado ou hostil.

 Para remover a requisição de autenticação:

1. Para os aplicativos Visual C# e Visual Basic, limpe a caixa **de seleção 'Autenticação** de uso' na página de propriedade **Debug.**

2. Para aplicativos Visual C++, escolha **Não** na lista **De autenticação** de exigência na página de propriedade **Depuração.**

   [Neste tópico](#BKMK_In_this_topic)

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Inicie a sessão de depuração

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Iniciar a depuração (F5)
 Quando você escolhe **Iniciar depuração** (Teclado: F5) no menu **Debug,** o Visual Studio inicia o aplicativo com o depurador conectado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção ou o aplicativo chegue ao fim.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Comece a depurar (F5), mas atrase o início do aplicativo
 Você pode definir que o aplicativo seja executado no modo de depuração, mas inicie-o por outro método que não seja o depurador. Por exemplo, convém depurar a inicialização do aplicativo no menu Iniciar ou depurar um processo em segundo plano do aplicativo sem iniciá-lo. Para atrasar o início do aplicativo, faça o seguinte:

- Na página de propriedade **Depuração** do aplicativo **(Depuração** no Visual C++)

  - Para os aplicativos Visual C# e Visual Basic, escolha **Não inicie, mas depurar meu código quando ele começar**.

  - Para os aplicativos Visual C++, escolha **Sim** na lista **de aplicativos de lançamento.**

- Escolha **Iniciar depuração** no menu **Depuração** (Teclado: F5).

- Inicie o aplicativo pelo menu Iniciar, por um contrato de execução ou por outro procedimento.

  O aplicativo é iniciado no modo de depuração. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.

  . Para obter mais informações sobre a depuração de tarefas em segundo plano, consulte [Iniciar suspender, retomar e eventos em segundo plano para o Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Inicie um aplicativo instalado no depurador
 Quando você inicia a depuração usando F5, o Visual Studio compila e implanta o aplicativo, define que ele seja executado no modo de depuração e, em seguida, inicia-o. Para iniciar um aplicativo que já está instalado em um dispositivo, use a caixa de diálogo Depurar Pacote do Aplicativo Instalado. Esse procedimento é útil quando você precisa depurar um aplicativo instalado da Windows Store ou quando você tem os arquivos de origem do aplicativo, mas não tem um projeto do Visual Studio para o aplicativo. Por exemplo, você pode ter um sistema de build personalizado que não use projetos ou soluções do Visual Studio.

 O aplicativo pode ser instalado no dispositivo local ou pode estar localizado em um dispositivo remoto.  É possível iniciar o aplicativo imediatamente ou defini-lo para ser executado no depurador quando for iniciado por outro processo ou método, por exemplo, no menu Iniciar ou por um contrato de ativação. Você também pode definir o aplicativo para ser executado no modo de depuração quando quiser depurar um processo em segundo plano sem iniciar o aplicativo. Para obter mais informações, consulte [Iniciar suspender, retomar e fazer eventos em segundo plano para a Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Para definir um aplicativo instalado para ser executado no modo de depuração, faça o seguinte:

> [!NOTE]
> O aplicativo não deve estar em execução quando você iniciar este procedimento.

1. No menu **Debug,** escolha **Debug Installed App Package**

2. Escolha uma destas opções na lista:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Máquina local**  |                                                                                                                Depura o aplicativo na sessão atual no computador local. Consulte [Executar aplicativos do Windows Store na máquina local](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulador**    | Depura o aplicativo no simulador do Visual Studio para aplicativos [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. O simulador é uma janela da área de trabalho que permite depurar recursos, como gestos de toque e rotação de dispositivos, que não estão disponíveis no computador local. Consulte [Executar aplicativos do Windows Store no simulador](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Máquina remota** |                          Depura o aplicativo em um dispositivo conectado ao computador local por uma intranet ou diretamente por meio de um cabo Ethernet. Para depurar remotamente, as Ferramentas Remotas do Visual Studio devem estar instaladas e em execução no dispositivo remoto. Consulte [Executar aplicativos do Windows Store em uma máquina remota](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. Escolha o aplicativo na lista **Pacotes de aplicativos instalados.**

4. Escolha o mecanismo de depuração a ser usado na **lista Debug deste tipo de código.**

5. (Opcional). Escolha **Não inicie, mas depurar meu código quando ele começar** a depurar o aplicativo quando ele é iniciado por algum outro método, ou para depurar um processo de fundo.

   Quando você **clica**em Iniciar , o aplicativo é iniciado ou está definido para ser executado no modo de depuração.

### <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Anexar o depurador a um aplicativo em execução
 Para anexar o depurador a um aplicativo [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], você deve usar o Gerenciador de Pacotes Depuráveis para definir a execução do aplicativo no modo de depuração. Esse recurso é instalado com as Ferramentas Remotas do Visual Studio.

 Anexar o depurador a um aplicativo é útil quando você precisa depurar um aplicativo já instalado; por exemplo, um que tenha sido instalado da [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]. A anexação é necessária quando você tem os arquivos de origem do aplicativo, mas não tem um projeto do Visual Studio para ele. Por exemplo, você pode ter um sistema de build personalizado que não use projetos ou soluções do Visual Studio.

 Para anexar o depurador a um aplicativo, são necessárias as seguintes etapas:

1. Defina o aplicativo para ser executado no modo de depuração. Isso deve ser feito quando o aplicativo não está em execução.

2. Inicie o aplicativo. Você pode fazer isso pela tela inicial, por um contrato de execução ou por outro método.

3. Anexe o depurador ao aplicativo em execução.

#### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Defina o aplicativo para ser executado no modo de depuração

1. Instale as Ferramentas Remotas do Visual Studio no dispositivo em que o aplicativo está instalado. Consulte [Instalar as ferramentas remotas](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Na tela inicial, procure por `Debuggable Package Manager` e inicie-o.

     É exibida uma janela do PowerShell corretamente configurada para o cmdlet AppxDebug.

3. Para habilitar a depuração de um aplicativo, é preciso especificar o identificador NomeCompletodoPacote do aplicativo. Para ver uma lista de todos os aplicativos que incluem o NomeCompletodoPacote, digite `Get-AppxPackage` no aviso do PowerShell.

4. No prompt do PowerShell, `Enable-AppxDebug` *digite PackageFullName* onde *PackageFullName* é o identificador PackageFullName do aplicativo.

#### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Anexar o depurador
 Para anexar o depurador:

1. No menu **Depurar**, escolha **Anexar ao Processo**.

    A caixa de diálogo **Anexar ao Processo** é exibida.

2. Para anexar a um aplicativo em um dispositivo remoto, especifique o dispositivo remoto na caixa **Qualifier.** Você pode:

   - Digite o nome na caixa **Qualifier.**

   - Escolha a seta baixa na caixa **Qualificador e** escolha o dispositivo em uma lista de dispositivos aos quais você já anexou antes.

   - Escolha **Encontrar** para selecionar o dispositivo em uma lista de dispositivos em sua sub-rede local.

3. Especifique o tipo de código que deseja depurar na **caixa Anexar à** caixa.

    Escolha **Selecionar** e, em seguida, faça um dos seguintes:

   - Escolha **determinar automaticamente o tipo de código a ser depurado**

   - Escolha **Depurar esses tipos de código** e escolha um ou mais tipos da lista.

4. Na lista **Processos Disponíveis,** escolha o processo do aplicativo.

5. Escolha **Anexar**.

   O Visual Studio anexa o depurador ao processo. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.

   [Neste tópico](#BKMK_In_this_topic)

## <a name="see-also"></a>Consulte Também
 [Aplicativos de depuração no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md) [Navegam em uma sessão de depuração (Xaml e C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)
