---
title: A conexão selecionada usa um provedor de base de dados sem suporte
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5fab6be50a9b4c273a7bb911d8afde5cf65d7676
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460577"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>A conexão selecionada usa um provedor de base de dados sem suporte

Esta mensagem aparece quando você arrasta itens que não usam o .NET Framework Data Provider para SQL Server a partir **Gerenciador de servidores** ou **Database Explorer** até o [LINQ to SQL das ferramentas no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

O **Relational Designer** dá suporte a apenas as conexões de dados que usam o provedor .NET Framework para SQL Server. Somente as conexões a Microsoft SQL Server ou o Arquivo base de dados do Microsoft SQL Server são válidos.

Para corrigir esse erro, adicionar itens somente as conexões de dados que usam o .NET Framework Data Provider para SQL Server para o **Relational Designer**.

## <a name="see-also"></a>Consulte também

- <xref:System.Data.SqlClient>
- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
