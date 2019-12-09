---
title: Avisos de documentação
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation warnings
- managed code analysis warnings, documentation warnings
- warnings, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4946c69bbbe4bf1c240967ebd93ef58cfa79e333
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807103"
---
# <a name="documentation-warnings"></a>Avisos de documentação

Os avisos de documentação dão suporte à criação de bibliotecas bem documentadas por meio do uso correto de [comentários de documentação XML](/dotnet/csharp/codedoc) para APIs visíveis externamente.

## <a name="in-this-section"></a>Nesta seção

| Regra | Descrição |
| - | - |
| [CA1200: Evite usar marcas cref com um prefixo](../code-quality/ca1200.md) | O atributo [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) em uma marca de documentação XML significa "referência de código". Ele especifica que o texto interno da marca é um elemento de código, como um tipo, método ou propriedade. Evite usar marcas `cref` com prefixos, porque isso impede que o compilador Verifique as referências. Ele também impede que o IDE (ambiente de desenvolvimento integrado) do Visual Studio Localize e atualize essas referências de símbolo durante refatoração. |

## <a name="see-also"></a>Consulte também

- [Avisos de análise de código](../code-quality/code-analysis-for-managed-code-warnings.md)
