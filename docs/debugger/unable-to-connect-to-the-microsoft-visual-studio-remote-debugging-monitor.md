---
title: Não é possível conectar-se ao monitor de depuração remota do Microsoft Visual Studio | Microsoft Docs
ms.date: 04/14/2020
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
ms.openlocfilehash: d6173d6b3525a1bd723bc859d34b889b3796d295
ms.sourcegitcommit: c3b92a9912a5816f16c6059d1738dbc833851346
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81397370"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Não foi possível se conectar ao Monitor de Depuração Remota do Microsoft Visual Studio
Essa mensagem pode ocorrer porque o monitor de depuração remota não está configurado corretamente na máquina remota ou a máquina remota está inacessível devido a problemas de rede ou à presença de um firewall.

> [!IMPORTANT]
> Se você acredita que recebeu esta mensagem por causa de um bug do produto, por favor, [reporte este problema](../ide/how-to-report-a-problem-with-visual-studio.md) ao Visual Studio. Se você precisar de mais ajuda, consulte [Fale conosco para](../ide/feedback-options.md) obter maneiras de entrar em contato com a Microsoft.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Qual é a mensagem de erro detalhada?

A `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` mensagem é genérica. Normalmente, uma mensagem mais específica é incluída na seqüência de erros e isso pode ajudá-lo a identificar a causa do problema ou procurar uma correção mais exata. Aqui estão algumas das mensagens de erro mais comuns que são anexadas à mensagem de erro principal:

