---
title: Depuração remota | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68ebd9ab8c4f9d3cda1371d90a8da459edb1592b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300555"
---
# <a name="remote-debugging"></a>Depuração remota
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode depurar um aplicativo do Visual Studio que foi implantado em um computador diferente.  Para fazer isso, use o depurador remoto do Visual Studio.  
  
 As informações aqui se aplicam a aplicativos de área de trabalho do Windows e aplicativos ASP.NET.  Para obter informações sobre depuração remota de aplicativos da Windows Store e aplicativos do Azure, consulte [depuração remota na Windows Store e aplicativos do Azure](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Obter as ferramentas remotas  
Você pode baixar as ferramentas remotas diretamente no dispositivo ou servidor que deseja depurar, ou pode obter as ferramentas remotas do seu computador host com o Visual Studio instalado.

### <a name="to-download-and-install-the-remote-tools"></a>Para baixar e instalar as ferramentas remotas
  
1. No computador do dispositivo ou do servidor que você deseja depurar (em vez da máquina que executa o Visual Studio), obtenha a versão correta das ferramentas remotas.

    |Version|Link|Observações|
    |-|-|-|
    |Visual Studio 2015 Atualização 3|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se solicitado, ingresse no grupo de Visual Studio Dev Essentials gratuito ou você pode apenas entrar com uma assinatura válida do Visual Studio. Em seguida, abra novamente o link, se necessário. Sempre baixar a versão correspondente ao sistema operacional do dispositivo (versão x86, x64 ou ARM)|
    |Visual Studio 2015 (mais antigo)|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se solicitado, ingresse no grupo de Visual Studio Dev Essentials gratuito ou você pode apenas entrar com uma assinatura válida do Visual Studio. Em seguida, abra novamente o link, se necessário.|
    |{1&gt;{2&gt;Visual Studio 2013&lt;2}&lt;1}|[Ferramentas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Página de download na documentação do Visual Studio 2013|
    |Visual Studio 2012|[Ferramentas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Página de download na documentação do Visual Studio 2012|
  
2. Na página de download, escolha a versão das ferramentas que corresponde ao seu sistema operacional (versão x86, x64 ou ARM) e baixe as ferramentas remotas.
  
    > [!IMPORTANT]
    > Recomendamos que você instale a versão mais recente das ferramentas remotas que correspondem à sua versão do Visual Studio. Não são recomendadas versões incompatíveis.  
    >   
    >  Além disso, você deve instalar as ferramentas remotas que têm a mesma arquitetura que o sistema operacional no qual você deseja instalá-lo. Em outras palavras, se você quiser depurar um aplicativo de 32 bits em um computador remoto que executa um sistema operacional de 64 bits, deverá instalar a versão de 64 bits das ferramentas remotas no computador remoto.  
  
3. Quando você terminar de baixar o executável, siga as instruções para instalar o aplicativo no computador remoto. Consulte [as instruções de instalação](#bkmk_setup)

Se você tentar copiar o depurador remoto (msvsmon. exe) para o computador remoto e executá-lo, lembre-se de que o **Assistente de configuração do depurador remoto** (**rdbgwiz. exe**) é instalado somente quando você baixa as ferramentas, e talvez seja necessário usar o assistente para configuração posteriormente, especialmente se você quiser que o depurador remoto seja executado como um serviço. Para obter mais informações, consulte [(opcional) configurar o depurador remoto como um serviço](#bkmk_configureService) abaixo.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Para executar o depurador remoto de um compartilhamento de arquivos

Você pode encontrar o depurador remoto (**msvsmon. exe**) em um computador com o Visual Studio 2015 Community, Professional ou Enterprise já instalado. Para muitos cenários, a maneira mais fácil de configurar a depuração remota é executar o depurador remoto (msvsmon. exe) de um compartilhamento de arquivos. Para obter limitações de uso, consulte a página de ajuda do depurador remoto (**Ajuda/uso** no depurador remoto).

1. Localize o **msvsmon. exe** no diretório que corresponde à sua versão do Visual Studio. Para o Visual Studio 2015:

      **Arquivos de Programas\microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Arquivos de Programas\microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Compartilhe a pasta do **depurador remoto** no computador do Visual Studio.

3. No computador remoto, execute **msvsmon. exe**. Siga as [instruções de instalação](#bkmk_setup).

> [!TIP] 
> Para instalação de linha de comando e referência de linha de comando, consulte a página de ajuda do **msvsmon. exe** digitando ``msvsmon.exe /?`` na linha de comando no computador com o Visual Studio instalado (ou vá para **Ajuda/uso** no depurador remoto).

## <a name="supported-operating-systems"></a>Supported Operating Systems  
 O computador remoto deve estar executando um dos seguintes sistemas operacionais:  
  
- Windows 10  
  
- Windows 8 ou 8,1  
  
- Windows 7 Service Pack 1  
  
- Windows Server 2012 ou Windows Server 2012 R2  
  
- Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Configurações de hardware com suporte  
  
- Processador de 1,6 GHz ou mais rápido  
  
- 1 GB de RAM (1,5 GB se executado em uma máquina virtual)  
  
- 1 GB de espaço em disco disponível  
  
- Disco rígido de 5400 RPM  
  
- Placa de vídeo compatível com DirectX 9 com execução na resolução de tela 1024 x 768 ou superior  
  
## <a name="network-configuration"></a>Configuração de rede  
 O computador remoto e o computador do Visual Studio devem estar conectados por uma rede, grupo de trabalho ou grupo doméstico, ou conectados diretamente por meio de um cabo Ethernet. Não há suporte para a depuração pela Internet.  
  
## <a name="bkmk_setup"></a>Configurar o depurador remoto  
 Você deve ter permissões administrativas no computador remoto  
  
1. Localize o aplicativo do depurador remoto. (Abra o menu iniciar e procure o **depurador remoto**.)
  
    Se você estiver executando o depurador remoto em um servidor remoto, poderá clicar com o botão direito do mouse no aplicativo do depurador remoto e escolher **Executar como administrador** (ou, você pode executar o depurador remoto como um serviço). Se você não o estiver executando em um servidor remoto, basta iniciá-lo normalmente.
  
2. Quando você inicia as ferramentas remotas pela primeira vez (ou antes de configurá-la), a caixa de daLog de **configuração de depuração remota** é exibida.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Se a API de serviço do Windows não estiver instalada (o que acontece somente no Windows Server 2008 R2), escolha o botão **instalar** .  
  
4. Selecione os tipos de rede nos quais você deseja usar as ferramentas remotas. Pelo menos um tipo de rede deve ser selecionado. Se os computadores estiverem conectados por meio de um domínio, você deverá escolher o primeiro item. Se os computadores estiverem conectados por meio de um grupo de trabalho ou grupos domésticos, você precisará escolher o segundo ou terceiro item, conforme apropriado.  
  
5. Escolha **Configurar depuração remota** para configurar o firewall e iniciar a ferramenta.  
  
6. Quando a configuração estiver concluída, a janela do depurador remoto será exibida.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    O depurador remoto agora está aguardando uma conexão. Anote o nome do servidor e o número da porta que é exibido, pois você precisará dele posteriormente para a configuração no Visual Studio.  
  
   Quando você terminar a depuração e precisar parar o depurador remoto, clique em **arquivo/sair** na janela. Você pode reiniciá-lo no menu **Iniciar** ou na linha de comando:  
  
   **\<diretório de instalação do Visual Studio > depurador do \Common7\IDE\Remote\\< x86, x64 ou Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Configurar o depurador remoto  
 Você pode alterar alguns aspectos da configuração do depurador remoto depois de iniciá-lo pela primeira vez.
  
- Para permitir que outros usuários se conectem ao depurador remoto, escolha **ferramentas/permissões**. Você deve ter privilégios de administrador para conceder ou negar permissões.

  > [!IMPORTANT]
  > Você pode executar o depurador remoto em uma conta de usuário que seja diferente da conta de usuário que você está usando no computador do Visual Studio, mas você deve adicionar a conta de usuário diferente às permissões do depurador remoto. 

   Como alternativa, você pode iniciar o depurador remoto a partir da linha de comando com o **/allow \<nome de usuário >** parâmetro: **msvsmon/allow \<username@computer>** .
  
- Para alterar o modo de autenticação ou o número da porta, ou para especificar um valor de tempo limite para as ferramentas remotas: escolha **ferramentas/opções**.  
  
   Para obter uma lista dos números de porta usados por padrão, consulte [atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  > Você também pode optar por executar as ferramentas remotas no Modo Sem Autenticação, mas isso é altamente desaconselhável. Nesse modo, não há nenhuma segurança de rede. Escolha o modo sem autenticação somente se você tiver certeza de que a rede não está em risco de tráfego mal-intencionado ou hostil.

## <a name="bkmk_configureService"></a>Adicional Configurar o depurador remoto como um serviço
 Para a depuração no ASP.NET e em outros ambientes de servidor, você deve executar o depurador remoto como administrador ou, se desejar que ele esteja sempre em execução, executar o depurador remoto como um serviço.
  
 Se você quiser configurar o depurador remoto como um serviço, siga estas etapas.  
  
1. Localize o **Assistente de configuração do depurador remoto** (rdbgwiz. exe). (Esse é um aplicativo separado do depurador remoto.) Ele está disponível somente quando você instala as ferramentas remotas. Ele não é instalado com o Visual Studio.  
  
2. Inicie a execução do assistente de configuração. Quando a primeira página aparecer, clique em **Avançar**.  
  
3. Marque a caixa de seleção **executar o depurador remoto do Visual Studio 2015 como um serviço** .  
  
4. Adicione o nome da conta de usuário e a senha.  
  
    Talvez seja necessário adicionar o direito de usuário **fazer logon como um serviço** a essa conta. (Localize a **política de segurança local** (secpol. msc) na página **inicial** ou na janela (ou digite **secpol** em um prompt de comando). Quando a janela for exibida, clique duas vezes em **atribuição de direitos de usuário**e, em seguida, localize **fazer logon como um serviço** no painel direito. Clique duas vezes nesse item. Adicione a conta de usuário à janela **Propriedades** e clique em **OK**.) Clique em **Avançar**.  
  
5. Selecione o tipo de rede com o qual você deseja que as ferramentas remotas se comuniquem. Pelo menos um tipo de rede deve ser selecionado. Se os computadores estiverem conectados por meio de um domínio, você deverá escolher o primeiro item. Se os computadores estiverem conectados por meio de um grupo de trabalho ou grupos domésticos, você deverá escolher o segundo ou terceiro itens. Clique em **Avançar**.  
  
6. Se o serviço puder ser iniciado, você verá **que concluiu com êxito o assistente de configuração de depurador remoto do Visual Studio**. Se o serviço não puder ser iniciado, você verá **falha ao concluir o assistente de configuração de depurador remoto do Visual Studio**. A página também fornece algumas dicas a serem seguidas para que o serviço seja iniciado.  
  
7. Clique em **Concluir**.  
  
   Neste ponto, o depurador remoto está sendo executado como um serviço. Você pode verificar isso indo até **painel de controle/serviços** e procurando pelo **depurador remoto do Visual Studio 2015**.  
  
   Você pode parar e iniciar o serviço de depurador remoto no **painel de controle/serviços**.  

## <a name="remote-debug-an-aspnet-application"></a>Depuração remota de um aplicativo ASP.NET  
 Implantar um aplicativo ASP.NET em um computador remoto que executa o IIS tem etapas diferentes, dependendo do sistema operacional e da versão do IIS. Para computadores remotos que executam o Windows Server 2008 ou o Windows Server 2012 que têm o IIS 7,5 ou posterior instalado, consulte [depuração remota ASP.net em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Se você estiver depurando um aplicativo ASP.NET Core, consulte [publicando no IIS](https://docs.asp.net/en/latest/publishing/iis.html). Etapas diferentes são necessárias para publicar um ASP.NET Core no IIS. Depois de publicar um aplicativo ASP.NET Core com êxito, você pode depurá-lo remotamente, [assim como outros aplicativos ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), exceto que o processo que você precisa anexar a é DNX. exe em vez de w3wp. exe.

## <a name="remote-debug-a-visual-c-project"></a>Depuração remota de um C++ projeto Visual  
 No procedimento a seguir, o nome e o caminho do projeto são C:\remotetemp\MyMfc e o nome do computador remoto é **MJO-DL**.  
  
1. Crie um aplicativo MFC chamado **mymfc.**  
  
2. Defina um ponto de interrupção em algum lugar no aplicativo que seja facilmente acessado, por exemplo, em **MainFrm. cpp**, no início de `CMainFrame::OnCreate`.  
  
3. Em Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Propriedades**. Abra a guia **depuração** .  
  
4. Defina o **depurador para iniciar** o **depurador remoto do Windows**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Faça as seguintes alterações nas propriedades:  
  
   |Configuração|Valor|
   |-|-|  
   |Comando remoto|C:\remotetemp\mymfc.exe|  
   |Diretório de trabalho|C:\remotetemp|  
   |Nome do servidor remoto|MJO-DL:*PortNumber*|  
   |Conexão|Remoto sem Autenticação do Windows|  
   |Tipo de Depurador|Somente Nativo|  
   |Diretório de implantação|C:\remotetemp.|  
   |Arquivos adicionais a implantar|C:\data\mymfcdata.txt.|  
  
    Se você implantar arquivos adicionais (opcional), a pasta deverá existir em ambos os computadores.  
  
6. Em Gerenciador de Soluções, clique com o botão direito do mouse na solução e escolha **Configuration Manager**.  
  
7. Para a configuração de **Depuração**, selecione a caixa de seleção **Implantar**.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Iniciar Depuração (**depurar/iniciar depuração**ou **F5**).  
  
9. O executável é implantado automaticamente no computador remoto.  
  
10. Se solicitado, insira as credenciais de rede para se conectar ao computador remoto.  
  
     As credenciais necessárias são específicas para a configuração de segurança da sua rede. Por exemplo, em um computador de domínio, você pode escolher um certificado de segurança ou inserir seu nome de domínio e senha. Em um computador que não seja de domínio, você pode inserir o nome do computador e um nome de conta de usuário válido, como <strong>MJO-DL\name@something.com</strong>, junto com a senha correta.  
  
11. No computador do Visual Studio, você deve ver que a execução é interrompida no ponto de interrupção.  
  
    > [!TIP]
    > Como alternativa, você pode implantar os arquivos como uma etapa separada. Na **Gerenciador de soluções,** clique com o botão direito do mouse no nó **mymfc** e escolha **implantar**.  
  
    Se você tiver arquivos que não são de código que precisam ser usados pelo aplicativo, você precisará incluí-los no projeto do Visual Studio. Crie uma pasta de projeto para os arquivos adicionais (na **Gerenciador de soluções**, clique em **Adicionar/nova pasta**.) Em seguida, adicione os arquivos à pasta (na **Gerenciador de soluções**, clique em **Adicionar/item existente**e selecione os arquivos.). Na página **Propriedades** de cada arquivo, defina **copiar para diretório de saída** como **copiar sempre**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Depuração remota de um C# projeto Visual ou Visual Basic  
 O depurador não pode implantar C# aplicativos de área de trabalho Visual ou Visual Basic em um computador remoto, mas você ainda pode depurá-los remotamente da seguinte maneira. O procedimento a seguir pressupõe que você deseja depurá-lo em um computador chamado **MJO-DL**, conforme mostrado na ilustração anterior.
  
1. Crie um projeto do WPF chamado **MyWpf**.  
  
2. Defina um ponto de interrupção em algum lugar no código que seja facilmente acessado.  
  
    Por exemplo, você pode definir um ponto de interrupção em um manipulador de botão. Para fazer isso, abra MainWindow. XAML e adicione um controle de botão da caixa de ferramentas e clique duas vezes no botão para abrir o manipulador.
  
3. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e escolha **Propriedades**.  
  
4. Na página **Propriedades** , escolha a guia **depurar** .  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Verifique se a caixa de texto **diretório de trabalho** está vazia.  
  
6. Escolha **usar computador remoto**e digite **MJO-DL: 4020** na caixa de texto. (4020 é o número da porta mostrado na janela do depurador remoto).  
  
7. Verifique se **Habilitar depuração de código nativo** não está selecionado.  
  
8. Compile o projeto.  
  
9. Crie uma pasta no computador remoto que seja do mesmo caminho que a pasta de **depuração** no computador do Visual Studio: **\<caminho de origem > \MyWPF\MyWPF\bin\Debug**.  
  
10. Copie o executável que você acabou de criar do computador do Visual Studio para a pasta recém-criada no computador remoto.
  
    > [!CAUTION]
    > Não faça alterações no código ou recompile (ou você deve repetir esta etapa). O executável que você copiou para o computador remoto deve corresponder exatamente à fonte local e aos símbolos.

    Você pode copiar o projeto manualmente, usar xcopy, Robocopy, PowerShell ou outras opções.
  
11. Verifique se o depurador remoto está em execução no computador de destino. (Se não for, procure o **depurador remoto** no menu **Iniciar** . ) A janela do depurador remoto tem esta aparência.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. No Visual Studio, inicie a depuração (**depurar/iniciar depuração**ou **F5**).  
  
13. Se solicitado, insira as credenciais de rede para se conectar ao computador remoto.  
  
     As credenciais necessárias variam de acordo com a configuração de segurança da rede. Por exemplo, em um computador de domínio, você pode inserir seu nome de domínio e senha. Em um computador que não seja de domínio, você pode inserir o nome do computador e um nome de conta de usuário válido, como <strong>MJO-DL\name@something.com</strong>, junto com a senha correta.

     Você deve ver que a janela principal do aplicativo WPF está aberta no computador remoto.
  
14. Se necessário, tome medidas para atingir o ponto de interrupção. Você deve ver que o ponto de interrupção está ativo. Se não estiver, os símbolos para o aplicativo não serão carregados. Tente novamente e, se isso não funcionar, obtenha informações sobre como carregar símbolos e como solucioná-los em [noções básicas sobre arquivos de símbolo e configurações de símbolo do Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. No computador do Visual Studio, você deve ver que a execução foi interrompida no ponto de interrupção.
  
    Se você tiver arquivos que não são de código que precisam ser usados pelo aplicativo, você precisará incluí-los no projeto do Visual Studio. Crie uma pasta de projeto para os arquivos adicionais (na **Gerenciador de soluções**, clique em **Adicionar/nova pasta**.) Em seguida, adicione os arquivos à pasta (na **Gerenciador de soluções**, clique em **Adicionar/item existente**e selecione os arquivos.). Na página **Propriedades** de cada arquivo, defina **copiar para diretório de saída** como **copiar sempre**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Configurar a depuração com símbolos remotos  
 Você deve ser capaz de depurar seu código com os símbolos que você gera no computador do Visual Studio. O desempenho do depurador remoto é muito melhor quando você usa símbolos locais.  Se for necessário usar símbolos remotos, você precisará instruir o monitor de depuração remota a procurar por símbolos no computador remoto.  
  
 A partir do Visual Studio 2013 atualização 2, você pode usar a seguinte opção de linha de comando do msvsmon para usar símbolos remotos para código gerenciado: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Para obter mais informações, consulte a ajuda de depuração remota (pressione **F1** na janela do depurador remoto ou clique em **Ajuda/uso**). Você pode encontrar mais informações em [alterações de carregamento de símbolo remoto do .net no Visual Studio 2012 e 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)  
  
## <a name="bkmk_winstoreAzure"></a>Depuração remota na Windows Store e aplicativos do Azure  
 Para obter informações sobre a depuração remota com aplicativos da Windows Store, consulte [depurar e testar aplicativos da Windows Store em um dispositivo remoto do Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Para obter informações sobre a depuração no Azure, consulte um destes tópicos:  
  
- [Depurando um serviço de nuvem ou máquina virtual no Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Depurando o back-end do .NET no Visual Studio](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Introdução à depuração remota nos sites do Azure ([parte 1](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [parte 2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [parte 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md)   
 [Depuração Remota de ASP.NET em um computador remoto IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)
