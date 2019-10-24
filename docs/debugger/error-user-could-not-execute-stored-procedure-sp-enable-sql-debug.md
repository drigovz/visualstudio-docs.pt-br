---
title: 'Erro: o usuário não pôde executar o procedimento armazenado Sp_enable_sql_debug | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3bdc6ecb03572d824f6e3b887090d67be416cdef
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736545"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Erro: o usuário não conseguiu executar o procedimento armazenado sp_enable_sql_debug

A depuração do Procedimento Armazenado sp_enable_sql_debug não pode ser executada no servidor. Isso pode ser causado por:

- Um problema de conexão. Você precisa ter uma conexão estável com o servidor.

- Falta das permissões necessárias no servidor. Para depurar no SQL Server 2005, a conta que executa o Visual Studio e a conta usada para conectar-se ao SQL Server devem ser membros da função sysadmin. A conta usada para se conectar ao SQL Server é sua conta de usuário do Windows (se você estiver usando a autenticação do Windows) ou uma conta com ID de usuário e senha (se você usar a autenticação do SQL).

Para obter mais informações, consulte [How to: Set SQL Server Permissions for Debugging](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Consulte também

- [Como definir permissões de SQL Server para depuração](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Configurando a depuração SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))