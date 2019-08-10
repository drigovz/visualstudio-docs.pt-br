---
title: 'CA1800: Não converta sem necessidade'
ms.date: 10/26/2017
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 942a9911d0dadbf5f130344735ca9aa504cb71fd
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921591"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Não converta sem necessidade

|||
|-|-|
|NomeDoTipo|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um método executa conversões duplicadas em um de seus argumentos ou variáveis locais.

Para uma análise completa por essa regra, o assembly testado deve ser criado usando informações de depuração e o arquivo de banco de dados do programa (. pdb) associado deve estar disponível.

## <a name="rule-description"></a>Descrição da regra
As conversões duplicadas diminui o desempenho, especialmente quando as conversões são realizadas em instruções de iteração compactas. Para operações de conversão duplicadas explícitas, armazene o resultado da conversão em uma variável local e use a variável local em vez das operações de conversão duplicadas.

Se o C# `is` operador for usado para testar se a conversão terá sucesso antes da execução da conversão real, considere testar `as` o resultado do operador. Isso fornece a mesma funcionalidade sem a operação de conversão implícita que é executada pelo `is` operador. Ou, em C# 7,0 e posterior, use o `is` operador com [correspondência de padrões](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) para verificar a conversão de tipo e converter a expressão em uma variável desse tipo em uma etapa.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, modifique a implementação do método para minimizar o número de operações de conversão.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra ou ignorar completamente a regra, se o desempenho não for uma preocupação.

## <a name="examples"></a>Exemplos
O exemplo a seguir mostra um método que viola a regra usando o C# `is` operador. Um segundo método satisfaz a regra, substituindo o `is` operador por um teste em relação ao resultado `as` do operador, o que diminui o número de operações de conversão por iteração de dois para um. Um terceiro método também satisfaz a regra usando `is` with Matching [Pattern](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) para criar uma variável do tipo desejado se a conversão de tipo for bem sucedido.

[!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

O exemplo a seguir mostra um método `start_Click`,, que tem várias conversões explícitas duplicadas, que violam a regra e um `reset_Click`método, que satisfaz a regra armazenando a conversão em uma variável local.

[!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
[!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Consulte também

- [como (C# referência)](/dotnet/csharp/language-reference/keywords/as)
- [é (C# referência)](/dotnet/csharp/language-reference/keywords/is)