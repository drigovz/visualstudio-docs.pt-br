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
ms.openlocfilehash: fcb1165ea00d407f5b4840358cc270eb299ba198
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586219"
---
# <a name="maintainability-warnings"></a>Avisos de facilidade de manutenção

Os avisos de manutenção dão suporte à biblioteca e manutenção de aplicativos.

## <a name="in-this-section"></a>Nesta seção

| Regra | Descrição |
|-----------|-----------------------------------|
| [CA1500: Nomes de variável não devem corresponder a nomes de campo](../code-quality/ca1500.md) | Um método de instância declara um parâmetro ou uma variável local cujo nome corresponde a um campo de instância do tipo declarativo, o que leva a erros. |
| [CA1501: Evitar herança excessiva](../code-quality/ca1501.md) | Um tipo está mais de quatro níveis abaixo na hierarquia de herança. As hierarquias de tipo profundamente aninhado podem ser difíceis de seguir, compreender e manter. |
| [CA1502: Evitar complexidade excessiva](../code-quality/ca1502.md) | Esta regra mede o número de caminhos linearmente independentes por meio do método, o que é determinado pelo número e pela complexidade das ramificações condicionais. |
| [CA1504: Examinar nomes de campo confusos](../code-quality/ca1504.md) | O nome de um campo de instância começa com "s_" ou o nome de um campo estático (compartilhado em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) começa com "M_". |
| [CA1505: Evitar código de difícil manutenção](../code-quality/ca1505.md) | Um tipo ou um método tem um baixo valor de índice de facilidade de manutenção. Um baixo índice de facilidade de manutenção indica que um tipo ou um método é provavelmente difícil de manter e seria um bom candidato para um novo design. |
| [CA1506: Evitar acoplamento de classes excessivo](../code-quality/ca1506.md) | Esta regra mede o acoplamento de classes contando o número de referências de tipo exclusivas que um tipo ou um método contém. |
| [CA1507: Usar nameof no lugar da cadeia de caracteres](../code-quality/ca1507.md) | Um literal de cadeia de caracteres é usado como um argumento em que uma `nameof` expressão pode ser usada. |
| [CA1508: Evitar código condicional morto](../code-quality/ca1508.md) | Um método tem código condicional que sempre é avaliado como `true` ou `false` em tempo de execução. Isso leva a um código inativo na `false` ramificação da condição. |
| [CA1509: Entrada inválida no arquivo de configuração de métrica de código](../code-quality/ca1509.md) | As regras de métricas de código, como [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) e [CA1506](ca1506.md), forneciam um arquivo de configuração chamado `CodeMetricsConfig.txt` que tem uma entrada inválida. |

## <a name="see-also"></a>Confira também

- [Meça a complexidade e a facilidade de manutenção do código gerenciado](../code-quality/code-metrics-values.md)
