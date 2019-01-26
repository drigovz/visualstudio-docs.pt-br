---
title: 'CA1025: Substituir argumentos repetitivos por matriz de parâmetros'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: de109dddf3bc0ddb8cd50df8dc27e81111d4b6df
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938504"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Substituir argumentos repetitivos por matriz de parâmetros

|||
|-|-|
|NomeDoTipo|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um método público ou protegido em um tipo público tem mais de três parâmetros e seus três últimos parâmetros são do mesmo tipo.

## <a name="rule-description"></a>Descrição da regra
 Use uma matriz de parâmetros em vez de argumentos repetidos, quando o número exato de argumentos é desconhecido e os argumentos variáveis forem do mesmo tipo, ou podem ser passados como o mesmo tipo. Por exemplo, o <xref:System.Console.WriteLine%2A> método fornece uma sobrecarga de uso geral que usa uma matriz de parâmetros para aceitar qualquer número de <xref:System.Object> argumentos.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, substitua os argumentos repetidos com uma matriz de parâmetros.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 É sempre seguro suprimir um aviso nessa regra; No entanto, esse design pode causar problemas de usabilidade.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola essa regra.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]