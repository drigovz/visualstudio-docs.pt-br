---
title: Não é possível conectar-se ao Microsoft Visual Studio Monitor de Depuração Remota | Microsoft Docs
ms.date: 08/24/2017
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 872f7c594344af2c59ebe7f8d1fbd1a640dd2190
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728823"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Não foi possível se conectar ao Monitor de Depuração Remota do Microsoft Visual Studio
Essa mensagem pode ocorrer porque o monitor de depuração remota não está configurado corretamente no computador remoto ou o computador remoto está inacessível devido a problemas de rede ou à presença de um firewall.

> [!IMPORTANT]
> Se você acreditar que recebeu esta mensagem por causa de um bug do produto, [relate esse problema](../ide/how-to-report-a-problem-with-visual-studio.md) ao Visual Studio. Se precisar de mais ajuda, consulte [Fale conosco](../ide/talk-to-us.md) para obter formas de entrar em contato com a Microsoft.

## <a name="specificerrors"></a>Qual é a mensagem de erro detalhada?

A `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` mensagem é genérica. Normalmente, uma mensagem mais específica é incluída na cadeia de caracteres de erro e pode ajudar a identificar a causa do problema ou pesquisar uma correção mais exata. Aqui estão algumas das mensagens de erro mais comuns que são acrescentadas à mensagem de erro principal:

