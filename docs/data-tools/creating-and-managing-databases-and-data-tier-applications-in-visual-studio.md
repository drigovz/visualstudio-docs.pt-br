---
title: Projetos de banco de dados e projetos de DAC
description: Leia sobre projetos de banco de dados e DACs (aplicativos da camada de dados). Use projetos de BD para criar novos bancos de dados, criar um novo DACs e atualizar bancos e DACs existentes.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 8ed1dc21d0029dc8939c540d33d0743c81db93fc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867081"
---
# <a name="database-projects-and-data-tier-applications"></a>Projetos e aplicativos da camada de dados

Você pode usar projetos de banco de dados para criar novos bancos de dado, novos aplicativos da camada de DACs (data-tier) e para atualizar bancos de dados existentes e aplicativos da camada de dado. Os projetos de banco de dados e o DAC permitem que você aplique as técnicas de controle de versão e gerenciamento de projeto aos seus esforços de desenvolvimento de banco de dados da mesma forma que aplica essas técnicas ao código gerenciado ou nativo. Você pode ajudar sua equipe de desenvolvimento a gerenciar alterações em bancos de dados e servidores de banco de dados criando um projeto de DAC, um projeto de banco de dados ou um projeto de servidor e colocando-o sob controle de versão. Os membros da sua equipe podem fazer check-out de arquivos para fazer, compilar e testar alterações em um ambiente de desenvolvimento isolado, ou na área restrita, antes de compartilhá-los com a equipe. Para ajudar a garantir a qualidade do código, sua equipe pode concluir e testar todas as alterações de uma versão específica do banco de dados em um ambiente de preparo antes de implantar as alterações na produção.

Para obter uma lista dos recursos de banco de dados com suporte dos aplicativos da camada de dado, consulte [suporte do DAC para objetos de SQL Server](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Se você usar recursos em seu banco de dados que não têm suporte de aplicativos da camada de dado, você deve usar um projeto de banco de dados para gerenciar alterações no banco de dados.

## <a name="common-high-level-tasks"></a>Tarefas comuns de alto nível

| High-Level tarefa | Conteúdo de suporte |
| - | - |
| **Iniciar o desenvolvimento de um aplicativo da camada de dados:** O conceito de um aplicativo da camada de dados (DAC) foi introduzido com SQL Server 2008. Um DAC contém a definição para um banco de dados SQL Server e os objetos de instância de suporte que são usados por um aplicativo cliente-servidor ou de três camadas. Um DAC inclui objetos de banco de dados, como tabelas e exibições, juntamente com entidades de instância, como logons. Você pode usar o Visual Studio para criar um projeto de DAC, criar um arquivo de pacote de DAC e enviar o arquivo de pacote de DAC para um administrador de banco de dados para implantação em uma instância do mecanismo de banco de dados SQL Server. | - [Aplicativos da camada de dados](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Executando o desenvolvimento de banco de dados iterativo:** Os desenvolvedores podem fazer check-out de partes do projeto e atualizá-las em um ambiente de desenvolvimento isolado. Usando esse tipo de ambiente, você pode testar suas alterações sem afetar outros membros da equipe. Depois que as alterações forem concluídas, você verificará os arquivos de volta para o controle de versão, onde outros membros da equipe podem obter suas alterações e compilá-las e implantá-las em um servidor de teste. | - [Desenvolvimento de banco de dados offline orientado a projetos (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Depurador Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Criando protótipos, verificando resultados de teste e modificando scripts e objetos de banco de dados:** Você pode usar o Editor Transact-SQL para executar qualquer uma dessas tarefas comuns. | - [Editores de consulta e texto (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Consulte também

- [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
