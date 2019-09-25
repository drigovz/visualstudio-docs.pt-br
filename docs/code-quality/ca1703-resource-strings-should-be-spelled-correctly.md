---
title: 'CA1703: Cadeias de caracteres de recurso devem ser escritas corretamente'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edd3945953a07b10aee5c2690a25aafe446e2c10
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234317"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Cadeias de caracteres de recurso devem ser escritas corretamente

|||
|-|-|
|NomeDoTipo|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Categoria|Microsoft.Naming|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Uma cadeia de caracteres de recurso contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft.

## <a name="rule-description"></a>Descrição da regra

Essa regra analisa a cadeia de caracteres do recurso em palavras (tokening de palavras compostas) e verifica a ortografia de cada palavra/token. Para obter informações sobre o algoritmo de análise, [consulte CA1704: Os identificadores devem ser escritos](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)corretamente.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, use palavras completas que estejam grafadas corretamente ou adicione as palavras a um dicionário personalizado. Para obter informações sobre como usar dicionários personalizados, [consulte CA1704: Os identificadores devem ser escritos](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)corretamente.

## <a name="change-the-dictionary-language"></a>Alterar o idioma do dicionário

Por padrão, a versão em inglês (EN) do verificador ortográfico é usada. Se você quiser alterar o idioma do verificador ortográfico, poderá fazê-lo adicionando um dos seguintes atributos ao seu arquivo *AssemblyInfo.cs* ou *AssemblyInfo. vb* :

- Use <xref:System.Reflection.AssemblyCultureAttribute> para especificar a cultura se seus recursos estiverem em um assembly satélite.
- Use <xref:System.Resources.NeutralResourcesLanguageAttribute> para especificar a *cultura neutra* do assembly se seus recursos estiverem no mesmo assembly que o seu código.

> [!IMPORTANT]
> Se você definir a cultura como algo diferente de uma cultura baseada em inglês, essa regra de análise de código será silenciosamente desabilitada.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. Palavras escritas corretamente reduzem o tempo necessário para aprender novas bibliotecas de software.

## <a name="related-rules"></a>Regras relacionadas

- [CA1701: As palavras compostas da cadeia de recursos devem estar em maiúsculas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Os identificadores devem ser escritos corretamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Os literais devem ser escritos corretamente](../code-quality/ca2204-literals-should-be-spelled-correctly.md)