---
title: Usando conjuntos de regras para agrupar regras de análise de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30bd2e53531d9abc7d27adba05c3b724c88d61c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603478"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Usando conjuntos de regras para agrupar regras de análise de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao configurar a análise de código em [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] ou [!INCLUDE[vsPro](../includes/vspro-md.md)], você pode escolher em uma lista de *conjuntos de regras*internas da Microsoft. Um conjunto de regras é um agrupamento lógico de regras de análise de código que identificam problemas direcionados e condições específicas. Por exemplo, você pode aplicar um conjunto de regras que foi projetado para verificar o código de APIs disponíveis publicamente ou pode aplicar um conjunto de regras que inclui apenas as regras mínimas recomendadas. Você também pode aplicar um conjunto de regras que inclui todas as regras.

 Você pode personalizar um conjunto de regras adicionando ou excluindo regras ou alterando as regras para que apareçam na janela de **lista de erros** como avisos ou erros. Conjuntos de regras personalizados podem atender a uma necessidade de seu ambiente de desenvolvimento específico. Quando você personaliza um conjunto de regras, a página conjunto de regras fornece ferramentas de pesquisa e filtragem para ajudá-lo no processo.

## <a name="common-tasks"></a>Tarefas comuns

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Introdução prática:** Use as ferramentas de análise de código para especificar um conjunto personalizado de regras para localizar e corrigir problemas em um aplicativo simples de .NET Framework.|[instruções passo a -   : Configurando e usando um conjunto de regras personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Configurar análise de código para um projeto:** Escolha um conjunto de regras existente para um projeto, site ou solução.|-   [como: configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [usando conjuntos de regras para especificar C++ as regras a serem executadas](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [como: configurar a análise de código para um aplicativo Web ASP.net](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [como especificar conjuntos de regras para vários projetos em uma solução](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Personalizar um conjunto de regras:** Especifique as regras a serem aplicadas ao seu projeto.|-   [criar conjuntos de regras personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**Entenda os conjuntos de regras internos:** Exiba as regras de análise de código que compõem os conjuntos de regras internos.|[referência do conjunto de regras de análise de código](../code-quality/code-analysis-rule-set-reference.md) -   |
|**Integre a análise de código com Team Foundation Server:** as políticas de check-in do [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] permitem que as equipes de desenvolvimento se confiram se todos os check-ins de código atendem a um conjunto comum de padrões de análise de código|-   [como: sincronizar conjuntos de regras de projeto de código com a política de check-in do projeto de equipe](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|
