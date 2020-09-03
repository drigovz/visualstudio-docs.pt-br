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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72807103"
---
# <a name="documentation-warnings"></a>Avisos de documentação

Os avisos de documentação dão suporte à criação de bibliotecas bem documentadas por meio do uso correto de [comentários de documentação XML](/dotnet/csharp/codedoc) para APIs visíveis externamente.

## <a name="in-this-section"></a>Nesta seção

| Regra | Descrição |
| - | - |
| [CA1200: Evitar o uso de marcas cref com um prefixo](../code-quality/ca1200.md) | O atributo [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) em uma marca de documentação XML significa "referência de código". Ele especifica que o texto interno da marca é um elemento de código, como um tipo, método ou propriedade. Evite usar `cref` marcas com prefixos, pois isso impede que o compilador Verifique as referências. Ele também impede que o IDE (ambiente de desenvolvimento integrado) do Visual Studio Localize e atualize essas referências de símbolo durante refatoração. |

## <a name="see-also"></a>Confira também

- [Avisos de análise de código](../code-quality/code-analysis-for-managed-code-warnings.md)
