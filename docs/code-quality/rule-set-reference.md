---
title: Referência do conjunto de regras da análise de código
ms.date: 04/04/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0222dab568ce421c3bd87474b956c82aab4d2683
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585247"
---
# <a name="code-analysis-rule-set-reference"></a>Referência do conjunto de regras da análise de código

Quando você configura a análise herdada para projetos de código gerenciado no Visual Studio, pode escolher em uma lista de *conjuntos de regras*internos. Algumas regras são incluídas em mais de um dos conjuntos de regras internos, por exemplo, o conjunto de regras básicas de regras de correção inclui regras que estão no conjunto de regras de regra recomendadas gerenciadas.

> [!NOTE]
> Os conjuntos de regras nesta seção pertencem à análise herdada. Para obter informações sobre conjuntos de regras disponíveis para pacotes do Code Analyzer, consulte [usar conjuntos de regras com analisadores de código](analyzer-rule-sets.md).

Você pode usar um desses conjuntos de regra interna, ou você pode [personalizar um conjunto de regras](../code-quality/how-to-create-a-custom-rule-set.md) para atender às suas necessidades de projeto. Se você incluir vários conjuntos de regras que contêm a mesma regra em um conjunto de regras personalizadas, essa regra aparecerá apenas uma vez no conjunto de regras personalizadas.

Os tópicos nesta seção descrevem a regra interna conjuntos e as regras (ou avisos) que eles contêm.

| Conjunto de regras | Regras incluídas |
| - | - |
| [Todas as regras](all-rules-rule-set.md) | Contém todas as regras e C++ gerenciadas disponíveis |
| [Regras básicas de correção](basic-correctness-rules-rule-set-for-managed-code.md) | Inclui regras gerenciadas recomendadas, além de regras para erros lógicos e uso de estrutura |
| [Regras de correção estendida](extended-correctness-rules-rule-set-for-managed-code.md) | Inclui regras básicas de correção (que inclui regras recomendadas gerenciadas) mais regras para erros de lógica e uso de estrutura |
| [Regras básicas de diretriz de design](basic-design-guideline-rules-rule-set-for-managed-code.md) | Inclui regras gerenciadas recomendadas, além de regras para garantir que o código seja fácil de ler, compreender e manter |
| [Regras de diretrizes de design estendidas](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Inclui regras básicas de diretrizes de design (que incluem regras recomendadas gerenciadas) e mais regras de manutenção que se concentram na nomenclatura |
| [Regras de globalização](globalization-rules-rule-set-for-managed-code.md) | Inclui regras para problemas de globalização |
| [Regras mínimas gerenciadas](managed-minimum-rules-rule-set-for-managed-code.md) | Inclui quatro regras para problemas críticos de código gerenciado |
| [Regras recomendadas gerenciadas](managed-recommended-rules-rule-set-for-managed-code.md) | Inclui regras mínimas gerenciadas e mais regras para problemas críticos de código gerenciado |
| [Regras mínimas mistas](mixed-minimum-rules-rule-set.md) | Inclui regras para problemas críticos no C++ código para CLR |
| [Regras recomendadas mistas](mixed-recommended-rules-rule-set.md) | Inclui regras mínimas mistas mais regras para problemas críticos C++ no código para CLR |
| [Regras mínimas nativas](native-minimum-rules-rule-set.md) | Inclui regras para problemas críticos em código nativo |
| [Regras nativas recomendadas](native-recommended-rules-rule-set.md) | Inclui regras mínimas nativas e mais regras para problemas críticos no código nativo |
| [Regras de segurança](security-rules-rule-set-for-managed-code.md) | Inclui regras para localizar vulnerabilidades de segurança |