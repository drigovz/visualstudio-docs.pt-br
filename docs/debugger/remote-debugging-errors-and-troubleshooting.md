---
title: Solução de problemas e erros de depuração remota | Microsoft Docs
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
ms.openlocfilehash: 078551111223f11b38f3192075caa9ddfabaf18c
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043327"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Erros de depuração remota e solução de problemas

Você pode se deparar com os seguintes erros ao tentar depurar remotamente.

- [Erro: Não é possível intervir no servidor automaticamente](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Erro: O Monitor de Depuração Remota do Microsoft Visual Studio (MSVSMON.EXE) parece não estar sendo executado no computador remoto.](/visualstudio/debugger/error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running)

- [Não foi possível se conectar ao Monitor de Depuração Remota do Microsoft Visual Studio](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Erro: O computador remoto não aparece em uma caixa de diálogo Conexões Remotas](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Executar o depurador remoto como um administrador

Você pode se deparar com problemas se você não executar o depurador remoto como um administrador. Por exemplo, você poderá ver o seguinte erro: "O Visual Studio depurador remoto (MSVSMON. EXE) tem privilégios insuficientes para depurar esse processo." Se você estiver executando o depurador remoto como um aplicativo (não é um serviço), você poderá ver o [conta de usuário diferente](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) erro.

### <a name="when-running-the-remote-debugger-as-a-service"></a>Ao executar o depurador remoto como um serviço

Ao executar o depurador remoto como serviço s, é recomendável executá-lo como um administrador por vários motivos:

- O serviço depurador remoto só permite conexões dos administradores, portanto, há **nenhum** novos riscos de segurança introduzidos por executá-lo como um administrador.

- Ele pode impedir que os erros que o resultado quando o usuário do Visual Studio tem mais direitos para depurar um processo que o depurador remoto em si.

- Para simplificar a instalação e configuração do depurador remoto.

Embora seja possível depurar sem executar o depurador remoto como um administrador, há vários requisitos para que funcione corretamente e muitas vezes exigem etapas de configuração de serviço mais avançadas.

- A conta que você está usando no computador remoto deve ter o **fazer logon como serviço** privilégio. Consulte as etapas descritas em "Ao adicionar logon como um serviço" a [não pode se conectar novamente](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) artigo de erro.

- A conta deve ter direitos para depurar o processo de destino. Para obter esses direitos, você deve executar o depurador remoto sob a mesma conta que o processo a ser depurado. (A alternativa mais fácil é executar o serviço como um administrador.) 

- A conta deve ser capaz de se conectar novamente para (ou seja, autenticar com a) o computador do Visual Studio pela rede. Em um domínio, é mais fácil para se conectar novamente se o depurador remoto está em execução sob as contas internas do sistema Local ou serviço de rede ou uma conta de domínio. As contas internas tem privilégios de segurança que podem representar um risco de segurança elevados.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Ao executar o depurador remoto como um aplicativo (modo normal)

Se você estiver tentando anexar a seu próprio processo sem privilégios elevados (por exemplo, um aplicativo normal), não importa se você estiver executando o depurador remoto como um administrador.

Você deseja executar o depurador remoto como um administrador em diversos cenários:

- Você deseja anexar a processos em execução como outro usuário (por exemplo, quando depurando o IIS), ou

- Você está tentando iniciar outro processo e o processo que você deseja iniciar é um administrador.

Você faz **não** deseja executar como administrador, se você deseja iniciar processos, e o processo que você deseja iniciar deve **não** ser um administrador.

## <a name="see-also"></a>Consulte também
- [Depuração remota](../debugger/remote-debugging.md)