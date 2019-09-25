---
title: 'CA1025: Substituir argumentos repetitivos por matriz de parâmetros'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f65d64dd4e881c41b17cd7cb9dc072a6fe800766
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236140"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Substituir argumentos repetitivos por matriz de parâmetros

|||
|-|-|
|NomeDoTipo|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Categoria|Microsoft.Design|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um método público ou protegido em um tipo público tem mais de três parâmetros, e seus últimos três parâmetros são do mesmo tipo.

## <a name="rule-description"></a>Descrição da regra
Use uma matriz de parâmetros em vez de argumentos repetidos quando o número exato de argumentos for desconhecido e os argumentos da variável forem do mesmo tipo, ou podem ser passados como o mesmo tipo. Por exemplo, o <xref:System.Console.WriteLine%2A> método fornece uma sobrecarga de finalidade geral que usa uma matriz de parâmetros para aceitar qualquer número <xref:System.Object> de argumentos.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, substitua os argumentos repetidos por uma matriz de parâmetros.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É sempre seguro suprimir um aviso dessa regra; no entanto, esse design pode causar problemas de usabilidade.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo que viola essa regra.

[!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]