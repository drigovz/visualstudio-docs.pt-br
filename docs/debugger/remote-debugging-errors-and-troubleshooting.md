---
title: Erros de depuração remota e solução de problemas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b413ce193e6761d515de5bc5ef30fae8e18a3a3
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302087"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Erros de depuração remota e solução de problemas

Você pode se deparar com os seguintes erros ao tentar depurar remotamente.

- [Erro: Não é possível entrar automaticamente no servidor](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Erro: o Monitor de Depuração Remota do Microsoft Visual Studio (MSVSMON.EXE) parece não estar sendo executado no computador remoto.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Não é possível conectar-se ao monitor de depuração remota do Microsoft Visual Studio](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Erro: O computador remoto não aparece em uma caixa de diálogo Conexões Remotas](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Execute o depurador remoto como administrador

Você pode encontrar problemas se não executar o depurador remoto como administrador. Por exemplo, você pode ver o seguinte erro: "O Visual Studio Remote Debugger (MSVSMON. EXE) tem privilégios insuficientes para depurar esse processo." Se você estiver executando o depurador remoto como um aplicativo (não um serviço), você pode ver o erro diferente da [conta de usuário.](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md)

### <a name="when-running-the-remote-debugger-as-a-service"></a>Ao executar o depurador remoto como um serviço

Ao executar o depurador remoto como serviço s, recomendamos executá-lo como administrador por várias razões:

- O serviço de depurador remoto só permite conexões dos administradores, de modo que **não** há novos riscos de segurança introduzidos executando-o como administrador.

- Ele pode evitar erros que resultam quando o usuário do Visual Studio tem mais direitos para depurar um processo do que o próprio depurador remoto.

- Para simplificar a configuração e configuração do depurador remoto.

Embora seja possível depurar sem executar o depurador remoto como administrador, existem vários requisitos para fazer isso funcionar corretamente e eles geralmente requerem etapas de configuração de serviço mais avançadas.

- A conta que você está usando na máquina remota deve ter o logon como privilégio **de serviço.** Consulte as etapas em "Para adicionar logon como serviço" no artigo de erro [não pode conectar de volta.](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)

- A conta deve ter direitos para depurar o processo de destino. Para obter esses direitos, você deve executar o depurador remoto na mesma conta que o processo a ser depurado. (A alternativa mais fácil é executar o serviço como administrador.) 

- A conta deve ser capaz de se conectar de volta ao (isto é, autenticar com) o computador Visual Studio na rede. Em um domínio, é mais fácil conectar-se se o depurador remoto estiver sendo executado as contas incorporadas do Sistema Local ou serviço de rede ou de uma conta de domínio. As contas incorporadas têm privilégios de segurança elevados que podem representar um risco à segurança.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Ao executar o depurador remoto como um aplicativo (modo normal)

Se você está tentando anexar ao seu próprio processo não elevado (como um aplicativo normal), não importa se você está executando o depurador remoto como administrador.

Você deseja executar o depurador remoto como administrador em vários cenários:

- Você deseja anexar a processos em execução como outro usuário (como ao depurar IIS), ou

- Você está tentando iniciar outro processo, e o processo que você deseja iniciar é um administrador.

Você **não** quer executar como administrador se quiser iniciar processos, e o processo que deseja iniciar **não** deve ser um administrador.

## <a name="see-also"></a>Confira também
- [Depuração Remota](../debugger/remote-debugging.md)