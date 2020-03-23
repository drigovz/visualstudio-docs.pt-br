---
title: Inicie uma sessão de depuração para aplicativos de loja (JavaScript) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b4e861c8985ee37a8c2d9b7f9286d6284bb4f91
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302479"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Iniciar uma sessão de depuração para aplicativos da Store no Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplica-se ao Windows e Windows Phone(.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Este tópico descreve como iniciar uma sessão de depuração para os aplicativos da Windows Store gravados em JavaScript e HTML5. Você pode iniciar a depuração com um único pressionamento de tecla ou configurar a sessão de depuração para cenários específicos e escolher a maneira de iniciar o aplicativo.

> [!NOTE]
> Para aplicativos escritos em XAML e Visual C#, Visual C++ou Visual Basic, consulte [Iniciar uma sessão de depuração (VB, C#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>Neste tópico
 [Neste tópico](#BKMK_In_this_topic)

 [{1&amp;gt;A maneira fácil de iniciar a depuração&amp;lt;1}](#BKMK_The_easy_way_to_start_debugging)

 [Configurar a sessão de depuração](#BKMK_Configure_the_debugging_session)

- [Abrir a página de propriedades de depuração do projeto](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Escolher as opções de configuração de build](#BKMK_Choose_the_build_configuration_options)

- [{1&amp;gt;Escolher o destino de implantação&amp;lt;1}](#BKMK_Choose_the_deployment_target)

- [Escolha o depurador para usar](#BKMK_Choose_the_debugger_to_use)

- [(Opcional) Atrasar o início do aplicativo na sessão de depuração](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [(Opcional) Desabilitar loopbacks de rede](#BKMK__Optional__Disable_network_loopbacks)

  [Iniciar a sessão de depuração](#BKMK_Start_the_debugging_session)

- [{1&amp;gt;Iniciar a depuração (F5)&amp;lt;1}](#BKMK_Start_debugging__F5_)

- [{1&amp;gt;{2&amp;gt;Iniciar a depuração (F5), mas atrasar o início do aplicativo&amp;lt;2}&amp;lt;1}](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [{1&amp;gt;Iniciar um aplicativo instalado no depurador&amp;lt;1}](#BKMK_Start_an_installed_app_in_the_debugger)

  [Anexar o depurador a um aplicativo em execução](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Defina o aplicativo para ser executado no modo de depuração](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Anexar o depurador](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>A maneira mais fácil de começar a depurar
 ![Aplica-se apenas ao Windows](../debugger/media/windows-only-content.png "windows_only_content")

1. Abra a solução do aplicativo no Visual Studio.

2. Se a solução contém projetos para aplicativos da Windows Store e Windows Phone Store, verifique se o projeto que você quer depurar é o projeto de inicialização. Em Explorar a solução, selecione o projeto e escolha **'Iniciar como Projeto de Inicializar',** no menu de contexto.

3. Pressione F5.

   ![Aplica-se apenas ao Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

   O Visual Studio compila e inicia o aplicativo com o depurador anexado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim. Para obter mais informações, consulte [Quickstart: Debug HTML e CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Configure a sessão de depuração
 Como o script não está compilado, a configuração de compilação e as configurações da plataforma não se aplicam. Se você estiver depurando um componente C++ ou gerenciado, defina a **Configuração** **como Depuração** e escolha sua plataforma de destino na caixa de diálogo **Configuração.**

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Abra a página de propriedade de depuração para o projeto

1. No Gerenciador de Soluções, selecione o projeto. No menu de atalho, escolha **Propriedades**.

2. Expanda o nó Propriedades de **configuração** e, em seguida, escolha **Depuração**

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a>Escolha as opções de configuração de compilação

1. Na lista **Configuração,** escolha **Depurar** ou **(Ativo) Debug**.

2. Na lista **Plataforma,** escolha a plataforma de destino para criar. Na maioria dos casos, **qualquer CPU** é a melhor escolha.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Escolha o alvo de implantação
 Você pode implantar e depurar um aplicativo no computador com o Visual Studio, no simulador do Visual Studio do computador local ou de um computador remoto. Você escolhe o destino do **Depurador para iniciar a** lista na página de propriedade **Depuração** para o projeto.

 ![Aplica-se apenas ao Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Para um aplicativo da Windows Store, escolha uma dessas opções na lista **de dispositivos Target:**

|||
|-|-|
|**Máquina local**|Depura o aplicativo na sessão atual no computador local. Consulte [Executar aplicativos do Windows Store na máquina local](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulador**|Depura o aplicativo no simulador do Visual Studio para aplicativos [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. O simulador é uma janela da área de trabalho que permite depurar recursos, como gestos de toque e rotação de dispositivos, que não estão disponíveis no computador local. Consulte [Executar aplicativos do Windows Store no simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Máquina remota**|Depura o aplicativo em um dispositivo conectado ao computador local por uma intranet ou diretamente por meio de um cabo Ethernet. Para depurar remotamente, as Ferramentas Remotas do Visual Studio devem estar instaladas e em execução no dispositivo remoto. Consulte [Executar aplicativos do Windows Store em uma máquina remota](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Se você escolher **Máquina remota,** especifique o nome ou endereço IP da máquina remota em uma dessas maneiras:

- Digite o nome ou endereço IP da máquina remota na caixa **Nome da máquina.**

- Escolha a seta para baixo na caixa Nome da **máquina** e escolha ** \<Localizar...>**. Em seguida, escolha a máquina remota na caixa de diálogo **Selecionar depurador remoto Depurador de conexão.**

   ![Selecione conexão de depurador remota](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > A caixa de diálogo Selecionar Conexão de Depurador Remoto exibe os computadores que estão na sub-rede local e os computadores que estão diretamente conectados ao computador com o Visual Studio por um cabo Ethernet. Para especificar outra máquina, digite o nome na caixa **Nome da máquina.**

  ![Aplica-se apenas ao Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Para um aplicativo do Windows Store Phone, escolha **Dispositivo** ou um dos emuladores da lista **de dispositivos Target.**

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> Escolher o depurador a ser usado
 Por padrão, o depurador se anexa ao código JavaScript do aplicativo. Você pode escolher depurar o código C++ nativo e gerenciado dos componentes do aplicativo em vez do código JavaScript. Você especifica o código a ser depurado na lista **Tipo de depuração** na página de propriedade **Depuração** do projeto do aplicativo.

 Escolha um desses depuradores na lista **Tipo de depuração:**

|||
|-|-|
|**{1&amp;gt;Somente Script&amp;lt;1}**|Depura o código JavaScript no aplicativo. O código gerenciado e o código nativo são ignorados.|
|**Somente nativo**|Depura o código C/C++ nativo no aplicativo. O código gerenciado e o código JavaScript são ignorados.|
|**Nativo com Script**|Depura o código C++ nativo e o código JavaScript no aplicativo.|
|**Somente Gerenciado**|Depura o código gerenciado no aplicativo. O código JavaScript e o código C/C++ nativo são ignorados.|
|**Misto (Gerenciado e Nativo)**|Depura o código C/C++ nativo e o código gerenciado no aplicativo. O código JavaScript é ignorado.|

### <a name="optional-delay-starting-the-app-in-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>(Opcional) Demore a iniciar o aplicativo na sessão de depuração
 Por padrão, o Visual Studio inicia o aplicativo imediatamente quando você começa a depuração. Você também pode iniciar uma sessão de depuração, mas atrasar o início do seu aplicativo. O aplicativo é iniciado no depurador quando é iniciado do menu Iniciar ou por um contrato de ativação ou quando é iniciado por outro processo ou método. Você também pode usar o início atrasado para depurar eventos em segundo plano no aplicativo que você quer que ocorram quando o aplicativo não está em execução.

 Você especifica se deseja atrasar o lançamento do seu aplicativo na lista **de aplicativos** de lançamento na página de propriedade **Depuração** do projeto do aplicativo. Escolha uma destas opções:

- Escolha **Não** para atrasar o lançamento do seu aplicativo.

- Escolha **Sim** para iniciar o aplicativo imediatamente.

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>(Opcional) Desativar loopbacks de rede
 ![Aplica-se apenas ao Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Por motivos de segurança, um aplicativo da Windows Store instalado da maneira padrão não pode efetuar chamadas de rede para o dispositivo em que está instalado. Por padrão, a implantação do Visual Studio cria uma isenção dessa regra para o aplicativo implantado. Essa isenção permite que você teste procedimentos de comunicação em um único computador. Antes de enviar seu aplicativo para o Windows Store, você deve testá-lo sem a isenção.

 Para remover a isenção de loopback de rede, escolha **Não** na lista **Permitir loopback** de rede na página de propriedade **Depuração.**

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Inicie a sessão de depuração

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Iniciar a depuração (F5)
 Quando você escolhe **Iniciar Depuração** no menu **Debug** (Teclado: F5), o Visual Studio inicia o aplicativo com o depurador conectado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Comece a depurar (F5), mas atrase o início do aplicativo
 Você pode definir o aplicativo para ser executado no modo de depuração, mas inicie-o por outro método que não seja o depurador. Por exemplo, convém depurar a inicialização do aplicativo no menu Iniciar ou depurar um processo em segundo plano do aplicativo sem iniciá-lo. Para atrasar o início do aplicativo, faça o seguinte:

1. Na página **Debug** das propriedades do projeto do aplicativo, escolha **Não** na lista **'Aplicativo de lançamento'.**

2. Escolha **Iniciar depuração** no menu **Depuração** (Teclado: F5).

3. Inicie o aplicativo pelo menu Iniciar, por um contrato de execução ou por outro procedimento.

   O aplicativo é iniciado no modo de depuração. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.

   . Para obter mais informações sobre a depuração de tarefas em segundo plano, consulte [Iniciar suspender, retomar e eventos em segundo plano para o Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

## <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Inicie um aplicativo instalado no depurador
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

## <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Anexar o depurador a um aplicativo em execução
 Para anexar o depurador a um aplicativo [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], você deve usar o Gerenciador de Pacotes Depuráveis para definir a execução do aplicativo no modo de depuração. Esse recurso é instalado com as Ferramentas Remotas do Visual Studio.

 Anexar o depurador a um aplicativo é útil quando você precisa depurar um aplicativo já instalado; por exemplo, um que tenha sido instalado na Windows Store. A anexação é necessária quando você tem os arquivos de origem do aplicativo, mas não tem um projeto do Visual Studio para ele. Por exemplo, você pode ter um sistema de build personalizado que não use projetos ou soluções do Visual Studio.

 Para anexar a um aplicativo:

1. Defina o aplicativo para ser executado no modo de depuração. Isso deve ser feito quando o aplicativo não está em execução.

2. Inicie o aplicativo. Você pode iniciar o aplicativo do menu Iniciar por um contrato de execução ou por outro método.

3. Anexe o depurador ao aplicativo em execução.

### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Defina o aplicativo para ser executado no modo de depuração

1. Instale as Ferramentas Remotas do Visual Studio no dispositivo em que o aplicativo está instalado. Consulte [Instalar as ferramentas remotas](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. No menu Iniciar, procure por `Debuggable Package Manager` e inicie-o.

     É exibida uma janela do PowerShell corretamente configurada para o cmdlet AppxDebug.

3. Para habilitar a depuração de um aplicativo, é preciso especificar o identificador NomeCompletodoPacote do aplicativo. Para ver uma lista de todos os aplicativos que incluem o NomeCompletodoPacote, digite `Get-AppxPackage` no aviso do PowerShell.

4. No prompt do PowerShell, `Enable-AppxDebug` *digite PackageFullName* onde *PackageFullName* é o identificador PackageFullName do aplicativo.

### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Anexar o depurador

> [!TIP]
> Os aplicativos JavaScript são executados em uma instância do processo wwahost.exe. Se outros aplicativos JavaScript estiverem em execução quando você anexa ao aplicativo, será necessário saber a ID do processo numérico (PID) do wwahost.exe em que o aplicativo está executando.
>
> A maneira mais fácil de lidar com essa situação é fechar todos os outros aplicativos JavaScript. Do contrário, você pode abrir o Gerenciador de Tarefas do Windows antes de iniciar o aplicativo e observar as IDs dos processos wwahost.exe. Quando você especificar o processo a ser anexado na caixa de diálogo **Processos Disponíveis,** o wwahost.exe do aplicativo terá um id diferente dos que você observou.

 Para anexar o depurador:

1. No menu **Depurar**, escolha **Anexar ao Processo**.

    A caixa de diálogo **Anexar ao Processo** é exibida.

2. Para anexar a um aplicativo em um dispositivo remoto, especifique o dispositivo remoto na caixa **Qualifier.** Você pode:

   - Digite o nome na caixa **Qualifier.**

   - Escolha a seta baixa na caixa **Qualificadore** e escolha o dispositivo em uma lista de dispositivos aos quais você já anexou antes.

   - Escolha **Encontrar** para escolher o dispositivo em uma lista de dispositivos em sua sub-rede local.

3. Especifique o tipo de código que deseja depurar na **caixa Anexar à** caixa.

    Escolha **Selecionar** e, em seguida, faça um dos seguintes:

   - Escolha **determinar automaticamente o tipo de código a ser depurado**

   - Escolha **Depurar esses tipos de código** e escolha um ou mais tipos da lista.

4. Na lista **Processos Disponíveis,** escolha o processo **wwahost.exe** apropriado. Use a coluna **Título** para identificar seu aplicativo.

5. Escolha **Anexar**.

   O Visual Studio anexa o depurador ao processo. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.

## <a name="see-also"></a>Consulte Também
 [Execução de controle em uma sessão de depuração (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [Quickstart: Depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md) [Trigger suspender, retomar e eventos em segundo plano para windows store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [Debug apps no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
