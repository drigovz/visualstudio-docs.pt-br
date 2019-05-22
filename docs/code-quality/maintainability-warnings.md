---
title: Avisos de facilidade de manutenção
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752a637ef01c33aa4e93083e9578d01f00977960
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65976162"
---
# <a name="maintainability-warnings"></a>Avisos de facilidade de manutenção

Avisos de facilidade de manutenção suporte à manutenção de biblioteca e o aplicativo.

## <a name="in-this-section"></a>Nesta seção

| Regra | Descrição |
|-----------|-----------------------------------|
| [CA1500: Nomes de variáveis não devem corresponder aos nomes de campo](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | Um método de instância declara um parâmetro ou uma variável local cujo nome corresponde a um campo de instância do tipo declarativo, que leva a erros. |
| [CA1501: Evitar herança excessiva](../code-quality/ca1501-avoid-excessive-inheritance.md) | Um tipo está mais de quatro níveis abaixo na hierarquia de herança. As hierarquias de tipo profundamente aninhado podem ser difíceis de seguir, compreender e manter. |
| [CA1502: Evitar complexidade excessiva](../code-quality/ca1502-avoid-excessive-complexity.md) | Esta regra mede o número de caminhos linearmente independentes por meio do método, o que é determinado pelo número e pela complexidade das ramificações condicionais. |
| [CA1504: Examine os nomes de campo](../code-quality/ca1504-review-misleading-field-names.md) | O nome de um campo de instância começa com "s _", ou o nome de um estático (compartilhado no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) campo começa com "m _". |
| [CA1505: Evitar código que](../code-quality/ca1505-avoid-unmaintainable-code.md) | Um tipo ou um método tem um baixo valor de índice de facilidade de manutenção. Um baixo índice de facilidade de manutenção indica que um tipo ou um método é provavelmente difícil de manter e seria um bom candidato para um novo design. |
| [CA1506: Evite acoplamento de classes excessivo](../code-quality/ca1506-avoid-excessive-class-coupling.md) | Esta regra mede o acoplamento de classes contando o número de referências de tipo exclusivas que um tipo ou um método contém. |
| [CA1507: Usar nameof no lugar da cadeia de caracteres](../code-quality/ca1507.md) | Um literal de cadeia de caracteres é usada como um argumento em que um `nameof` expressão pode ser usada. |

## <a name="see-also"></a>Consulte também

- [Medir a complexidade e facilidade de manutenção do código gerenciado](../code-quality/code-metrics-values.md)