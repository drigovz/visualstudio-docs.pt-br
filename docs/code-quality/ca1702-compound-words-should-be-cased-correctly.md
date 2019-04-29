---
title: 'CA1702: Palavras compostas devem ter maiúsculas e minúsculas corretas'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f78ea4f44c48d2740df58def03a6335bce6637a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545926"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Palavras compostas devem ter maiúsculas e minúsculas corretas

|||
|-|-|
|NomeDoTipo|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra quando acionado em assemblies.<br /><br /> Sem quebra - quando disparado em parâmetros de tipo.|

## <a name="cause"></a>Causa

O nome de um identificador contém várias palavras e pelo menos uma das palavras parece ser uma palavra composta que não tem maiúsculas corretas.

## <a name="rule-description"></a>Descrição da regra

O nome do identificador é dividido em palavras que são baseadas em maiusculas. Cada combinação de duas palavras contígua é verificada pela biblioteca do verificador ortográfico da Microsoft. Se ele for reconhecido, o identificador produz uma violação da regra. São exemplos de palavras compostas que fazem com que uma violação "CheckSum" e "MultiPart", que deve ter maiusculas e minúsculas como "Checksum" e "Multipart", respectivamente. Devido ao uso anterior de comuns, várias exceções são incorporadas a regra e várias palavras únicas são sinalizadas, como "Ferramentas" e "Filename", que deve ter a grafia duas palavras distintas (nesse caso, "Ferramentas" e "FileName").

Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Altere o nome, de modo que ele é maiusculas e minúsculas corretas.

## <a name="language"></a>Idioma

O verificador ortográfico verifica atualmente apenas em relação a dicionários de cultura baseada em inglês. Você pode alterar a cultura do seu projeto no arquivo de projeto, adicionando a **CodeAnalysisCulture** elemento.

Por exemplo:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Se você definir a cultura como algo diferente de uma cultura com base em inglês, essa regra de análise de código é silenciosamente desabilitada.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso nessa regra, se ambas as partes da palavra composta são reconhecidas pelo dicionário de ortografia e a intenção é usar duas palavras.

## <a name="related-rules"></a>Regras relacionadas

- [CA1701: Palavras compostas da cadeia de caracteres de recurso devem ter maiusculas e minúsculas corretamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identificadores devem ser diferentes de maiusculas e minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Consulte também

- [Diretrizes de nomenclatura](/dotnet/standard/design-guidelines/naming-guidelines)
- [Convenções de maiúsculas e minúsculas](/dotnet/standard/design-guidelines/capitalization-conventions)