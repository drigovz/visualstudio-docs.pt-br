---
title: Aprimorando a qualidade do código com as políticas de check-in do projeto de equipe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 13f943baef21560132f2f9b9ba98c0325540fbf2
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301086"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Melhorando a qualidade do código com políticas de check-in do projeto da equipe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao usar o Controle de Versão do Team Foundation (TFVC), você pode criar políticas de check-in para seus projetos de equipe. para impor práticas que levam a um melhor código e um desenvolvimento de grupo mais eficiente. As políticas de check-in são regras que são definidas no nível do projeto de equipe e impostas em computadores de desenvolvedor antes do código ter permissão para fazer check-in.

 Você pode especificar estas políticas de check-in do projeto de equipe:

- **Compilações**: requer que as quebras de compilação criadas durante uma compilação devam ser corrigidas antes de um novo check-in.

- **Comentários do conjunto de alterações**: requer que os usuários forneçam comentários ao fazer check-in de alterações.

- **Análise de código**: requer que a análise de código seja executada antes do check-in.

- **Itens de trabalho**: requer que um ou mais itens de trabalho sejam associados ao check-in.

> [!IMPORTANT]
> Para usar as políticas de check-in, você deve estar conectado a [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)].

## <a name="common-tasks"></a>Tarefas comuns

|Tarefa|Conteúdo de suporte|
|----------|------------------------|
|**Criar e usar políticas de check-in:** Você cria políticas de check-in usando as configurações do projeto de equipe de [!INCLUDE[esprscc](../includes/esprscc-md.md)].|[Definir e impor Gates de qualidade](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**Criar e usar políticas de check-in de análise de código:** Você pode escolher entre um conjunto padrão de regras de análise de código ou pode criar um conjunto personalizado.|[Criando e usando políticas de check-in de análise de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>Tarefas relacionadas

|Tarefa|Conteúdo de suporte|
|----------|------------------------|
|**Configure seu ambiente de desenvolvimento:** Antes de criar ou modificar o código, você deve configurar seus ambientes de desenvolvimento e teste usando o código-fonte apropriado. Se você estiver trabalhando com bancos de dados, também deverá ter acesso à sua representação offline.|[Configurando ambientes de desenvolvimento](https://msdn.microsoft.com/7b686610-d379-4ca0-9608-73ef0e576e3a)|
|**Use a análise de código no processo de desenvolvimento:** Os membros da equipe executam a análise de código em seus computadores de desenvolvimento. No Visual Studio, os desenvolvedores configuram e executam execuções de análise de código para projetos de código individuais, exibem e analisam os problemas encontrados pelas execuções e criam itens de trabalho para avisos.|[Analisando a qualidade do aplicativo](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**Criar e executar testes de unidade:** Os testes de unidade oferecem aos desenvolvedores e testadores uma maneira rápida de procurar erros lógicos nos métodos de C#classes no, Visual Basic .NET C++ e projetos. Um teste de unidade pode ser criado uma vez e executado toda vez que o código-fonte é alterado para garantir que nenhum bug seja introduzido.|[Efetuar teste de unidade em seu código](../test/unit-test-your-code.md)|
|**Acompanhe itens de trabalho e defeitos:** Você pode usar itens de trabalho para acompanhar e gerenciar seu trabalho e suas informações sobre seu projeto de equipe. Um item de trabalho é um registro de banco de dados que [!INCLUDE[esprfound](../includes/esprfound-md.md)] usa para acompanhar a atribuição e o andamento do trabalho. Você pode usar diferentes tipos de itens de trabalho para acompanhar diferentes tipos de trabalho, como requisitos do cliente, bugs do produto e tarefas de desenvolvimento.|[Acompanhe o trabalho e gerencie o workflow &#91;Redirecionado&#93;](https://msdn.microsoft.com/d2d8637d-0ef8-4ca3-874e-a04713344032)|

## <a name="external-resources"></a>Recursos externos

### <a name="guidance"></a>Diretrizes
 [Testes de Entrega Contínua com o Visual Studio 2012 – Capítulo 2: Teste de Unidade: Testando o Interior](https://go.microsoft.com/fwlink/?LinkID=255188)
