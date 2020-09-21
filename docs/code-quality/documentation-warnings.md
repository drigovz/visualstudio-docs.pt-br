---
title: Regras de documentação
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- rules, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f4ec6a0dd154dae89145add26c60a8b1322a444
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808646"
---
# <a name="documentation-rules"></a>Regras de documentação

As regras de documentação dão suporte à gravação de bibliotecas bem documentadas por meio do uso correto de [comentários de documentação XML](/dotnet/csharp/codedoc) para APIs visíveis externamente.

## <a name="in-this-section"></a>Nesta seção

| Regra | Descrição |
| - | - |
| [CA1200: Evitar o uso de marcas cref com um prefixo](../code-quality/ca1200.md) | O atributo [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) em uma marca de documentação XML significa "referência de código". Ele especifica que o texto interno da marca é um elemento de código, como um tipo, método ou propriedade. Evite usar `cref` marcas com prefixos, pois isso impede que o compilador Verifique as referências. Ele também impede que o IDE (ambiente de desenvolvimento integrado) do Visual Studio Localize e atualize essas referências de símbolo durante refatoração. |

## <a name="see-also"></a>Confira também

- [Regras de análise de código](../code-quality/code-analysis-for-managed-code-warnings.md)