- [O depurador não pode se conectar ao computador remoto. O depurador não pôde resolver o nome do computador especificado](#cannot_connect)
- [A solicitação de conexão foi rejeitada pelo depurador remoto](#rejected)
- [Acesso inválido ao local da memória](#invalid_access)
- [Não há nenhum servidor pelo nome especificado em execução no computador remoto](#no_server)
- [O nome solicitado era válido, mas nenhum dado do tipo solicitado foi encontrado](#valid_name)
- [O Depurador Remoto do Visual Studio no computador de destino não pode se conectar de volta a este computador](#cant_connect_back)
- [Acesso negado](#access_denied)
- [Ocorreu um erro específico do pacote de segurança](#security_package)

## <a name="cannot_connect"></a>O depurador não pode se conectar ao computador remoto. O depurador não pôde resolver o nome do computador especificado

Tente estas etapas:

1. Certifique-se de inserir um nome de computador e número de porta válidos na caixa de diálogo **anexar ao processo** ou nas propriedades do projeto (para definir propriedades, consulte [estas etapas](#server_incorrect)). O nome do computador deve ter o seguinte formato:

    `computername:port`

    > [!NOTE]
    > O número da porta deve corresponder ao [número da porta do depurador remoto](../debugger/remote-debugger-port-assignments.md), que *deve estar em execução* no computador de destino.

2. Se o nome do computador não funcionar, tente o endereço IP e o número da porta.

3. Verifique se a versão do depurador remoto em execução no computador de destino corresponde à sua versão do Visual Studio. Para obter a versão correta do depurador remoto, consulte [depuração remota](../debugger/remote-debugging.md).

    > [!TIP]
    > Se você estiver anexando ao processo e se conectar com êxito, mas não vir o processo desejado, marque a **caixa de seleção Mostrar processos de todos os usuários**. Isso mostrará os processos se você estiver conectado a uma conta de usuário diferente.

4. Se essas etapas não resolverem esse erro, consulte [o computador remoto não está acessível](#dns).

## <a name="rejected"></a>A solicitação de conexão foi rejeitada pelo depurador remoto

Na caixa de diálogo **anexar ao processo** ou nas propriedades do projeto, verifique se o nome do computador remoto e o número da porta correspondem ao nome e ao número da porta mostrada na janela do depurador remoto. Se estiver incorreto, corrija e tente novamente.

Se esses valores estiverem corretos e a mensagem mencionar o modo de **autenticação do Windows** , verifique se o depurador remoto está no modo de autenticação correto (**Ferramentas > opções**).

## <a name="invalid_access"></a>Acesso inválido ao local da memória

Ocorreu um erro interno. Reinicie o Visual Studio e tente novamente.

## <a name="no_server"></a>Não há nenhum servidor pelo nome especificado em execução no computador remoto

O Visual Studio não pôde se conectar ao depurador remoto. Essa mensagem pode ocorrer por vários motivos:

- O depurador remoto pode estar sendo executado em uma conta de usuário diferente. Consulte [estas etapas](#user_accounts)

- A porta está bloqueada no firewall. Verifique se o firewall [não está bloqueando sua solicitação](#firewall), especialmente se você estiver usando um firewall de terceiros.

- A versão do depurador remoto não corresponde ao Visual Studio. Para obter a versão correta do depurador remoto, consulte [depuração remota](../debugger/remote-debugging.md).

## <a name="valid_name"></a>O nome solicitado era válido, mas nenhum dado do tipo solicitado foi encontrado

O computador remoto existe, mas o Visual Studio não pôde se conectar ao depurador remoto. Essa mensagem pode ocorrer por vários motivos:

- Um problema de DNS está impedindo a conexão. Consulte [estas etapas](#dns).

- O depurador remoto pode estar sendo executado em uma conta de usuário diferente. Siga [essas etapas](#user_accounts).

- A porta está bloqueada no firewall. Verifique se o firewall [não está bloqueando sua solicitação](#firewall), especialmente se você estiver usando um firewall de terceiros.

- A versão do depurador remoto não corresponde ao Visual Studio. Para obter a versão correta do depurador remoto, consulte [depuração remota](../debugger/remote-debugging.md).

## <a name="cant_connect_back"></a>O Depurador Remoto do Visual Studio no computador de destino não pode se conectar de volta a este computador

O depurador remoto pode estar sendo executado em uma conta de usuário diferente. No depurador remoto, abra **ferramentas > permissões** para adicionar o usuário às permissões do depurador remoto. Para obter mais informações, consulte [o depurador remoto está sendo executado em uma conta de usuário diferente](#user_accounts).

Se a mensagem de erro também mencionar um firewall, o firewall no computador local pode estar impedindo a comunicação do computador remoto de volta para o Visual Studio. Consulte [estas etapas](#firewall).

## <a name="access_denied"></a> Acesso negado

Você poderá ver esse erro se tentar depurar em um computador remoto de 64 bits de um computador de 32 bits (sem suporte).

## <a name="security_package"></a>Ocorreu um erro específico do pacote de segurança

Isso pode ser um problema herdado específico do Windows XP e do Windows 7. Consulte essas [informações](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Causas e recomendações

### <a name="dns"></a>O computador remoto não está acessível

Se você não puder se conectar usando o nome do computador remoto, tente usar o endereço IP em vez disso. Você pode usar `ipconfig` em uma linha de comando no computador remoto para obter o endereço IPv4. Se você estiver usando um arquivo de HOSTs, verifique se ele está configurado corretamente.

Se isso falhar, verifique se o computador remoto está acessível na rede ([execute ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) no computador remoto). Não há suporte para a depuração remota pela Internet, exceto em alguns cenários de Microsoft Azure.

### <a name="server_incorrect"></a>O nome do servidor está incorreto ou o software de terceiros está interferindo com o depurador remoto

No Visual Studio, examine as propriedades do projeto e verifique se o nome do servidor está correto. Consulte os tópicos para [ C# e Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) e. [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus) Para ASP.NET, abra **Propriedades/Web/servidores** ou **Propriedades/depuração** , dependendo do tipo de projeto.

> [!NOTE]
> Se você estiver anexando ao processo, as configurações remotas nas propriedades do projeto não serão usadas.

Se o nome do servidor estiver correto, o software antivírus ou um firewall de terceiros poderá estar bloqueando o depurador remoto. Ao depurar localmente, isso pode acontecer porque o Visual Studio é um aplicativo de 32 bits, portanto, ele usa a versão de 64 bits do depurador remoto para depurar aplicativos de 64 bits. Os processos de 32 bits e 64 bits se comunicam usando a rede local no computador local. Nenhum tráfego de rede deixa o computador, mas é possível que o software de segurança de terceiros possa bloquear a comunicação.

### <a name="user_accounts"></a>O depurador remoto está sendo executado em uma conta de usuário diferente

O depurador remoto, por padrão, só aceitará conexões do usuário que iniciou o depurador remoto e os membros do grupo de administradores. Usuários adicionais devem ter permissões concedidas explicitamente.

Você pode resolver isso de uma das seguintes maneiras:

- Adicione o usuário do Visual Studio às permissões do depurador remoto (na janela do depurador remoto, escolha **ferramentas > permissões**).

- No computador remoto, reinicie o depurador remoto na mesma conta de usuário e senha que você está usando no computador do Visual Studio.

    > [!NOTE]
    > Se você estiver executando o depurador remoto em um servidor remoto, clique com o botão direito do mouse no aplicativo do depurador remoto e escolha **Executar como administrador** (ou, você pode executar o depurador remoto como um serviço). Se você não o estiver executando em um servidor remoto, basta iniciá-lo normalmente.

- Você pode iniciar o depurador remoto a partir da linha de comando com o parâmetro **/allow \<username >** : `msvsmon /allow <username@computer>`.

- Como alternativa, você pode permitir que qualquer usuário faça a depuração remota. Na janela depurador remoto, vá para a caixa de diálogo **ferramentas > opções** . Quando você **não seleciona nenhuma autenticação**, pode então verificar **permitir que qualquer usuário depure**. No entanto, você deve tentar esta opção somente se as outras opções falharem ou se você estiver em uma rede privada.

### <a name="firewall"></a>O firewall no computador remoto não permite conexões de entrada para o depurador remoto
 O firewall no computador do Visual Studio e o firewall no computador remoto devem ser configurados para permitir a comunicação entre o Visual Studio e o depurador remoto. Para obter informações sobre as portas que o depurador remoto está usando, consulte [atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md). Para obter informações sobre como configurar o Firewall do Windows, consulte [Configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>A versão do depurador remoto não corresponde à versão do Visual Studio
 A versão do Visual Studio que você está executando localmente precisa corresponder à versão do monitor de depuração remota em execução no computador remoto. Para corrigir isso, baixe e instale a versão correspondente do monitor de depuração remota. Para obter a versão correta do depurador remoto, consulte [depuração remota](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>As máquinas locais e remotas têm modos de autenticação diferentes
 Os computadores locais e remotos precisam usar o mesmo modo de autenticação. Para corrigir isso, verifique se ambos os computadores estão usando o mesmo modo de autenticação. Você pode alterar o modo de autenticação. Na janela depurador remoto, vá para a caixa de diálogo **ferramentas > opções** .

 Para obter mais informações sobre modos de autenticação, consulte [visão geral da autenticação do Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>O software antivírus está bloqueando as conexões
 O software antivírus do Windows permite conexões de depurador remoto, mas algum software antivírus de terceiros pode bloqueá-las. Verifique a documentação do seu software antivírus para saber como permitir essas conexões.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>A política de segurança de rede está bloqueando a comunicação entre o computador remoto e o Visual Studio
 Examine a segurança da rede para certificar-se de que ela não está bloqueando a comunicação. Para obter mais informações sobre a política de segurança de rede do Windows, consulte [configurações de política de segurança](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>A rede está muito ocupada para dar suporte à depuração remota
 Talvez seja necessário fazer a depuração remota em um momento diferente ou reagendar o trabalho na rede por um horário diferente.

## <a name="more-help"></a>Mais ajuda
 Para obter mais ajuda do depurador remoto, abra a página de ajuda do depurador remoto (**ajuda > uso** no depurador remoto).

## <a name="see-also"></a>Consulte também
- [Depuração remota](../debugger/remote-debugging.md)
