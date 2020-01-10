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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5dad282bfc1c539216b55e41d77d7743808311d6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587362"
---
# <a name="maintainability-warnings"></a>Avisos de facilidade de manutenção

Os avisos de manutenção dão suporte à biblioteca e manutenção de aplicativos.

## <a name="in-this-section"></a>Nesta seção

| Regra | Descrição |
|-----------|-----------------------------------|
| [CA1500: os nomes de variável não devem corresponder aos nomes de campo](../code-quality/ca1500.md) | Um método de instância declara um parâmetro ou uma variável local cujo nome corresponde a um campo de instância do tipo declarativo, o que leva a erros. |
| [CA1501: evitar herança excessiva](../code-quality/ca1501.md) | Um tipo está mais de quatro níveis abaixo na hierarquia de herança. As hierarquias de tipo profundamente aninhado podem ser difíceis de seguir, compreender e manter. |
| [CA1502: evitar complexidade excessiva](../code-quality/ca1502.md) | Esta regra mede o número de caminhos linearmente independentes por meio do método, o que é determinado pelo número e pela complexidade das ramificações condicionais. |
| [CA1504: examinar nomes de campo confusos](../code-quality/ca1504.md) | O nome de um campo de instância começa com "s_" ou o nome de um campo estático (compartilhado no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) começa com "m_". |
| [CA1505: evitar código que não possa ser mantido](../code-quality/ca1505.md) | Um tipo ou um método tem um baixo valor de índice de facilidade de manutenção. Um baixo índice de facilidade de manutenção indica que um tipo ou um método é provavelmente difícil de manter e seria um bom candidato para um novo design. |
| [CA1506: evitar acoplamento de classes excessivo](../code-quality/ca1506.md) | Esta regra mede o acoplamento de classes contando o número de referências de tipo exclusivas que um tipo ou um método contém. |
| [CA1507: usar nameof no lugar da cadeia de caracteres](../code-quality/ca1507.md) | Um literal de cadeia de caracteres é usado como um argumento em que uma expressão de `nameof` pode ser usada. |

## <a name="see-also"></a>Veja também

- [Meça a complexidade e a facilidade de manutenção do código gerenciado](../code-quality/code-metrics-values.md)
