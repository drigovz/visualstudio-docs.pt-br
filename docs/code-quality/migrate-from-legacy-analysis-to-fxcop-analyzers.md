---
title: Migrar do FxCop para a análise de origem (analisadores de FxCop)
ms.custom: SEO-VS-2020
description: Saiba como analisar o código pela primeira vez ou como migrar do FxCop (análise binária) para a nova maneira de analisar o código gerenciado usando a análise de origem (analisadores do FxCop).
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb75b7374e7f88f4643a5ecc4a9c193d8144efc4
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91860477"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>Migrar da análise herdada (FxCop) para a análise de origem (analisadores do FxCop)

Análise de origem por .NET Compiler Platform ("Roslyn") analisadores substitui a [análise herdada](../code-quality/code-analysis-for-managed-code-overview.md) para código gerenciado. Para modelos de projeto mais recentes, como projetos .NET Core e .NET Standard, a análise herdada não está disponível.

Muitas das regras de análise herdada (FxCop) já foram reescritas para analisadores do FxCop, um conjunto de analisadores de código Roslyn. Você [instala os analisadores do FxCop como um pacote NuGet](install-fxcop-analyzers.md#nuget-package) referenciado pelo projeto ou pela solução. Os analisadores do FxCop executam a análise baseada em código-fonte durante a execução do compilador. Os resultados do analisador são relatados junto com os resultados do compilador.

Para obter mais informações sobre as diferenças entre análise herdada e análise de origem, consulte o seguinte:

- [Análise de código-fonte versus análise herdada](../code-quality/fxcop-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers)

- [Perguntas frequentes sobre analisadores do FxCop](../code-quality/fxcop-analyzers-faq.md)

Para migrar para a análise de origem, [Instale os analisadores do FxCop](../code-quality/install-fxcop-analyzers.md). Como violações de regras de análise herdadas, as violações de análise de código-fonte aparecem na janela Lista de Erros no Visual Studio. Além disso, as violações de análise de código-fonte também aparecem no editor de códigos como *ondulado* no código incorreto. A cor da linha ondulada depende da [configuração de gravidade](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) da regra. Para ver o status das regras portadas para os novos analisadores do FxCop, consulte [regras portadas e não portadas](../code-quality/fxcop-rule-port-status.md).

Para saber mais sobre como configurar os analisadores do FxCop:

- Para configurar os analisadores do FxCop, consulte [Configurar analisadores de FxCop](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- Para descobrir sobre a configuração de analisadores usando regras predefinidas com EditorConfig ou um arquivo de conjunto de regras, consulte [habilitar uma categoria de regras](/dotnet/fundamentals/code-analysis/code-quality-rule-options).
