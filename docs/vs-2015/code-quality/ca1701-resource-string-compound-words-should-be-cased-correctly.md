---
title: 'CA1701: Palavras compostas da cadeia de caracteres de recurso devem ter maiusculas e minúsculas corretamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d6c71286e5aff5928717402912d99f37a49a38f7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923341"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Palavras compostas de cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Uma cadeia de caracteres de recurso contém uma palavra composta que não parece ter maiusculas e minúsculas corretamente.

## <a name="rule-description"></a>Descrição da Regra
 Cada palavra na cadeia de caracteres de recurso é dividida em tokens que são baseados em maiusculas. Cada combinação contígua de dois tokens é verificada pela biblioteca do verificador ortográfico da Microsoft. Se reconhecidas, as palavras produzirão uma violação da regra. São exemplos de palavras compostas que fazem com que uma violação "CheckSum" e "MultiPart", que deve ter maiusculas e minúsculas como "Checksum" e "Multipart", respectivamente. Devido ao uso anterior de comuns, várias exceções são incorporadas a regra e várias palavras únicas são sinalizadas como "Ferramentas" e "Filename", que deve ter a grafia duas palavras distintas. Neste exemplo, "Ferramentas" e "FileName" será sinalizado.

 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Altere a palavra para que ele é maiusculas e minúsculas corretas.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, se ambas as partes da palavra composta são reconhecidas pelo dicionário de ortografia e a intenção é usar duas palavras.

 Você também pode adicionar palavras compostas a um dicionário personalizado para o verificador ortográfico. Palavras no dicionário personalizado não causam violações. Para obter mais informações, confira [Como: Personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Regras relacionadas
 [CA1702: Palavras compostas devem ter maiusculas e minúsculas corretamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: Identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identificadores devem ser diferentes de maiusculas e minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Consulte também
 [Convenções de capitalização](http://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) [diretrizes de nomenclatura](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)
