---
title: Criando e gerenciando bancos de dados e aplicativos da camada de dados
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2b1caf45235f9dd745841cb26a2fa10a148a7b5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299645"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Criar e gerenciar aplicativos da camada de dados e de bancos de dados no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[IMPORTANTE]
> Os projetos de banco de dados que foram incluídos em versões anteriores do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] agora são fornecidos em ferramentas de [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)]. Para obter mais informações, consulte [ferramentas de SQL Server Developer](https://go.microsoft.com/fwlink/?LinkId=228126).

 Você pode usar projetos de banco de dados para criar novos bancos de dado, novos aplicativos da camada de DACs (data-tier) e para atualizar bancos de dados existentes e aplicativos da camada de dado. Os projetos de banco de dados e o DAC permitem que você aplique as técnicas de controle de versão e gerenciamento de projeto aos seus esforços de desenvolvimento de banco de dados da mesma forma que aplica essas técnicas ao código gerenciado ou nativo. Você pode ajudar sua equipe de desenvolvimento a gerenciar alterações em bancos de dados e servidores de banco de dados criando um projeto de *DAC*, um *projeto de banco de dados*ou um projeto de *servidor* e colocando-o sob controle de versão. Os membros da sua equipe podem fazer check-out de arquivos para fazer, compilar e testar alterações em um *ambiente de desenvolvimento isolado*, ou na área restrita, antes de compartilhá-los com a equipe. Para ajudar a garantir a qualidade do código, sua equipe pode concluir e testar todas as alterações de uma versão específica do banco de dados em um ambiente de preparo antes de implantar as alterações na produção.

 Para obter uma lista dos recursos de banco de dados com suporte dos aplicativos da camada de dado, consulte [recursos com suporte em aplicativos da camada de dados](https://go.microsoft.com/fwlink/?LinkId=164239) no site da Microsoft. Se você usar recursos em seu banco de dados que não têm suporte de aplicativos da camada de dado, você deve usar um projeto de banco de dados para gerenciar alterações no banco de dados.

## <a name="common-high-level-tasks"></a>Tarefas comuns de alto nível

|Tarefa de alto nível|Conteúdo de suporte|
|----------------------|------------------------|
|**Iniciar o desenvolvimento de um aplicativo da camada de dados:** Um DAC é um novo conceito introduzido com [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] que contém a definição de um banco de dados [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e os objetos de instância de suporte que são usados por um aplicativo cliente-servidor ou de três camadas. Um DAC inclui objetos de banco de dados, como tabelas e exibições, juntamente com entidades de instância, como logons. Você pode usar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para criar um projeto de DAC, criar um arquivo de pacote de DAC e enviar esse arquivo de pacote de DAC para um administrador de banco de dados para implantação em uma instância do mecanismo de banco de dados [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|-   [criar e gerenciar aplicativos da camada de dados](https://go.microsoft.com/fwlink/?LinkId=160741) (site da Microsoft)<br />-   [SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=227328)|
|**Executando o desenvolvimento de banco de dados iterativo:** Se você for um desenvolvedor ou um testador, você faz check-out de partes do projeto e os atualiza em um ambiente de desenvolvimento isolado. Usando esse tipo de ambiente, você pode testar suas alterações sem afetar outros membros da equipe. Depois que as alterações forem concluídas, você verificará os arquivos de volta para o controle de versão, onde outros membros da equipe podem obter suas alterações e compilá-las e implantá-las em um servidor de teste.|-   [editores de consulta e texto (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (site da Microsoft)<br />[depurador do Transact-SQL](https://go.microsoft.com/fwlink/?LinkId=227324) -   (site da Microsoft)|
|**Criando protótipos, verificando resultados de teste e modificando scripts e objetos de banco de dados:** Você pode usar o editor de [!INCLUDE[tsql](../includes/tsql-md.md)] para executar qualquer uma dessas tarefas comuns.|-   [editores de consulta e texto (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (site da Microsoft)|

## <a name="see-also"></a>Consulte também
 [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
