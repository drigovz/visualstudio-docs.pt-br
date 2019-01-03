---
title: 'Erro: Usuário não conseguiu executar procedimento armazenado sp_enable_sql_debug | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b121b863237a3b12b5131be348581ea3fd043d2
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348563"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Erro: O usuário não conseguiu executar o procedimento armazenado sp_enable_sql_debug

A depuração do Procedimento Armazenado sp_enable_sql_debug não pode ser executada no servidor. Isso pode ser causado por:

- Um problema de conexão. Você precisa ter uma conexão estável com o servidor.

- Falta das permissões necessárias no servidor. Para depurar no SQL Server 2005, a conta que executa o Visual Studio e a conta usada para conectar-se ao SQL Server devem ser membros da função sysadmin. A conta usada para se conectar ao SQL Server é sua conta de usuário do Windows (se você estiver usando a autenticação do Windows) ou uma conta com ID de usuário e senha (se você usar a autenticação do SQL).

Para obter mais informações, confira [Como: Definir permissões do SQL Server para depuração](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Consulte também

- [Como: Definir permissões do SQL Server para depuração](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Configuração de depuração de SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))