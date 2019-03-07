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
ms.openlocfilehash: 2643ff7cb8ce401462be7e5c1e52d5f985896f3a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55915720"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Cadeias de caracteres de recurso devem ser escritas corretamente

|||
|-|-|
|NomeDoTipo|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Uma cadeia de caracteres de recurso contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft.

## <a name="rule-description"></a>Descrição da regra

Esta regra analisa a cadeia de caracteres de recurso em palavras (criar tokens de palavras compostas) e verifica a ortografia de cada palavra/token. Para obter informações sobre o algoritmo de análise, consulte [CA1704: Identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, use palavras completas que estão escritas corretamente ou adicioná-las a um dicionário personalizado. Para obter informações sobre como usar dicionários personalizados, consulte [CA1704: Identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Alterar o idioma do dicionário

Por padrão, a versão em inglês (en) do verificador ortográfico é usada. Se você quiser alterar o idioma do verificador ortográfico, você poderá fazê-lo com a adição de um dos seguintes atributos para seus *AssemblyInfo.cs* ou *AssemblyInfo* arquivo:

- Use <xref:System.Reflection.AssemblyCultureAttribute> para especificar a cultura, se os recursos estiverem em um assembly satélite.
- Use <xref:System.Resources.NeutralResourcesLanguageAttribute> para especificar o *cultura neutra* do seu assembly, se os recursos estiverem no mesmo assembly que seu código.

> [!IMPORTANT]
> Se você definir a cultura como algo diferente de uma cultura com base em inglês, essa regra de análise de código é silenciosamente desabilitada.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. Corretamente as palavras escritas de reduzem o tempo necessário para aprender novas bibliotecas de software.

## <a name="related-rules"></a>Regras relacionadas

- [CA1701: Palavras compostas da cadeia de caracteres de recurso devem ter maiusculas e minúsculas corretamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Literais devem ter grafia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)