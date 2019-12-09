---
title: 'CA1703: as cadeias de caracteres de recurso devem ser escritas corretamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9574ff022e0d5407b2683e5ba7a6b2e0cde5201e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669230"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Categoria|Microsoft. Naming|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Uma cadeia de caracteres de recurso contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra analisa a cadeia de caracteres do recurso em palavras (tokening de palavras compostas) e verifica a ortografia de cada palavra/token. Para obter informações sobre o algoritmo de análise, consulte [CA1704: identificadores devem ser escritos corretamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 Por padrão, a versão em inglês (EN) do verificador ortográfico é usada.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, use palavras completas que estejam grafadas corretamente ou adicione as palavras a um dicionário personalizado. Para obter informações sobre como usar dicionários personalizados, consulte [CA1704: os identificadores devem ser escritos corretamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Palavras escritas corretamente reduzem o tempo necessário para aprender novas bibliotecas de software.

## <a name="related-rules"></a>Regras relacionadas
 [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: os literais devem ter a ortografia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
