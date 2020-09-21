---
title: Executar aplicativos da Windows Store em um computador remoto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e53e05d9df5a7bbdca5fd8a9b74dd9325dc7aae5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838382"
---
# <a name="run-windows-store-apps-on-a-remote-machine"></a>Executar aplicativos da Windows Store em um computador remoto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplica-se somente ao Windows] (.. /Imagem/windows_only_content.png "windows_only_content")  
  
 O aplicativo Ferramentas Remotas do Visual Studio permite executar, depurar, analisar e testar um aplicativo da Windows Store sendo executado em um dispositivo de um segundo computador que esteja executando o Visual Studio. A execução em um dispositivo remoto pode ser especialmente eficaz quando o computador do Visual Studio não oferece suporte à funcionalidade específica dos aplicativos da Windows Store, como toque, localização geográfica e orientação física. Este tópico descreve os procedimentos para configurar e iniciar uma sessão remota.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Neste tópico  
 Você aprende sobre:  
  
 [Pré-requisitos](#BKMK_Prerequisites)  
  
 [Segurança](#BKMK_Security)  
  
 [{1&amp;gt;Como se conectar diretamente a um dispositivo remoto&amp;lt;1}](#BKMK_DirectConnect)  
  
 [Instalando as Ferramentas Remotas](#BKMK_Installing_the_Remote_Tools)  
  
 [{1&amp;gt;Iniciando o Monitor de Depuração Remota&amp;lt;1}](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [{1&amp;gt;Configurando o depurador remoto&amp;lt;1}](#BKMK_ConfigureRemoteDebugger)  
  
 [Configurando o projeto do Visual Studio para depuração remota](#BKMK_ConnectVS)  
  
- [{1&amp;gt;{2&amp;gt;Escolhendo o dispositivo remoto para projetos em C# e Visual Basic&amp;lt;2}&amp;lt;1}](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
- [{1&amp;gt;{2&amp;gt;Escolhendo o dispositivo remoto para projetos em JavaScript e C++&amp;lt;2}&amp;lt;1}](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
  [{1&amp;gt;{2&amp;gt;Executando uma sessão de depuração remota&amp;lt;2}&amp;lt;1}](#BKMK_RunRemoteDebug)  
  
## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Pré-requisitos  
 Para depurar em um dispositivo remoto:  
  
- O dispositivo remoto e o computador com o Visual Studio devem estar conectados por uma rede ou diretamente por um cabo Ethernet. Não há suporte à depuração pela Internet.  
  
- Uma licença de desenvolvedor deve estar instalada no dispositivo remoto.  
  
- O dispositivo remoto deve estar executando os componentes de depuração remota.  
  
- Você deve ser um administrador do dispositivo remoto para configurar o firewall durante a instalação. Você deve ter acesso de usuário ao dispositivo remoto para executar o depurador remoto ou conectar-se a ele.  
  
## <a name="security"></a><a name="BKMK_Security"></a> Segurança  
 Por padrão, o depurador remoto usa a Autenticação do Windows.  
  
> [!WARNING]
> Você também pode optar por executar o depurador remoto no Modo Sem Autenticação, mas isso é altamente desaconselhável. Nesse modo, não há nenhuma segurança de rede. Escolha o Modo Sem Autenticação somente se você tiver certeza de que a rede não corre risco de tráfego mal-intencionado ou hostil.  
  
## <a name="how-to-connect-directly-to-a-remote-device"></a><a name="BKMK_DirectConnect"></a> Como se conectar diretamente a um dispositivo remoto  
 Para se conectar diretamente a um dispositivo remoto, conecte o computador com o Visual Studio ao dispositivo usando um cabo Ethernet padrão. Se o dispositivo não tiver uma porta Ethernet, você poderá usar um adaptador USB-Ethernet para se conectar ao cabo.  
  
## <a name="installing-the-remote-tools"></a><a name="BKMK_Installing_the_Remote_Tools"></a> Instalando o Ferramentas Remotas  
  
> [!NOTE]
> **Versões e atualizações**  
>   
> Não há suporte para o **Ferramentas Remotas para Visual Studio 2015** em versões anteriores do Visual Studio.  
>   
> Recomendamos que você instale a versão de atualização do Ferramentas Remotas para Visual Studio 2015 que corresponde à versão de atualização da instalação do Visual Studio.  
>   
> O depurador do VS é compatível com qualquer combinação de versões do VS 2015 e do Ferramentas Remotas para VS 2015. No entanto, a funcionalidade mais recente no Visual Studio requer que o Visual Studio e as Ferramentas Remotas estejam na versão mais atualizada.  
>   
> Outras ferramentas de diagnóstico podem exigir as mesmas versões das ferramentas remotas e do Visual Studio.  
  
 **Instalando os componentes de depuração remota em um dispositivo remoto**  
  
 Para executar ou salvar o programa de instalação para as ferramentas remotas, escolha um dos links nesta tabela que corresponde à sua versão do Visual Studio:  
  
|Versão|Link|Observações|
|-|-|-|
|Visual Studio 2015 Atualização 3|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se solicitado, ingresse no grupo de Visual Studio Dev Essentials gratuito ou você pode apenas entrar com uma assinatura válida do Visual Studio. Em seguida, abra novamente o link, se necessário. Sempre baixar a versão correspondente ao sistema operacional do dispositivo (versão x86, x64 ou ARM)|
|Visual Studio 2015 (mais antigo)|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se solicitado, ingresse no grupo de Visual Studio Dev Essentials gratuito ou você pode apenas entrar com uma assinatura válida do Visual Studio. Em seguida, abra novamente o link, se necessário. Sempre baixar a versão correspondente ao sistema operacional do dispositivo (versão x86, x64 ou ARM)|
|Visual Studio 2013|[Ferramentas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Página de download na documentação do Visual Studio 2013|
  
 É possível optar por baixar o programa de instalação ou executá-lo imediatamente. Ao executar o programa de instalação, aceite o contrato de usuário e escolha **instalar**.  
  
 Por padrão, os componentes de depuração remota são instalados na pasta **C:\Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger** .  
  
## <a name="starting-the-remote-debugger-monitor"></a><a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> Iniciando o monitor de depurador remoto  
  
> [!NOTE]
> Como o depurador remoto configura o firewall para permitir a comunicação com o host do Visual Studio, você deve ser um administrador no dispositivo remoto ao iniciar o depurador remoto pela primeira vez.  
  
 Depois de instalar o Ferramentas Remotas, escolha **depurador remoto** na tela **Iniciar** . A **configuração de depuração remota** aparece na primeira vez que você inicia o depurador remoto.  
  
 Na caixa de diálogo **configuração de depuração remota** :  
  
1. Se a API dos serviços Web do Windows não estiver instalada, escolha **instalar**  
  
2. No grupo **Configurar firewall do Windows** , escolha as redes às quais você deseja permitir conexões. Somente as redes às quais o dispositivo está conectado no momento estão habilitadas. Você deve escolher pelo menos uma rede.  
  
3. Escolha **Configurar depuração remota** para definir as opções de firewall e iniciar o depurador remoto.  Abra a caixa de diálogo **Monitor de depuração remota do Visual Studio** para dar aos usuários permissões para as ferramentas remotas e para definir outras opções avançadas.  
  
4. A caixa de diálogo **Monitor de depuração remota do Visual Studio** é exibida. Você pode fornecer aos usuários permissões para as ferramentas remotas e definir outras opções avançadas nessa caixa de diálogo.  
  
## <a name="configuring-the-remote-debugger"></a><a name="BKMK_ConfigureRemoteDebugger"></a> Configurando o depurador remoto  
 São usadas duas ferramentas para modificar a configuração do depurador remoto.  
  
1. No menu **ferramentas** do monitor de depuração remota do **Visual Studio**:  
  
   1. Escolha **Opções** para alterar o número da porta, o modo de autenticação ou o intervalo de tempo limite do depurador remoto.  
  
   2. Escolha **permissões** para adicionar ou remover usuários que têm permissão para depuração remota.  
  
       > [!NOTE]
       > As permissões devem ser concedidas a cada conta de usuário que depurar remotamente.  
  
   Use o **Assistente de configuração do depurador remoto** para definir opções avançadas para o depurador remoto. Para abrir o assistente, escolha **Assistente de configuração do depurador remoto** na tela iniciar.  
  
2. Na página **Configurar o depurador remoto do Visual Studio** , você pode optar por executar o depurador remoto como um serviço. Na maioria dos casos, não é obrigatória a execução como um serviço.  
  
3. Na página **Configurar o Firewall do Windows para depuração** , você pode adicionar ou remover o tipo de rede ao qual deseja que o depurador remoto se conecte. Somente as redes às quais o dispositivo está conectado no momento estão habilitadas. Você deve escolher pelo menos uma rede.  
  
## <a name="configuring-the-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a> Configurando o projeto do Visual Studio para depuração remota  
 Você especifica o dispositivo remoto ao qual deseja se conectar nas propriedades do projeto. O procedimento varia dependendo da linguagem de programação. Você pode digitar o nome da rede do dispositivo remoto ou pode selecioná-lo na caixa de diálogo Selecionar Conexão de Depurador Remoto.  
  
 ![Caixa de diálogo Selecionar conexão do depurador remoto](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 A caixa de diálogo lista somente os dispositivos que estão na sub-rede local do computador com o Visual Studio e que estão executando o depurador remoto.  
  
> [!TIP]
> Se você tiver problemas para se conectar a um dispositivo remoto, tente inserir o endereço IP do dispositivo. Para determinar o endereço IP de um dispositivo, abra uma janela de comando e digite **ipconfig**. O endereço IP é listado como **endereço IPv4**.  
  
### <a name="choosing-the-remote-device-for-c-and-visual-basic-projects"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Escolhendo o dispositivo remoto para projetos em C# e Visual Basic  
 ![Propriedades do projeto gerenciado para depuração remota](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1. Selecione o nome do projeto em Gerenciador de Soluções e, em seguida, escolha **Propriedades** no menu de atalho.  
  
2. Selecione **depurar**.  
  
3. Escolha **Computador Remoto** na lista **Dispositivo de Destino**.  
  
4. Insira o nome da rede do dispositivo remoto na caixa **máquina remota** ou escolha **Localizar** para escolher o dispositivo na caixa de diálogo **selecionar conexão do depurador remoto** .  
  
### <a name="choosing-the-remote-device-for-javascript-and-c-projects"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Escolhendo o dispositivo remoto para projetos JavaScript e C++  
 ![C&#43;&#43; Propriedades do projeto para depuração remota](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1. Selecione o nome do projeto em Gerenciador de Soluções e, em seguida, escolha **Propriedades** no menu de atalho.  
  
2. Expanda o nó **Propriedades de configuração** e, em seguida, selecione **depuração**.  
  
3. Escolha **Depurador Remoto** na lista **Depurador a ser iniciado**.  
  
4. Insira o nome da rede do dispositivo remoto na caixa **nome da máquina** ou escolha a seta para baixo na caixa para escolher o dispositivo na caixa de diálogo **selecionar conexão do depurador remoto** .  
  
## <a name="running-a-remote-debugging-session"></a><a name="BKMK_RunRemoteDebug"></a> Executando uma sessão de depuração remota  
 Você inicia e interrompe uma sessão de depuração remota e navega por ela da mesma maneira que faz em uma sessão local. Antes de iniciar a depuração, verifique se o Monitor de Depuração Remota está em execução no dispositivo remoto.  
  
 Em seguida, escolha **Iniciar Depuração** no menu **depurar** (teclado: F5). O projeto é recompilado, depois é implantado e iniciado no dispositivo remoto. O depurador suspende a execução em pontos de interrupção, e você pode fazer step-into, step-over e step-out do seu código. Escolha **parar depuração** para encerrar a sessão de depuração e fechar o aplicativo remoto. Para obter mais informações, consulte [depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Testando aplicativos da loja com o Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
