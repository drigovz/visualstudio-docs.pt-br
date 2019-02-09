---
title: 'CA1708: Identificadores devem ser diferentes em algo além das maiúsculas e minúsculas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 204e19e6abb40b8b50af4bd8b206c643f44e08ba
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920074"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Identificadores devem ser diferentes em algo além das maiúsculas e minúsculas

|||
|-|-|
|NomeDoTipo|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Os nomes dos dois tipos, membros, parâmetros ou espaços para nomes totalmente qualificados são idênticos quando eles são convertidos em minúsculas.

## <a name="rule-description"></a>Descrição da regra
 Os identificadores de namespaces, tipos, membros e parâmetros não podem se diferenciar apenas por maiúsculas porque linguagens com o Common Language Runtime como destino não precisam diferenciar maiúsculas e minúsculas. Por exemplo, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] é uma linguagem diferencia maiusculas de minúsculas amplamente utilizada.

 Essa regra é acionada em apenas a membros publicamente visível.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Selecione um nome exclusivo quando comparado a outros identificadores no diferenciando maiusculas de minúsculas.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra. A biblioteca não pode ser utilizada em todos os idiomas disponíveis no .NET Framework.

## <a name="example-of-a-violation"></a>Exemplo de uma violação
 O exemplo a seguir demonstra uma violação dessa regra.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1709: Identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)