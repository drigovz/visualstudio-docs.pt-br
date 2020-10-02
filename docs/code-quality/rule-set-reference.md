---
title: Referência do conjunto de regras da análise de código
ms.date: 04/04/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b20974d2e44661ed7f4a0288ecb9eff82b2035a
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658419"
---
# <a name="code-analysis-rule-set-reference"></a>Referência do conjunto de regras da análise de código

Quando você configura a análise herdada para projetos de código gerenciado no Visual Studio, pode escolher em uma lista de *conjuntos de regras*internos. Algumas regras são incluídas em mais de um dos conjuntos de regras internos, por exemplo, o conjunto de regras básicas de regras de correção inclui regras que estão no conjunto de regras de regra recomendadas gerenciadas.

> [!NOTE]
> Os conjuntos de regras nesta seção pertencem à análise herdada. Para obter informações sobre conjuntos de regras disponíveis para pacotes do Code Analyzer, consulte [usar conjuntos de regras com analisadores de código](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

Você pode usar um desses conjuntos de regras internos ou pode [Personalizar um conjunto de regras](../code-quality/how-to-create-a-custom-rule-set.md) para se adequar aos requisitos do projeto. Se você incluir vários conjuntos de regras que contêm a mesma regra em um conjunto de regras personalizadas, essa regra aparecerá apenas uma vez no conjunto de regras personalizadas.

Os tópicos nesta seção descrevem os conjuntos de regras internos e as regras (ou avisos) que eles contêm.

| Conjunto de regras | Regras incluídas |
| - | - |
| [Todas as regras](all-rules-rule-set.md) | Contém todas as regras de C++ e gerenciadas disponíveis |
| [Regras básicas de correção](basic-correctness-rules-rule-set-for-managed-code.md) | Inclui regras gerenciadas recomendadas, além de regras para erros lógicos e uso de estrutura |
| [Regras estendidas de correção](extended-correctness-rules-rule-set-for-managed-code.md) | Inclui regras básicas de correção (que inclui regras recomendadas gerenciadas) mais regras para erros de lógica e uso de estrutura |
| [Regras básicas de diretriz de design](basic-design-guideline-rules-rule-set-for-managed-code.md) | Inclui regras gerenciadas recomendadas, além de regras para garantir que o código seja fácil de ler, compreender e manter |
| [Regras estendidas de diretrizes de design](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Inclui regras básicas de diretrizes de design (que incluem regras recomendadas gerenciadas) e mais regras de manutenção que se concentram na nomenclatura |
| [Regras de globalização](globalization-rules-rule-set-for-managed-code.md) | Inclui regras para problemas de globalização |
| [Regras mínimas gerenciadas](managed-minimum-rules-rule-set-for-managed-code.md) | Inclui quatro regras para problemas críticos de código gerenciado |
| [Regras gerenciadas recomendadas](managed-recommended-rules-rule-set-for-managed-code.md) | Inclui regras mínimas gerenciadas e mais regras para problemas críticos de código gerenciado |
| [Regras mistas mínimas](mixed-minimum-rules-rule-set.md) | Inclui regras para problemas críticos no código C++ para CLR |
| [Regras mistas recomendadas](mixed-recommended-rules-rule-set.md) | Inclui regras mínimas mistas e mais regras para problemas críticos no código C++ para CLR |
| [Regras nativas mínimas](native-minimum-rules-rule-set.md) | Inclui regras para problemas críticos em código nativo |
| [Regras nativas recomendadas](native-recommended-rules-rule-set.md) | Inclui regras mínimas nativas e mais regras para problemas críticos no código nativo |
| [Regras de segurança](security-rules-rule-set-for-managed-code.md) | Inclui regras para localizar vulnerabilidades de segurança |
