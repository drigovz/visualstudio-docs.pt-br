---
title: Usando sequências de escape em modelos de texto
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6de30faec90fd59531187d09f7eef76c3db7b043
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910435"
---
# <a name="using-escape-sequences-in-text-templates"></a>Usando sequências de escape em modelos de texto
Você pode usar sequências de escape em modelos de texto para gerar marcações de modelo de texto e (no C# somente código) para caracteres de controle de escape e aspas.

 Para imprimir as marcas de abertura e fechamento de um bloco de código padrão para o arquivo de saída, escape as marcas da seguinte maneira:

```
\<# ... \#>
```

 Você pode fazer o mesmo com marcas de bloco outro texto modelo diretiva e código.

 Se um bloco de texto inclui cadeias de caracteres usadas para sair de marcas do modelo de texto, em seguida, você pode usar as seguintes sequências de escape:

-   Se uma marca de modelo de texto é precedida por um número par de escape (\\) caracteres o modelo de analisador será incluir metade dos caracteres de escape e a sequência como uma marca de modelo de texto. Por exemplo, se houver quatro caracteres de escape no modelo de texto, haverá dois "\\" caracteres no arquivo gerado.

-   Se a marcação de modelo de texto é precedida por um número ímpar de escape (\\) caracteres, o analisador de modelo incluirá metade da "\\" caracteres além de marca em si (\<# ou #>). A marca não é considerada uma marca de modelo de texto.

-   Se um escape (\\) caracteres é exibida em qualquer lugar em qualquer sequência diferente de onde ele realiza o escape de um caractere de controle ou uma cotação (no C# somente), o caractere será gerado diretamente.

## <a name="see-also"></a>Consulte também

- [Como: Gerar modelos a partir de modelos usando sequências de Escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)