- [O depurador não pode se conectar ao computador remoto. O depurador não conseguiu resolver o nome do computador especificado](#cannot_connect)
- [Pedido de conexão foi rejeitado pelo depurador remoto](#rejected)
- [A conexão com o ponto final remoto foi encerrada](#connection_terminated)
- [Acesso inválido ao local de memória](#invalid_access)
- [Não há servidor pelo nome especificado em execução no computador remoto](#no_server)
- [O nome solicitado era válido, mas nenhum dado do tipo solicitado foi encontrado](#valid_name)
- [O Depurador Remoto do Visual Studio no computador de destino não pode se conectar de volta a este computador](#cant_connect_back)
- [Acesso negado](#access_denied)
- [Ocorreu um erro específico do pacote de segurança](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a>O depurador não pode se conectar ao computador remoto. O depurador não conseguiu resolver o nome do computador especificado

Experimente estas etapas:

1. Certifique-se de inserir um nome de computador válido e um número de porta na caixa de diálogo **Anexar ao processo** ou nas propriedades do projeto (Para definir propriedades, consulte essas [etapas](#server_incorrect)). O nome do computador deve ser o seguinte formato:

    `computername:port`

    > [!NOTE]
    > O número da porta deve corresponder ao [número da porta do depurador remoto](../debugger/remote-debugger-port-assignments.md), que deve estar em *execução* na máquina de destino.

2. Se o nome do computador não funcionar, tente o endereço IP e o número da porta.

3. Certifique-se de que a versão do depurador remoto em execução na máquina de destino corresponda à sua versão do Visual Studio. Para obter a versão correta do depurador remoto, consulte [Depuração remota](../debugger/remote-debugging.md).

    > [!TIP]
    > Se você estiver anexando ao processo e se conectar com sucesso, mas não ver o processo que deseja, selecione os **processos Mostrar em todas as caixas de seleção de usuários**. Isso mostrará processos se você estiver conectado sob uma conta de usuário diferente.

4. Se essas etapas não resolverem esse erro, consulte [A máquina remota não pode ser alcançável](#dns).

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a>Pedido de conexão foi rejeitado pelo depurador remoto

Na caixa de diálogo **Anexar ao processo** ou nas propriedades do projeto, certifique-se de que o nome do computador remoto e o número da porta correspondam ao nome e ao número da porta mostrados na janela de depurador remota. Se estiver incorreto, conserte e tente novamente.

Se esses valores estiverem corretos e a mensagem mencionar o modo **de autenticação** do Windows, verifique se o depurador remoto está no modo de autenticação correto **(Ferramentas > Opções).**

## <a name="connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a>A conexão com o ponto final remoto foi encerrada

Se você estiver depurando um aplicativo do Azure App Service, tente usar o comando [Attach Debugger](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) do Cloud Explorer ou Server Explorer em vez de **Anexar ao Processo**.

Se você estiver usando **'Anexar ao processo'** para depurar:

- Na caixa de diálogo **Anexar ao processo** ou nas propriedades do projeto, certifique-se de que o nome do computador remoto e o número da porta correspondam ao nome e ao número da porta mostrados na janela de depurador remota. Se estiver incorreto, conserte e tente novamente.

- Se você estiver tentando se conectar usando um nome de host, tente um endereço IP em vez disso.

- Verifique o registro do aplicativo no servidor (Visualizador de Eventos no Windows) para obter informações mais detalhadas para ajudar a resolver o problema.

- Caso contrário, tente reiniciar o Visual Studio com privilégios de administrador e tente novamente.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a>Acesso inválido ao local de memória

Ocorreu um erro interno. Reiniciar o Visual Studio e tentar novamente.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a>Não há servidor pelo nome especificado em execução no computador remoto

O Visual Studio não pôde se conectar ao depurador remoto. Esta mensagem pode ocorrer por várias razões:

- O depurador remoto pode estar sendo executado em outra conta de usuário. Veja [esses passos](#user_accounts)

- A porta está bloqueada no firewall. Certifique-se de que o firewall não está [bloqueando sua solicitação,](#firewall)especialmente se você estiver usando um firewall de terceiros.

- A versão de depurador remota não corresponde ao Visual Studio. Para obter a versão correta do depurador remoto, consulte [Depuração remota](../debugger/remote-debugging.md).

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a>O nome solicitado era válido, mas nenhum dado do tipo solicitado foi encontrado

O computador remoto existe, mas o Visual Studio não conseguiu se conectar ao depurador remoto. Esta mensagem pode ocorrer por várias razões:

- Um problema de DNS está impedindo a conexão. Veja [esses passos](#dns).

- O depurador remoto pode estar sendo executado em outra conta de usuário. Siga [estes passos](#user_accounts).

- A porta está bloqueada no firewall. Certifique-se de que o firewall não está [bloqueando sua solicitação,](#firewall)especialmente se você estiver usando um firewall de terceiros.

- A versão de depurador remota não corresponde ao Visual Studio. Para obter a versão correta do depurador remoto, consulte [Depuração remota](../debugger/remote-debugging.md).

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a>O Depurador Remoto do Visual Studio no computador de destino não pode se conectar de volta a este computador

O depurador remoto pode estar sendo executado em outra conta de usuário. No depurador remoto, abra **as > permissões** para adicionar o usuário às permissões do depurador remoto. Para obter mais informações, consulte [O depurador remoto está sendo executado em uma conta de usuário diferente](#user_accounts).

Se a mensagem de erro também mencionar um firewall, o firewall na máquina local pode estar impedindo a comunicação do computador remoto de volta ao Visual Studio. Veja [esses passos](#firewall).

## <a name="access-denied"></a><a name="access_denied"></a>Acesso negado

Você pode ver esse erro se tentar depurar em um computador remoto de 64 bits a partir de um computador de 32 bits (não suportado).

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a>Ocorreu um erro específico do pacote de segurança

Este pode ser um problema legado específico para o Windows XP e o Windows 7. Veja essa [informação](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Causas e recomendações

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a>A máquina remota não é acessível

Se você não puder se conectar usando o nome do computador remoto, tente usar o endereço IP. Você pode `ipconfig` usar em uma linha de comando no computador remoto para obter o endereço IPv4. Se você estiver usando um arquivo HOSTS, verifique se ele está configurado corretamente.

Se isso falhar, verifique se o computador remoto está acessível na rede[(ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) da máquina remota). A depuração remota pela Internet não é suportada, exceto em alguns cenários do Microsoft Azure.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a>O nome do servidor está incorreto ou o software de terceiros está interferindo no depurador remoto

No Visual Studio, olhe as propriedades do projeto e certifique-se de que o nome do servidor está correto. Veja tópicos para [C# e Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) e [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). Para ASP.NET, abra **Propriedades / Web / Servidores** ou Propriedades / **Depuração** dependendo do seu tipo de projeto.

> [!NOTE]
> Se você estiver anexando ao processo, as configurações remotas nas propriedades do projeto não serão usadas.

Se o nome do servidor estiver correto, seu software antivírus ou um firewall de terceiros podem estar bloqueando o depurador remoto. Ao depurar localmente, isso pode acontecer porque o Visual Studio é um aplicativo de 32 bits, por isso usa a versão de 64 bits do depurador remoto para depurar aplicativos de 64 bits. Os processos de 32 bits e 64 bits se comunicam usando a rede local dentro do computador local. Nenhum tráfego de rede sai do computador, mas é possível que o software de segurança de terceiros possa bloquear a comunicação.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a>O depurador remoto está sendo executado em uma conta de usuário diferente

O depurador remoto, por padrão, só aceitará conexões do usuário que lançou o depurador remoto e membros do grupo Administradores. Os usuários adicionais devem receber permissões explicitamente concedidas.

Você pode resolver isso de uma das seguintes maneiras:

- Adicione o usuário do Visual Studio às permissões do depurador remoto (na janela de depurador remoto, escolha **Ferramentas > Permissões**).

- No computador remoto, reinicie o depurador remoto sob a mesma conta de usuário e senha que você está usando no computador do Visual Studio.

    > [!NOTE]
    > Se você estiver executando o depurador remoto em um servidor remoto, clique com o botão direito do mouse no aplicativo Depurador Remoto e escolha **Executar como administrador** (Ou, você pode executar o depurador remoto como um serviço). Se você não estiver executando-o em um servidor remoto, basta iniciá-lo normalmente.

- Você pode iniciar o depurador remoto a partir da linha `msvsmon /allow <username@computer>`de comando com o parâmetro de>de nome de usuário **/permitir: \<** .

- Alternativamente, você pode permitir que qualquer usuário faça depuração remota. Na janela de depurador remoto, vá para a caixa de diálogo **Ferramentas > Opções.** Quando você selecionar **Nenhuma Autenticação,** você pode então verificar **Permitir que qualquer usuário depurar**. No entanto, você deve tentar essa opção somente se as outras opções falharem, ou se você estiver em uma rede privada.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a>O firewall na máquina remota não permite conexões recebidas ao depurador remoto
 O firewall na máquina do Visual Studio e o firewall na máquina remota devem ser configurados para permitir a comunicação entre o Visual Studio e o depurador remoto. Para obter informações sobre as portas que o depurador remoto está usando, consulte [Atribuições de porta de depurador remoto](../debugger/remote-debugger-port-assignments.md). Para obter informações sobre a configuração do firewall do Windows, consulte [Configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>A versão do depurador remoto não corresponde à versão do Visual Studio
 A versão do Visual Studio que você está executando localmente precisa corresponder à versão do monitor de depuração remota que está sendo executado na máquina remota. Para corrigir isso, baixe e instale a versão correspondente do monitor de depuração remota. Para obter a versão correta do depurador remoto, consulte [Depuração remota](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>As máquinas locais e remotas têm diferentes modos de autenticação
 As máquinas locais e remotas precisam usar o mesmo modo de autenticação. Para corrigir isso, certifique-se de que ambas as máquinas estejam usando o mesmo modo de autenticação. Você pode alterar o modo de autenticação. Na janela de depurador remota, vá para a caixa de diálogo **Ferramentas > Opções.**

 Para obter mais informações sobre os modos de autenticação, consulte [Visão Geral de Autenticação do Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>O software antivírus está bloqueando as conexões
 O software antivírus do Windows permite conexões remotas de depurador, mas algum software antivírus de terceiros pode bloqueá-los. Verifique a documentação do seu software antivírus para descobrir como permitir essas conexões.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>A política de segurança da rede está bloqueando a comunicação entre a máquina remota e o Visual Studio
 Revise a segurança da rede para ter certeza de que não está bloqueando a comunicação. Para obter mais informações sobre a política de segurança da rede Windows, consulte [configurações de diretiva de segurança](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>A rede está muito ocupada para suportar depuração remota
 Você pode precisar fazer depuração remota em um horário diferente ou reagendar o trabalho na rede por um tempo diferente.

## <a name="more-help"></a>Mais ajuda
 Para obter ajuda de depurador mais remota, abra a página de Ajuda do depurador remoto **(Ajuda > Uso** no depurador remoto).

## <a name="see-also"></a>Confira também
- [Depuração remota](../debugger/remote-debugging.md)
