---
title: Você tiver selecionado um objeto de base de dados de um provedor de base de dados sem suporte
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b1dd14c428b90b87e665aa41681b5a9e68eb00e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648016"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Você tiver selecionado um objeto de base de dados de um provedor de base de dados sem suporte

O o **/R Designer** dá suporte apenas ao .NET Framework Provedor de Dados para SQL Server (<xref:System.Data.SqlClient>). Embora você possa clicar em **OK** e continuar trabalhando com objetos de provedores de banco de dados sem suporte, você pode enfrentar um comportamento inesperado em tempo de execução.

> [!NOTE]
> Somente as conexões de dados que usam o provedor de dados. NET Framework para SQL Server são suportadas.

## <a name="options"></a>Opções

- Clique em **OK** para continuar a criar as classes de entidade que mapeiam para a conexão que usa o provedor de banco de dados sem suporte. Você pode apresentar comportamento inesperado quando você usa provedores de base de dados sem suporte.

- Clique em **Cancelar** para interromper a ação. Crie ou use uma conexão de dados diferente que use o provedor de .NET Framework para SQL Server.

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)