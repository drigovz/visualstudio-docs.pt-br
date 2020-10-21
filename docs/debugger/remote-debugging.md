---
title: Depuração remota | Microsoft Docs
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8051b83e0022361e4cb1cb61602dfcf8991062e
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "92298698"
---
# <a name="remote-debugging"></a>Depuração remota
Você pode depurar um aplicativo do Visual Studio que foi implantado em um computador diferente. Para fazer isso, use o depurador remoto do Visual Studio.

Para obter instruções detalhadas sobre a depuração remota, consulte estes tópicos.

|Cenário|Link|
|-|-|-|
|Serviço de Aplicativo do Azure|[Depuração remota ASP.net no Azure](../debugger/remote-debugging-azure.md) ou, por Visual Studio Enterprise, o [depurador de instantâneos](../debugger/debug-live-azure-applications.md)|
|VM do Azure|[Depuração remota ASP.NET no Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Depurar um aplicativo de Service Fabric do Azure](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[ASP.NET Core de depuração remota](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) ou [depuração remota ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# ou Visual Basic|[Depuração remota de um projeto C# ou Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Depuração remota de um projeto C++](../debugger/remote-debugging-cpp.md)|
|Aplicativos universais do Windows (UWP)|[Executar aplicativos UWP em um computador remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md) ou [depurar um pacote do aplicativo instalado](../debugger/debug-installed-app-package.md)|

Se você quiser apenas baixar e instalar o depurador remoto e não precisar de instruções adicionais para seu cenário, siga as etapas neste artigo.

## <a name="download-and-install-the-remote-tools"></a>Baixar e instalar as ferramentas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> Requisitos

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> Adicional Para executar o depurador remoto de um compartilhamento de arquivos

Você pode encontrar o depurador remoto (*msvsmon.exe*) em um computador com Visual Studio Community, Professional ou Enterprise já instalado. Para alguns cenários, a maneira mais fácil de configurar a depuração remota é executar o depurador remoto (msvsmon.exe) de um compartilhamento de arquivos. Para obter limitações de uso, consulte a página de ajuda do depurador remoto (**ajuda > uso** no depurador remoto).

1. Encontre *msvsmon.exe* no diretório que corresponde à sua versão do Visual Studio:

   ::: moniker range=">=vs-2019"

   *Arquivos de programas (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Arquivos de programas (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Arquivos de programas (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Arquivos de programas (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Compartilhe a pasta do **depurador remoto** no computador do Visual Studio.

3. No computador remoto, execute *msvsmon.exe* da pasta compartilhada. Siga as [instruções de instalação](#bkmk_setup).

> [!TIP]
> Para instalação de linha de comando e referência de linha de comando, consulte a página de ajuda para *msvsmon.exe* digitando ``msvsmon.exe /?`` na linha de comando no computador com o Visual Studio instalado (ou vá para **ajuda > uso** no depurador remoto).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a> Configurar o depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> Configurar o depurador remoto
Você pode alterar alguns aspectos da configuração do depurador remoto depois de iniciá-lo pela primeira vez.

- Se você precisar adicionar permissões para que outros usuários se conectem ao depurador remoto, escolha **ferramentas > permissões**. Você deve ter privilégios de administrador para conceder ou negar permissões.

     > [!IMPORTANT]
     > Você pode executar o depurador remoto em uma conta de usuário que seja diferente da conta de usuário que você está usando no computador do Visual Studio, mas você deve adicionar a conta de usuário diferente às permissões do depurador remoto.

     Como alternativa, você pode iniciar o depurador remoto a partir da linha de comando com o parâmetro ** \<username> /Allow** : **msvsmon/Allow \<username@computer> **.

- Se você precisar alterar o modo de autenticação ou o número da porta, ou especificar um valor de tempo limite para as ferramentas remotas: escolha **ferramentas > opções**.

     Para obter uma lista dos números de porta usados por padrão, consulte [atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Você também pode optar por executar as ferramentas remotas no Modo Sem Autenticação, mas isso é altamente desaconselhável. Nesse modo, não há nenhuma segurança de rede. Escolha o modo sem autenticação somente se você tiver certeza de que a rede não está em risco de tráfego mal-intencionado ou hostil.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> Adicional Configurar o depurador remoto como um serviço
Para a depuração no ASP.NET e em outros ambientes de servidor, você deve executar o depurador remoto como administrador ou, se desejar que ele esteja sempre em execução, executar o depurador remoto como um serviço.

 Se você quiser configurar o depurador remoto como um serviço, siga estas etapas.

1. Localize o **Assistente de configuração do depurador remoto** (rdbgwiz.exe). (Esse é um aplicativo separado do depurador remoto.) Ele está disponível somente quando você instala as ferramentas remotas. Ele não é instalado com o Visual Studio.

2. Inicie a execução do assistente de configuração. Quando a primeira página aparecer, clique em **Avançar**.

3. Marque a caixa de seleção **executar o depurador remoto do Visual Studio 2015 como um serviço** .

4. Adicione o nome da conta de usuário e a senha.

    Talvez seja necessário adicionar o direito de usuário **fazer logon como um serviço** a essa conta (localizar **política de segurança local** (secpol. msc) na página **inicial** ou na janela (ou digite **secpol** em um prompt de comando). Quando a janela for exibida, clique duas vezes em **atribuição de direitos de usuário**e, em seguida, localize **fazer logon como um serviço** no painel direito. Clique duas vezes nesse item. Adicione a conta de usuário à janela **Propriedades** e clique em **OK**). Clique em **Próximo**.

5. Selecione o tipo de rede com o qual você deseja que as ferramentas remotas se comuniquem. Pelo menos um tipo de rede deve ser selecionado. Se os computadores estiverem conectados por meio de um domínio, você deverá escolher o primeiro item. Se os computadores estiverem conectados por meio de um grupo de trabalho ou grupos domésticos, você deverá escolher o segundo ou terceiro itens. Clique em **Próximo**.

6. Se o serviço puder ser iniciado, você verá **que concluiu com êxito o assistente de configuração de depurador remoto do Visual Studio**. Se o serviço não puder ser iniciado, você verá **falha ao concluir o assistente de configuração de depurador remoto do Visual Studio**. A página também fornece algumas dicas a serem seguidas para que o serviço seja iniciado.

7. Clique em **Concluir**.

   Neste ponto, o depurador remoto está sendo executado como um serviço. Você pode verificar isso indo até o **painel de controle > serviços** e procurando o **depurador remoto do Visual Studio 2015**.

   Você pode parar e iniciar o serviço de depurador remoto no **painel de controle > serviços**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar a depuração com símbolos remotos

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Confira também

- [Introdução ao depurador](../debugger/debugger-feature-tour.md)
- [Configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md)
- [ASP.NET Core de depuração remota em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)