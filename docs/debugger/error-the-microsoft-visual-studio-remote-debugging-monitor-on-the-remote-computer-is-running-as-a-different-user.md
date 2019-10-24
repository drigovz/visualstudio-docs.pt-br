---
title: 'Erro: o Monitor de Depuração Remota do Microsoft Visual Studio no computador remoto está sendo executado como um usuário diferente'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5ff383b279bbdac85ce85de6e65b857cec6a8e7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737484"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Erro: o Monitor de Depuração Remota do Microsoft Visual Studio no computador remoto está sendo executado como um usuário diferente
Ao tentar fazer a depuração remota, você pode receber a seguinte mensagem de erro:

 O Monitor de Depuração Remota do Microsoft Visual Studio no computador está sendo executado como um usuário diferente.

## <a name="cause"></a>Causa
 Essa mensagem ocorre quando você está depurando no modo Sem Autenticação e o usuário que iniciou o msvsmon não é o usuário que está executando o Visual Studio.

## <a name="solution"></a>Solução
 A solução melhor e mais segura é executar o Monitor de Depuração Remota (msvsmon.exe) na mesma conta de usuário que o Visual Studio. Se você não puder fazer isso, execute o Monitor de Depuração Remota em outra conta com a opção **Permitir que qualquer usuário depure** selecionada na caixa de diálogo **Opções** dele.

> [!CAUTION]
> Conceder permissões a outros usuários para se conectar permite a possibilidade de acidentalmente conectar à sessão de depuração remota incorreta. A depuração no modo **Sem Autenticação** nunca é segura e deve ser usada com cuidado.

## <a name="see-also"></a>Consulte também
- [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Depuração remota](../debugger/remote-debugging.md)