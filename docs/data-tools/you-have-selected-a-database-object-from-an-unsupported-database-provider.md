---
title: Objeto de provedor sem suporte
description: Você selecionou um objeto de banco de dados de um provedor de banco de dados sem suporte. Exibir informações sobre esta mensagem do Visual Studio (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c3ccd477882382962efcc2f87c5dc99f59c14be1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858040"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Você tiver selecionado um objeto de base de dados de um provedor de base de dados sem suporte

O o **/R Designer** dá suporte apenas ao .NET Framework Provedor de Dados para SQL Server ( <xref:System.Data.SqlClient> ). Embora você possa clicar em **OK** e continuar trabalhando com objetos de provedores de banco de dados sem suporte, você pode enfrentar um comportamento inesperado em tempo de execução.

> [!NOTE]
> Somente as conexões de dados que usam o provedor de dados. NET Framework para SQL Server são suportadas.

## <a name="options"></a>Opções

- Clique em **OK** para continuar a criar as classes de entidade que mapeiam para a conexão que usa o provedor de banco de dados sem suporte. Você pode apresentar comportamento inesperado quando você usa provedores de base de dados sem suporte.

- Clique em **Cancelar** para interromper a ação. Crie ou use uma conexão de dados diferente que use o provedor de .NET Framework para SQL Server.

## <a name="see-also"></a>Consulte também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
