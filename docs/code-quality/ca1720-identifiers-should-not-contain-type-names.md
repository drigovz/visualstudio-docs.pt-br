---
title: 'CA1720: Identificadores não devem conter nomes de tipos'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0eb7cfeb2271b7ed01f59d4892987fb2ef72808
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546564"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Identificadores não devem conter nomes de tipos

|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

O nome de um parâmetro em um membro contém um nome de tipo de dados.

- ou -

O nome de um membro contém um nome de tipo de dados específicos de idioma.

Por padrão, essa regra olha apenas para membros visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Nomes de parâmetros e membros são melhor usados para se comunicar seu significado que to descrevem seu tipo, que deve ser fornecido pelas ferramentas de desenvolvimento. Para nomes de membros, se um nome de tipo de dados deve ser usado, usam um nome independente de linguagem em vez de um idioma específico. Por exemplo, em vez do C# nome do tipo `int`, use o nome do tipo de dados independente de idioma, `Int32`.

Cada token discreto no nome do parâmetro ou membro é verificado em relação os seguintes nomes de tipo de dados específicos de idioma no diferenciando maiusculas de minúsculas:

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

Além disso, os nomes de um parâmetro também são verificados em relação os seguintes nomes de tipo de dados independente de linguagem diferenciando maiusculas de minúsculas:

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

## <a name="how-to-fix-violations"></a>Como corrigir violações

**Se disparado em relação a um parâmetro:**

Substitua o identificador de tipo de dados no nome do parâmetro com um termo que melhor descreve seu significado ou um termo mais genérico, como 'value'.

**Se disparado em relação a um membro:**

Substitua o identificador de tipo de dados específicos de idioma no nome do membro com um termo que melhor descreve seu significado, um equivalente independente da linguagem ou um termo mais genérico, como 'value'.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Uso ocasional de nomes de parâmetro e de membros com base no tipo pode ser apropriado. No entanto, para novos desenvolvimentos, nenhum conhecidos ocorrem de cenários em que você deve suprimir um aviso nessa regra. Para bibliotecas que foram enviados anteriormente, você pode ter que suprimir um aviso nessa regra.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```
dotnet_code_quality.ca1720.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (nomenclatura). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Regras relacionadas

- [CA1709: Identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identificadores devem ser diferentes de maiusculas e minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719: Nomes de parâmetro não devem corresponder aos nomes de membro](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)