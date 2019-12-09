---
title: A conexão selecionada usa um provedor de banco de dados sem suporte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e79d8408fba54cf192d51f9d2ead8c0ffafe1f0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667190"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>A conexão selecionada usa um provedor de base de dados sem suporte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa mensagem é exibida quando você arrasta itens que não usam o .NET Framework Provedor de Dados para SQL Server de **Gerenciador de Servidores** /**Gerenciador de banco de dados** nas [ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] suporta apenas as conexões de dados que usam o provedor. NET Framework para SQL Server. Somente as conexões a Microsoft SQL Server ou o Arquivo base de dados do Microsoft SQL Server são válidos.

### <a name="to-correct-this-error"></a>Para corrigir esse erro

- Adicionar itens somente as conexões de dados que usam o provedor de dados. NET Framework para SQL Server a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

## <a name="see-also"></a>Consulte também
 <xref:System.Data.SqlClient> [.NET Framework provedores de dados](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) [Walkthrough: Criando classes de LINQ to SQL (O-R Designer) ](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)