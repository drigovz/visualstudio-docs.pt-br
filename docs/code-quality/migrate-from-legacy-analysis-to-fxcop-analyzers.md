---
title: Migrar da análise herdada (FxCop) para a análise de origem (analisadores do FxCop)
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
ms.openlocfilehash: 9157d47278f835232308dc497965afebb294f8fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78937577"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>Migrar da análise herdada (FxCop) para a análise de origem (analisadores do FxCop)

Análise de origem por .NET Compiler Platform ("Roslyn") analisadores substitui a [análise herdada](../code-quality/code-analysis-for-managed-code-overview.md) para código gerenciado. Para modelos de projeto mais recentes, como projetos .NET Core e .NET Standard, a análise herdada não está disponível.

Muitas das regras de análise herdada (FxCop) já foram reescritas para analisadores do FxCop, um conjunto de analisadores de código Roslyn. Você [instala os analisadores do FxCop como um pacote NuGet](install-fxcop-analyzers.md#nuget-package) referenciado pelo projeto ou pela solução. Os analisadores do FxCop executam a análise baseada em código-fonte durante a execução do compilador. Os resultados do analisador são relatados junto com os resultados do compilador.

Para obter mais informações sobre as diferenças entre análise herdada e análise de origem, consulte o seguinte:

- [Análise de código-fonte versus análise herdada](../code-quality/roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis)

- [Perguntas frequentes sobre analisadores do FxCop](../code-quality/fxcop-analyzers-faq.md)

Para migrar para a análise de origem, [Instale os analisadores do FxCop](../code-quality/install-fxcop-analyzers.md). Como violações de regras de análise herdadas, as violações de análise de código-fonte aparecem na janela Lista de Erros no Visual Studio. Além disso, as violações de análise de código-fonte também aparecem no editor de códigos como *ondulado* no código incorreto. A cor da linha ondulada depende da [configuração de gravidade](../code-quality/use-roslyn-analyzers.md#rule-severity) da regra. Para ver o status das regras portadas para os novos analisadores do FxCop, consulte [regras portadas e não portadas](../code-quality/fxcop-rule-port-status.md).

Para saber mais sobre como configurar os analisadores do FxCop:

- Para configurar os analisadores do FxCop, consulte [Configurar analisadores de FxCop](../code-quality/configure-fxcop-analyzers.md).

- Para descobrir sobre a configuração de analisadores usando regras predefinidas com EditorConfig ou um arquivo de conjunto de regras, consulte [habilitar uma categoria de regras](../code-quality/analyzer-rule-sets.md).