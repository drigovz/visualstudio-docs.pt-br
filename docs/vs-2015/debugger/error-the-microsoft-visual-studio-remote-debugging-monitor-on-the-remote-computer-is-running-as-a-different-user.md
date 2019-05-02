---
title: 'Erro: O Monitor de depuração remota do Microsoft Visual Studio no computador remoto está em execução como um usuário diferente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7cba3de8aa07a021d61e1ebb2a2c97f568eaf9ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388430"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Erro: O Monitor de Depuração Remota do Microsoft Visual Studio no computador remoto está sendo executado como um usuário diferente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao tentar fazer a depuração remota, você pode receber a seguinte mensagem de erro:  
  
 O Monitor de Depuração Remota do Microsoft Visual Studio no computador está sendo executado como um usuário diferente.  
  
## <a name="cause"></a>Causa  
 Essa mensagem ocorre quando você está depurando no modo Sem Autenticação e o usuário que iniciou o msvsmon não é o usuário que está executando o Visual Studio.  
  
## <a name="solution"></a>Solução  
 A solução melhor e mais segura é executar o Monitor de Depuração Remota (msvsmon.exe) na mesma conta de usuário que o Visual Studio. Se você não puder fazer isso, execute o Monitor de Depuração Remota em outra conta com a opção **Permitir que qualquer usuário depure** selecionada na caixa de diálogo **Opções** dele.  
  
> [!CAUTION]
> Conceder permissões a outros usuários para se conectar permite a possibilidade de acidentalmente conectar à sessão de depuração remota incorreta. A depuração no modo **Sem Autenticação** nunca é segura e deve ser usada com cuidado.  
  
 Para obter mais informações, consulte [iniciar o Monitor de depuração remota](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c).  
  
## <a name="see-also"></a>Consulte também  
 [Solução de problemas e erros de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)
