---
title: 'Erro: a execução do Transact-SQL foi encerrada sem depuração | Microsoft Docs'
ms.date: 11/08/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94ced2902becc2e988cde5198eff28911864dcbb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736943"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Erro: execução de Transact-SQL encerrada sem depuração

Esse erro ocorre quando você está tentando depurar um procedimento Transact-SQL ou SQLCLR e o depurador não recebe mensagens de depuração do SQL Server.

Esse problema pode ser devido a problemas de rede ou problemas na SQL Server, mas a causa mais provável é um problema de permissões.

Há duas contas envolvidas:

- A conta de aplicativo é a conta de usuário como o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está sendo executado.

- A conta de conexão é a identidade usada para fazer a conexão com o SQL Server. Essa conta não é necessariamente a mesma que a identidade em que o Visual Studio está sendo executado como se a conexão estiver usando a autenticação do SQL.

  A depuração SQL requer que a conta de aplicativo corresponda à conta de conexão ou que seja um sysadmin.

  Se você estiver usando um nome de conta SQL como SA, a conta de aplicativo deverá ser configurada no SQL Server como um sysadmin. Por padrão, os administradores no computador em que o SQL Server está sendo executado são SQL Server sysadmins.

  Para corrigir esse erro, talvez seja necessário:

  - Verificar suas configurações de permissões. Para obter mais informações, consulte [How to: Set SQL Server Permissions for Debugging](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

  - Verifique se a depuração do SQL está configurada corretamente.

  - Consulte o administrador de rede ou banco de dados.

## <a name="see-also"></a>Consulte também

- [Configurando a depuração SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Como definir permissões de SQL Server para depuração](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)
- [Depuração remota](../debugger/remote-debugging.md)