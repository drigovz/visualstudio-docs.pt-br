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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89316131"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Erros de depuração remota e solução de problemas

Você pode vir os seguintes erros ao tentar depurar remotamente.

- [Erro: não é possível entrar automaticamente no servidor](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Erro: o Monitor de Depuração Remota do Microsoft Visual Studio (MSVSMON.EXE) parece não estar sendo executado no computador remoto.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Não foi possível se conectar ao Monitor de Depuração Remota do Microsoft Visual Studio](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Erro: O computador remoto não aparece em uma caixa de diálogo Conexões Remotas](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Executar o depurador remoto como administrador

Você poderá encontrar problemas se não executar o depurador remoto como administrador. Por exemplo, você pode ver o seguinte erro: "o Depurador Remoto do Visual Studio (MSVSMON.EXE) tem privilégios insuficientes para depurar esse processo." Se você estiver executando o depurador remoto como um aplicativo (não um serviço), poderá ver o erro de [conta de usuário diferente](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) .

### <a name="when-running-the-remote-debugger-as-a-service"></a>Ao executar o depurador remoto como um serviço

Ao executar o depurador remoto como s Service, recomendamos executá-lo como administrador por vários motivos:

- O serviço de depurador remoto só permite conexões de administradores, portanto, **não há novos riscos** de segurança introduzidos com a execução como administrador.

- Ele pode evitar erros que resultam quando o usuário do Visual Studio tem mais direitos para depurar um processo do que o próprio depurador remoto.

- Para simplificar a instalação e a configuração do depurador remoto.

Embora seja possível depurar sem executar o depurador remoto como administrador, há vários requisitos para que isso funcione corretamente e, muitas vezes, exigem etapas de configuração de serviço mais avançadas.

- A conta que você está usando no computador remoto deve ter o privilégio de **logon como serviço** . Consulte as etapas em "para adicionar logon como um serviço" no artigo [não é possível se conectar](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) ao erro de retorno.

- A conta deve ter direitos para depurar o processo de destino. Para obter esses direitos, você deve executar o depurador remoto na mesma conta que o processo a ser depurado. (A alternativa mais fácil é executar o serviço como administrador.) 

- A conta deve ser capaz de se conectar de volta para (ou seja, autenticar com) o computador do Visual Studio pela rede. Em um domínio, é mais fácil se conectar de volta se o depurador remoto estiver sendo executado no sistema local interno ou nas contas de serviço de rede ou em uma conta de domínio. As contas internas têm privilégios de segurança elevados que podem representar um risco de segurança.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Ao executar o depurador remoto como um aplicativo (modo normal)

Se você estiver tentando se conectar ao seu próprio processo não elevado (como um aplicativo normal), não importa se você está executando o depurador remoto como administrador.

Você deseja executar o depurador remoto como administrador em vários cenários:

- Você deseja anexar a processos em execução como outro usuário (como ao depurar o IIS) ou

- Você está tentando iniciar outro processo, e o processo que você deseja iniciar é um administrador.

Você **não** deseja executar como administrador se desejar iniciar processos, e o processo que você deseja iniciar **não** deve ser um administrador.

## <a name="see-also"></a>Confira também
- [Depuração remota](../debugger/remote-debugging.md)