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
ms.openlocfilehash: a35bec2395ccec649443df71e87904c71bf635d8
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547104"
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

O nome de um membro contém um nome de tipo de dados específico a um idioma.

Por padrão, essa regra só examina membros externos visíveis, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Os nomes de parâmetros e membros são mais usados para comunicar seu significado do que descrever seu tipo, que deve ser fornecido pelas ferramentas de desenvolvimento. Para nomes de membros, se um nome de tipo de dados precisar ser usado, use um nome independente de idioma em vez de um idioma específico. Por exemplo, em vez do C# nome `int`do tipo, use o nome do tipo de dados independente `Int32`de idioma,.

Cada token discreto no nome do parâmetro ou membro é verificado em relação aos seguintes nomes de tipo de dados específicos de idioma em uma maneira que não diferencia maiúsculas de minúsculas:

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

Além disso, os nomes de um parâmetro também são verificados em relação aos seguintes nomes de tipos de dados independentes de idioma de maneira não diferencia maiúsculas de minúsculas:

- Object
- Obj
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
- PTR
- Ponteiro
- UInptr
- UPtr
- UPointer
- Simples
- Duplo
- Decimal
- Guid

## <a name="how-to-fix-violations"></a>Como corrigir violações

**Se for acionado em um parâmetro:**

Substitua o identificador de tipo de dados no nome do parâmetro por um termo que melhor descreva seu significado ou um termo mais genérico, como ' value '.

**Se for acionado em relação a um membro:**

Substitua o identificador de tipo de dados específico do idioma no nome do membro por um termo que melhor descreva seu significado, um equivalente independente de idioma ou um termo mais genérico, como ' value '.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

O uso ocasional do parâmetro baseado em tipo e dos nomes de membros pode ser apropriado. No entanto, para o novo desenvolvimento, nenhum cenário conhecido ocorre onde você deve suprimir um aviso dessa regra. Para bibliotecas que foram enviadas anteriormente, talvez seja necessário suprimir um aviso dessa regra.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de analisadores do [FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1720.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (nomenclatura). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Regras relacionadas

- [CA1709: Os identificadores devem estar em maiúsculas e minúsculas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Os identificadores devem ser diferentes em mais do que caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719: Nomes de parâmetros não devem corresponder a nomes de membros](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)