---
title: 'Erro: o Monitor de Depuração Remota do Microsoft Visual Studio no computador remoto não tem permissão para se conectar a este computador'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac6e632927878988f8a3ff86d63fea080a45bd6d
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55852982"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Erro: o Monitor de Depuração Remota do Microsoft Visual Studio no computador remoto não tem permissão para se conectar a este computador

Esse erro ocorre quando o usuário que está tentando executar o Monitor de Depuração Remota do Visual Studio (msvsmon) não tem uma conta no computador local.

## <a name="to-fix-this-problem"></a>Para corrigir esse problema

- Adicione uma conta de usuário ao computador host do depurador do Visual Studio, com o mesmo nome e senha que a conta usuário que está executando msvsmon no computador remoto,

   \- ou -

- Execute msvsmon como um usuário que tem permissão para chamar no computador local. Isso significa que o usuário deve ser usuário de domínio e administrador no computador de msvsmon. Você pode especificar a conta de usuário para executar msvsmon de uma de duas maneiras:

  - Clique com o botão direito do mouse no ícone de msvsmon e escolha **Executar como** no menu de atalho

    \- ou -

  - No prompt de comando, execute `runas.exe`.

## <a name="see-also"></a>Consulte também

- [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Depuração remota](../debugger/remote-debugging.md)