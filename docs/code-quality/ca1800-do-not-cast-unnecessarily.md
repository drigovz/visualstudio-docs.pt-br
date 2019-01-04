---
title: 'CA1800: Não converta sem necessidade'
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 1ef6e73812a63fdc4cc4392621ab49b279a32d18
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822023"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Não converta sem necessidade

|||
|-|-|
|NomeDoTipo|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
Um método realiza conversões duplicadas em um dos seus argumentos ou variáveis locais.

Para concluir a análise por essa regra, testado assembly deve ser criado usando as informações de depuração e o arquivo de banco de dados (. PDB) do programa associado deve estar disponível.

## <a name="rule-description"></a>Descrição da regra
As conversões duplicadas diminui o desempenho, especialmente quando as conversões são realizadas em instruções de iteração compactas. Para operações de conversão explícita de duplicados, armazenar o resultado da conversão em uma variável local e usa a variável local em vez de operações de conversão duplicados.

Se a linguagem c# `is` operador é usado para testar se a conversão for bem-sucedida antes que a conversão real é executada, Experimente testar o resultado do `as` operador em vez disso. Isso fornece a mesma funcionalidade sem a operação de conversão implícita é executada pelo `is` operador. Ou, no c# 7.0 e posterior, use o `is` operador com [correspondência de padrões](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) para verificar a conversão de tipo e converter a expressão a uma variável desse tipo em uma única etapa.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, modificar a implementação do método para minimizar o número de operações de conversão.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 É seguro para suprimir um aviso nessa regra, ou ignorar a regra completamente, se o desempenho não for uma preocupação.

## <a name="examples"></a>Exemplos
 O exemplo a seguir mostra um método que viola a regra usando o c# `is` operador. Um segundo método satisfaz a regra, substituindo o `is` operador com um teste com o resultado do `as` operador, que diminui o número de operações de conversão por iteração de dois para um. Um terceiro método também atende a regra usando `is` com [correspondência de padrões](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) para criar uma variável do tipo desejado se a conversão de tipo teria êxito.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 O exemplo a seguir mostra um método `start_Click`, que tem várias conversões explícitas duplicados que viola a regra e um método, `reset_Click`, que satisfaz a regra, armazenando a conversão em uma variável local.

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Consulte também

- [as (referência de c#)](/dotnet/csharp/language-reference/keywords/as)
- [IS (referência de c#)](/dotnet/csharp/language-reference/keywords/is)