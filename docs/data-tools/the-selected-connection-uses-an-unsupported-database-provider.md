---
title: Provedor de banco de dados sem suporte
description: A conexão selecionada usa um provedor de base de dados sem suporte
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c8fa073b47927f673914156c586bf27a121e53ea
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037563"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>A conexão selecionada usa um provedor de base de dados sem suporte

Essa mensagem é exibida quando você arrasta itens que não usam o .NET Framework Provedor de Dados para SQL Server de **Gerenciador de servidores** ou **Gerenciador de banco de dados** nas [ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

O o **/R Designer** dá suporte apenas a conexões de dados que usam o provedor de .NET Framework para SQL Server. Somente as conexões a Microsoft SQL Server ou o Arquivo base de dados do Microsoft SQL Server são válidos.

Para corrigir esse erro, adicione somente itens de conexões de dados que usam o .NET Framework Provedor de Dados para SQL Server ao o **/R Designer**.

## <a name="see-also"></a>Confira também

- <xref:System.Data.SqlClient>
- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
