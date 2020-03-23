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
ms.openlocfilehash: 9918a2de67693c0232c94a736f12c7af0a0b959c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302073"
---
# <a name="remote-debugging"></a>Depuração Remota
Você pode depurar um aplicativo do Visual Studio que foi implantado em um computador diferente. Para isso, você usa o depurador remoto do Visual Studio.

Para obter instruções detalhadas sobre depuração remota, consulte esses tópicos.

|Cenário|Link|
|-|-|-|
|Serviço de aplicativo do Azure|[Depurador de instantâneos](../debugger/debug-live-azure-applications.md) ou [depuração remota ASP.NET no Azure](../debugger/remote-debugging-azure.md)|
|VM do Azure|[Depuração remota ASP.NET no Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Depurar um aplicativo de malha de serviço do Azure](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Depuração remota ASP.NET Núcleo](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) ou [depuração remota ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# ou Visual Basic|[Depuração remota de um projeto C# ou Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Depuração remota de um projeto C++](../debugger/remote-debugging-cpp.md)|
|Universal Windows Apps (UWP)|[Execute aplicativos UWP em uma máquina remota](../debugger/run-windows-store-apps-on-a-remote-machine.md) ou [detestava um pacote de aplicativo instalado](../debugger/debug-installed-app-package.md)|

Se você só deseja baixar e instalar o depurador remoto e não precisar de instruções adicionais para o seu cenário, siga os passos deste artigo.

## <a name="download-and-install-the-remote-tools"></a>Baixe e instale as ferramentas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a>Requisitos

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a>(Opcional) Para executar o depurador remoto de um compartilhamento de arquivos

Você pode encontrar o depurador remoto *(msvsmon.exe)* em um computador com visual studio community, profissional ou enterprise já instalado. Para alguns cenários, a maneira mais fácil de configurar a depuração remota é executar o depurador remoto (msvsmon.exe) a partir de um compartilhamento de arquivos. Para obter limitações de uso, consulte a página de Ajuda do depurador remoto **(Ajuda > uso** no depurador remoto).

1. Encontre *msvsmon.exe* no diretório que corresponda à sua versão do Visual Studio:

   ::: moniker range=">=vs-2019"

   *Arquivos de programa (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Arquivos de programa (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Arquivos de programa (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Arquivos de programa (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Compartilhe a pasta **Depurador Remoto** no computador do Visual Studio.

3. No computador remoto, execute *msvsmon.exe* da pasta compartilhada. Siga as [instruções de configuração](#bkmk_setup).

> [!TIP]
> Para instalação da linha de comando e referência da linha de comando, ``msvsmon.exe /?`` consulte a página Ajuda para *msvsmon.exe* digitando na linha de comando no computador com o Visual Studio instalado (ou vá para **Ajudar > Uso** no depurador remoto).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Configure o depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a>Configure o depurador remoto
Você pode alterar alguns aspectos da configuração do depurador remoto depois de tê-lo iniciado pela primeira vez.

- Se você precisar adicionar permissões para outros usuários se conectarem ao depurador remoto, escolha **Ferramentas > Permissões**. Você deve ter privilégios de administrador para conceder ou negar permissões.

     > [!IMPORTANT]
     > Você pode executar o depurador remoto em uma conta de usuário que difere da conta de usuário que você está usando no computador do Visual Studio, mas você deve adicionar a conta de usuário diferente às permissões do depurador remoto.

     Alternativamente, você pode iniciar o depurador remoto a partir da linha de comando com o **parâmetro de>de nome de usuário /permitir: \<** **msvsmon \< username@computer /permitir>**.

- Se você precisar alterar o modo autenticação ou o número da porta ou especificar um valor de tempo para as ferramentas remotas: escolha **Ferramentas > Opções**.

     Para obter uma listagem dos números de porta usados por padrão, consulte [Atribuições de porta de depuração remota](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Você também pode optar por executar as ferramentas remotas no Modo Sem Autenticação, mas isso é altamente desaconselhável. Nesse modo, não há nenhuma segurança de rede. Escolha o modo Sem Autenticação somente se tiver certeza de que a rede não está em risco de tráfego malicioso ou hostil.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a>(Opcional) Configure o depurador remoto como um serviço
Para depurar em ASP.NET e outros ambientes do servidor, você deve executar o depurador remoto como administrador ou, se quiser que ele esteja sempre em execução, execute o depurador remoto como um serviço.

 Se você quiser configurar o depurador remoto como um serviço, siga essas etapas.

1. Encontre o **Assistente de Configuração do Depurador Remoto** (rdbgwiz.exe). (Este é um aplicativo separado do Depurador Remoto.) Ele só está disponível quando você instala as ferramentas remotas. Não está instalado com o Visual Studio.

2. Comece a executar o assistente de configuração. Quando a primeira página aparecer, clique **em Next**.

3. Verifique o **Depurador Remoto Do Visual Studio 2015 como uma** caixa de seleção de serviço.

4. Adicione o nome da conta de usuário e senha.

    Você pode precisar adicionar o **Log on como um** direito do usuário de serviço a esta conta (Encontre política de segurança **local** (secpol.msc) na página **inicial** ou janela (ou digite **secpol** em um prompt de comando). Quando a janela aparecer, clique duas vezes em **Atribuição de Direitos do Usuário**e, em seguida, encontre Log on como um **serviço** no painel direito. Clique duas vezes nesse item. Adicione a conta de usuário à janela **Propriedades** e clique em **OK**). Clique em **Avançar**.

5. Selecione o tipo de rede com a que deseja que as ferramentas remotas se comuniquem. Pelo menos um tipo de rede deve ser selecionado. Se os computadores estiverem conectados através de um domínio, você deve escolher o primeiro item. Se os computadores estiverem conectados através de um grupo de trabalho ou grupo doméstico, você deve escolher o segundo ou terceiro itens. Clique em **Avançar**.

6. Se o serviço puder ser iniciado, você verá **que você completou com sucesso o Assistente de Configuração do Depurador Remoto do Visual Studio**. Se o serviço não puder ser iniciado, você verá **Falha ao concluir o Assistente de Configuração do Depurador Remoto do Visual Studio**. A página também dá algumas dicas a seguir para que o serviço comece.

7. Clique em **concluir**.

   Neste momento, o depurador remoto está sendo executado como um serviço. Você pode verificar isso indo para **O Painel de Controle > Serviços** e procurando por Visual Studio **2015 Remote Debugger**.

   Você pode parar e iniciar o serviço de depurador remoto a partir do **Control Panel > Services**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar a depuração com símbolos remotos

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Confira também

- [Primeiro olhe para o depurador](../debugger/debugger-feature-tour.md)
- [Configure o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Atribuições de Porta do Depurador Remoto](../debugger/remote-debugger-port-assignments.md)
- [Depuração remota ASP.NET Núcleo em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)