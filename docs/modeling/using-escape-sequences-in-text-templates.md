---
title: Usando sequências de escape em modelos de texto
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e03f5eafc00b8431725ed06da10371a93692fb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662927"
---
# <a name="use-escape-sequences-in-text-templates"></a>Usar sequências de escape em modelos de texto

Você pode usar sequências de escape em modelos de texto para gerar marcas de modelo C# de texto e (somente em código) para escapar caracteres de controle e aspas.

Para imprimir marcas abertas e fechadas para um bloco de código padrão no arquivo de saída, escape as marcas da seguinte maneira:

```
\<# ... \#>
```

Você pode fazer o mesmo com outras diretivas de modelo de texto e marcas de bloco de código.

Se um bloco de texto incluir cadeias de caracteres usadas para escapar marcas de modelo de texto, você poderá usar as seguintes sequências de escape:

- Se uma marca de modelo de texto for precedida por um número par de caracteres de escape (\\), o analisador de modelo incluirá metade dos caracteres de escape e incluirá a sequência como uma marca de modelo de texto. Por exemplo, se houver quatro caracteres de escape no modelo de texto, haverá dois caracteres "\\" no arquivo gerado.

- Se a marca de modelo de texto for precedida por um número ímpar de caracteres de escape (\\), o analisador de modelo incluirá metade dos caracteres de "\\" mais a marca (\< # ou # >). A marca não é considerada uma marca de modelo de texto.

- Se um caractere de escape (\\) aparecer em qualquer lugar em qualquer sequência diferente de onde ele sai de um caractere de controle ou de C# uma aspa (em apenas), o caractere será impresso diretamente.

## <a name="see-also"></a>Consulte também

- [Como gerar modelos com base em modelos usando sequências de escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)