---
title: Usando sequências de escape em modelos de texto
description: Saiba como você pode usar sequências de escape em modelos de texto para gerar marcas de modelo de texto e para escapar caracteres de controle e aspas apenas em código C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 126fe3f4e42c9c6cf0b75bf740e1e7e2c4b269ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924333"
---
# <a name="use-escape-sequences-in-text-templates"></a>Usar sequências de escape em modelos de texto

Você pode usar sequências de escape em modelos de texto para gerar marcas de modelo de texto e (somente em código C#) para escapar caracteres de controle e aspas.

Para imprimir marcas abertas e fechadas para um bloco de código padrão no arquivo de saída, escape as marcas da seguinte maneira:

```
\<# ... \#>
```

Você pode fazer o mesmo com outras diretivas de modelo de texto e marcas de bloco de código.

Se um bloco de texto incluir cadeias de caracteres usadas para escapar marcas de modelo de texto, você poderá usar as seguintes sequências de escape:

- Se uma marca de modelo de texto for precedida por um número par de \\ caracteres escape (), o analisador de modelo incluirá metade dos caracteres de escape e incluirá a sequência como uma marca de modelo de texto. Por exemplo, se houver quatro caracteres de escape no modelo de texto, haverá dois \\ caracteres "" no arquivo gerado.

- Se a marca de modelo de texto for precedida por um número ímpar de \\ caracteres escape (), o analisador de modelo incluirá metade dos \\ caracteres "" mais a marca em si ( \<# or #> ). A marca não é considerada uma marca de modelo de texto.

- Se um caractere de escape ( \\ ) aparecer em qualquer lugar em qualquer sequência diferente de onde ele sai de um caractere de controle ou de uma aspa (somente em C#), o caractere será impresso diretamente.

## <a name="see-also"></a>Consulte também

- [Como gerar modelos a partir de modelos usando sequências de escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
