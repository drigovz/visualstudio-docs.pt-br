---
title: Objeto de provedor sem suporte
description: Você tiver selecionado um objeto de base de dados de um provedor de base de dados sem suporte
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a4867ab2e7d8f269961c7d1a783a3b31d70da05d
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743166"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Você tiver selecionado um objeto de base de dados de um provedor de base de dados sem suporte

O o **/R Designer** dá suporte apenas ao .NET Framework Provedor de Dados para SQL Server ( <xref:System.Data.SqlClient> ). Embora você possa clicar em **OK** e continuar trabalhando com objetos de provedores de banco de dados sem suporte, você pode enfrentar um comportamento inesperado em tempo de execução.

> [!NOTE]
> Somente as conexões de dados que usam o provedor de dados. NET Framework para SQL Server são suportadas.

## <a name="options"></a>Opções

- Clique em **OK** para continuar a criar as classes de entidade que mapeiam para a conexão que usa o provedor de banco de dados sem suporte. Você pode apresentar comportamento inesperado quando você usa provedores de base de dados sem suporte.

- Clique em **Cancelar** para interromper a ação. Crie ou use uma conexão de dados diferente que use o provedor de .NET Framework para SQL Server.

## <a name="see-also"></a>Veja também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
