---
title: 'CA1720: Identificadores não devem conter nomes de tipo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 504c985bd276a891b76e8c9b2a7c0ef51c3a490a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58927229"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Identificadores não devem conter nomes de tipos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de um parâmetro em um membro visível externamente contém um nome de tipo de dados.

 - ou -

 O nome de um membro visível externamente contém um nome de tipo de dados específicos de idioma.

## <a name="rule-description"></a>Descrição da Regra
 Nomes de parâmetros e membros são melhor usados para se comunicar seu significado que to descrevem seu tipo, que deve ser fornecido pelas ferramentas de desenvolvimento. Para nomes de membros, se um nome de tipo de dados deve ser usado, usam um nome independente de linguagem em vez de um idioma específico. Por exemplo, em vez do c# tipo nome 'int', use o nome do tipo de dados independente de idioma, Int32.

 Cada token discreto no nome do parâmetro ou membro é verificado em relação os seguintes nomes de tipo de dados específicos de idioma, no diferenciando maiusculas de minúsculas:

- Bool

- WChar

- Int8

- UInt8

- Abreviado

- UShort

- int

- UInt

- Inteiro

- UInteger

- Long

- ULong

- Não assinado

- Assinado

- Float

- Float32

- Float64

  Além disso, os nomes de um parâmetro também são verificados em relação os seguintes nomes de tipo de dados independente de idioma, diferenciando maiusculas de minúsculas:

- Objeto

- obj

- Boolean

- Char

- Cadeia de Caracteres

- SByte

- Byte

- UByte

- Int16

- UInt16

- Int32

- UInt32

- Int64

- UInt64

- IntPtr

- Ptr

- Ponteiro

- UInptr

- UPtr

- UPointer

- Simples

- Duplo

- Decimal

- Guid

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 **Se disparado em relação a um parâmetro:**

 Substitua o identificador de tipo de dados no nome do parâmetro com um termo que melhor descreve seu significado ou um termo mais genérico, como 'value'.

 **Se disparado em relação a um membro:**

 Substitua o identificador de tipo de dados específicos de idioma no nome do membro com um termo que melhor descreve seu significado, um equivalente independente da linguagem ou um termo mais genérico, como 'value'.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Uso ocasional de nomes de parâmetro e de membros com base no tipo pode ser apropriado. No entanto, para novos desenvolvimentos, nenhum conhecidos ocorrem de cenários em que você deve suprimir um aviso nessa regra. Para bibliotecas que têm anterior enviados, você pode ter que suprimir um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1709: Identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identificadores devem ser diferentes de maiusculas e minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: Nomes de parâmetro não devem corresponder aos nomes de membro](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
