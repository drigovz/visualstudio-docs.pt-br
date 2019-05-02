---
title: 'Erro: Execução de Transact-SQL terminou sem depuração | Microsoft Docs'
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
ms.openlocfilehash: 71d1f14bef8eb69fa6c6fc4d9c3f669826079c99
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850168"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Erro: A execução de Transact-SQL terminou sem depuração

Esse erro ocorre quando você está tentando depurar um Transact-SQL ou procedimento SQLCLR e o depurador não recebe mensagens de depuração do SQL Server.

Esse problema pode ser devido a problemas de rede ou problemas no SQL Server, mas a causa mais provável é um problema de permissões.

Há duas contas envolvidas:

- A conta de aplicativo é a conta de usuário como o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está sendo executado.

- A conta de conexão é a identidade usada para fazer a conexão com o SQL Server. Essa conta não é necessariamente o mesmo que a identidade do Visual Studio está em execução como se a conexão está usando a autenticação do SQL.

  Depuração de SQL exige que a conta do aplicativo deve corresponder à conta de conexão ou ser um sysadmin.

  Se você estiver usando um nome de conta do SQL como sa, a aplicativo conta deve ser configurada no SQL Server como um sysadmin. Por padrão, os administradores no computador do SQL server em execução no são sysadmins do SQL Server.

  Para corrigir esse erro, talvez seja necessário:

  - Verificar suas configurações de permissões. Para obter mais informações, confira [Como: Definir permissões do SQL Server para depuração](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

  - Verifique se a depuração do SQL está configurada corretamente.

  - Consulte o administrador de rede ou banco de dados.

## <a name="see-also"></a>Consulte também

- [Configuração de depuração de SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Como: Definir permissões do SQL Server para depuração](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)
- [Depuração remota](../debugger/remote-debugging.md)