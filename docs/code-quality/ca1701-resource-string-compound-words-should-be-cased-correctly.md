---
title: 'CA1701: Palavras compostas de cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: bf671e8c948f4554225278982c4db794fedb974d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023373"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Palavras compostas de cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas

|||
|-|-|
|NomeDoTipo|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Uma cadeia de caracteres de recurso contém uma palavra composta que não parece ter maiusculas e minúsculas corretamente.

## <a name="rule-description"></a>Descrição da regra

Cada palavra na cadeia de caracteres de recurso é dividida em tokens que são baseados em maiusculas. Cada combinação contígua de dois tokens é verificada pela biblioteca do verificador ortográfico da Microsoft. Se reconhecidas, as palavras produzirão uma violação da regra. São exemplos de palavras compostas que fazem com que uma violação "CheckSum" e "MultiPart", que deve ter maiusculas e minúsculas como "Checksum" e "Multipart", respectivamente. Devido ao uso anterior de comuns, várias exceções são incorporadas a regra e várias palavras únicas são sinalizadas como "Ferramentas" e "Filename", que deve ter a grafia duas palavras distintas. Neste exemplo, "Ferramentas" e "FileName" será sinalizado.

Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Altere a palavra para que ele é maiusculas e minúsculas corretas.

## <a name="change-the-dictionary-language"></a>Alterar o idioma do dicionário

Por padrão, a versão em inglês (en) do verificador ortográfico é usada. Se você quiser alterar o idioma do verificador ortográfico, você poderá fazê-lo com a adição de um dos seguintes atributos para seus *AssemblyInfo.cs* ou *AssemblyInfo* arquivo:

- Use <xref:System.Reflection.AssemblyCultureAttribute> para especificar a cultura, se os recursos estiverem em um assembly satélite.
- Use <xref:System.Resources.NeutralResourcesLanguageAttribute> para especificar o *cultura neutra* do seu assembly, se os recursos estiverem no mesmo assembly que seu código.

> [!IMPORTANT]
> Se você definir a cultura como algo diferente de uma cultura com base em inglês, essa regra de análise de código é silenciosamente desabilitada.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso nessa regra, se ambas as partes da palavra composta são reconhecidas pelo dicionário de ortografia e a intenção é usar duas palavras.

Você também pode adicionar palavras compostas a um dicionário personalizado para o verificador ortográfico. Palavras no dicionário personalizado não causam violações. Para obter mais informações, confira [Como: Personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Regras relacionadas

- [CA1702: Palavras compostas devem ter maiusculas e minúsculas corretamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: Identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identificadores devem ser diferentes de maiusculas e minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Consulte também

- [Convenções de maiúsculas e minúsculas](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Diretrizes de nomenclatura](/dotnet/standard/design-guidelines/naming-guidelines)