---
title: Você tiver selecionado um objeto de base de dados de um provedor de base de dados sem suporte
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: dae92f404bb9ecb23b77dbda33c329994b9ed15b
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457874"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Você tiver selecionado um objeto de base de dados de um provedor de base de dados sem suporte

O **Relational Designer** dá suporte a apenas o .NET Framework Data Provider para SQL Server (<xref:System.Data.SqlClient>). Embora você possa clicar em **OK** e continuar trabalhando com objetos de provedores de banco de dados sem suporte, você pode enfrentar um comportamento inesperado em tempo de execução.

> [!NOTE]
> Somente as conexões de dados que usam o provedor de dados. NET Framework para SQL Server são suportadas.

## <a name="options"></a>Opções

- Clique em **OK** para continuar a criar as classes de entidade que mapeiam para a conexão que usa o provedor de banco de dados sem suporte. Você pode apresentar comportamento inesperado quando você usa provedores de base de dados sem suporte.

- Clique em **Cancelar** para parar a ação. Crie ou use uma conexão de dados diferente que usa o provedor .NET Framework para SQL Server.

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)