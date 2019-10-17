---
title: 'CA1701: as palavras compostas da cadeia de caracteres do recurso devem ter maiúsculas e minúsculas corretas'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5d7aa3c29ca8ba82f6c50b070c5210cf10d1884
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443934"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: as palavras compostas da cadeia de caracteres do recurso devem ter maiúsculas e minúsculas corretas

|||
|-|-|
|NomeDoTipo|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Categoria|Microsoft. Naming|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Uma cadeia de caracteres de recurso contém uma palavra composta que não parece estar em maiúsculas corretamente.

## <a name="rule-description"></a>Descrição da regra

Cada palavra na cadeia de caracteres de recurso é dividida em tokens baseados em maiúsculas e minúsculas. Cada combinação contígua de dois tokens é verificada pela biblioteca do verificador ortográfico da Microsoft. Se reconhecidas, as palavras produzirão uma violação da regra. Exemplos de palavras compostas que causam uma violação são "CheckSum" e "MultiPart", que devem ser totais como "Checksum" e "multipart", respectivamente. Devido ao uso comum anterior, várias exceções são incorporadas à regra, e várias palavras únicas são sinalizadas, como "Toolbar" e "filename", que devem ser maiúsculas e minúsculas como duas palavras distintas. Neste exemplo, "ToolBar" e "FileName" seriam sinalizados.

As convenções de nomenclatura fornecem uma aparência comum para as bibliotecas direcionadas ao Common Language Runtime. Isso reduz a curva de aprendizado necessária para novas bibliotecas de software e aumenta a confiança do cliente de que a biblioteca foi desenvolvida por alguém que tenha experiência no desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Altere a palavra de forma que ela fique correta.

## <a name="change-the-dictionary-language"></a>Alterar o idioma do dicionário

Por padrão, a versão em inglês (EN) do verificador ortográfico é usada. Se você quiser alterar o idioma do verificador ortográfico, poderá fazê-lo adicionando um dos seguintes atributos ao seu arquivo *AssemblyInfo.cs* ou *AssemblyInfo. vb* :

- Use <xref:System.Reflection.AssemblyCultureAttribute> para especificar a cultura se os recursos estiverem em um assembly satélite.
- Use <xref:System.Resources.NeutralResourcesLanguageAttribute> para especificar a *cultura neutra* do assembly se seus recursos estiverem no mesmo assembly que o seu código.

> [!IMPORTANT]
> Se você definir a cultura como algo diferente de uma cultura baseada em inglês, essa regra de análise de código será silenciosamente desabilitada.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra se ambas as partes da palavra composta forem reconhecidas pelo dicionário ortográfico e a intenção for usar duas palavras.

Você também pode adicionar palavras compostas a um dicionário personalizado para o verificador ortográfico. As palavras no dicionário personalizado não causam violações. Para obter mais informações, consulte [como: personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Regras relacionadas

- [CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Consulte também

- [Convenções de maiúsculas e minúsculas](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Diretrizes de nomenclatura](/dotnet/standard/design-guidelines/naming-guidelines)
