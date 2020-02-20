---
title: Não é possível conectar-se ao Microsoft Visual Studio Monitor de Depuração Remota | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.remote_debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d62e7ce1c419a9c53e40e1ecf2f71497d60d7a23
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477057"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Não foi possível se conectar ao Monitor de Depuração Remota do Microsoft Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa mensagem de erro é exibida quando você insere um nome de Monitor de Depuração Remota do Visual Studio inválido na caixa de diálogo **anexar ao processo** . O nome do Monitor de Depuração Remota geralmente é igual ao computador você está tentando conectar para a depuração remota. Essa mensagem pode ocorrer porque o computador remoto não existe na rede, o monitor de depuração remota não está configurado corretamente no computador remoto ou o computador remoto está inacessível devido a problemas de rede ou à presença de um firewall.  
  
> [!IMPORTANT]
> Se precisar de mais ajuda, consulte [Fale conosco](../ide/talk-to-us.md) para obter formas de entrar em contato com a Microsoft.  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Recebi essa mensagem enquanto eu estava Depurando localmente  
 Se você estiver recebendo essa mensagem enquanto estiver Depurando localmente, o software antivírus ou um firewall de terceiros poderá ser a culpa. O Visual Studio é um aplicativo de 32 bits, portanto, ele usa a versão de 64 bits do depurador remoto para depurar aplicativos de 64 bits. Os dois processos se comunicam usando a rede local no computador local. Nenhum tráfego de rede deixa o computador, mas é possível que o software de segurança de terceiros possa bloquear a comunicação.  
  
 As seções a seguir listam algumas outras razões pelas quais você pode ter chegado a essa mensagem e o que você pode fazer para corrigir o problema.  
  
## <a name="to-correct-this-error"></a>Para corrigir esse erro  
  
- Verifique se o Monitor de Depuração Remota do Visual Studio está instalado e em execução no computador remoto. Para obter informações sobre o depurador remoto e como instalá-lo, consulte [depuração remota](../debugger/remote-debugging.md).  
  
- No Visual Studio, examine as propriedades do projeto (**projeto/Propriedades/depuração**). Verifique se o **nome do servidor remoto** está correto.  
  
- Verifique se o computador remoto está acessível na rede.  
  
## <a name="the-remote-machine-is-not-reachable"></a>O computador remoto não está acessível  
 Tente [executar o ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) no computador remoto. Se ele não responder ao ping, as ferramentas remotas não poderão se conectar. Tente reinicializar o computador remoto e, caso contrário, verifique se ele está configurado corretamente na rede.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>A versão do depurador remoto não corresponde à versão do Visual Studio  
 A versão do Visual Studio que você está executando localmente precisa corresponder à versão do monitor de depuração remota em execução no computador remoto. Para corrigir isso, baixe e instale a versão correspondente do monitor de depuração remota. Vá para [assinaturas do Visual Studio](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) para encontrar a versão correta do depurador remoto para sua versão do Visual Studio.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>As máquinas locais e remotas têm modos de autenticação diferentes  

 Os computadores locais e remotos precisam usar o mesmo modo de autenticação. Para corrigir isso, verifique se ambos os computadores estão usando o mesmo modo de autenticação. Você pode alterar o modo de autenticação no depurador remoto na caixa de diálogo **ferramentas/opções** .  
  
 Para obter mais informações sobre modos de autenticação, consulte [visão geral da autenticação do Windows](https://technet.microsoft.com/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>O depurador remoto está sendo executado em uma conta de usuário diferente  
 Você pode resolver isso de uma das seguintes maneiras:  
  
- Você pode interromper o depurador remoto e reiniciá-lo com a conta que você está usando no computador local.  
  
- Você pode iniciar o depurador remoto a partir da linha de comando com o parâmetro **/allow \<nome de usuário >** : `msvsmon /allow <username@computer>`  
  
- Você pode adicionar o usuário às permissões do depurador remoto (na janela do depurador remoto, **ferramentas/permissões**).  
  
- Se você não puder usar os métodos nas etapas anteriores, poderá permitir que qualquer usuário faça a depuração remota. Na janela depurador remoto, vá para a caixa de diálogo **ferramentas/opts** . Quando você **não seleciona nenhuma autenticação**, pode então verificar **permitir que qualquer usuário depure**. No entanto, você deve usar essa opção somente se não tiver nenhuma opção ou se estiver em uma rede privada.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>O firewall no computador remoto não permite conexões de entrada para o depurador remoto  
 O firewall no computador do Visual Studio e o firewall no computador remoto devem ser configurados para permitir a comunicação entre o Visual Studio e o depurador remoto. Para obter informações sobre as portas que o depurador remoto está usando, consulte [atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md). Para obter informações sobre como configurar o Firewall do Windows, consulte [Configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>O software antivírus está bloqueando as conexões  
 O software antivírus do Windows permite conexões de depurador remoto, mas algum software antivírus de terceiros pode bloqueá-las. Verifique a documentação do seu software antivírus para saber como permitir essas conexões.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>A política de segurança de rede está bloqueando a comunicação entre o computador remoto e o Visual Studio  
 Examine a segurança da rede para certificar-se de que ela não está bloqueando a comunicação. Para obter mais informações sobre a política de segurança de rede do Windows, consulte [Gerenciamento de segurança](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>A rede está muito ocupada para dar suporte à depuração remota  
 Talvez seja necessário fazer a depuração remota em um momento diferente ou reagendar o trabalho na rede por um horário diferente.  
  
## <a name="more-help"></a>Mais ajuda  
 Para obter mais ajuda do depurador remoto, incluindo opções de linha de comando, abra o seguinte em um navegador:  
  
 **res://C: \ Program %2 0 arquivos \ Microsoft %2 0 Visual %2 0 Studio% 2014.0 \ Common7 \ IDE \ Remote %2 0 depurador \ x64 \ msvsmon. exe/help. htm**  
  
## <a name="see-also"></a>Consulte Também  
 [Depuração Remota](../debugger/remote-debugging.md)
