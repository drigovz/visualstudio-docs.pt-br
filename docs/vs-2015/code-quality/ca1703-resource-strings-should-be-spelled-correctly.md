---
title: 'CA1703: Cadeias de caracteres de recurso devem ter grafia correta | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c1ff5a2600a4f40673f7d38dfe551ab9ac8cfe29
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923365"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Cadeias de caracteres de recurso devem ser escritas corretamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Uma cadeia de caracteres de recurso contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft.

## <a name="rule-description"></a>Descrição da Regra
 Esta regra analisa a cadeia de caracteres de recurso em palavras (criar tokens de palavras compostas) e verifica a ortografia de cada palavra/token. Para obter informações sobre o algoritmo de análise, consulte [CA1704: Identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 Por padrão, a versão em inglês (en) do verificador ortográfico é usada.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, use palavras completas que estão escritas corretamente ou adicioná-las a um dicionário personalizado. Para obter informações sobre como usar dicionários personalizados, consulte [CA1704: Identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Corretamente as palavras escritas de reduzem o tempo necessário para aprender novas bibliotecas de software.

## <a name="related-rules"></a>Regras relacionadas
 [CA1701: Palavras compostas da cadeia de caracteres de recurso devem ter maiusculas e minúsculas corretamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: Identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: Literais devem ter grafia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
