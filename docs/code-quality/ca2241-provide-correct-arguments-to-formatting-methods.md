---
title: 'CA2241: Fornecer argumentos corretos para métodos de formatação'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3767d361375ce1b3d54281a6850d9ac3b960ece6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237864"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Fornecer argumentos corretos para métodos de formatação

|||
|-|-|
|NomeDoTipo|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Categoria|Microsoft.Usage|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
O `format` argumento de cadeia de caracteres passado para um <xref:System.Console.WriteLine%2A>método <xref:System.Console.Write%2A>como, <xref:System.String.Format%2A?displayProperty=fullName> ou não contém um item de formato que corresponde a cada argumento de objeto, ou vice-versa.

## <a name="rule-description"></a>Descrição da regra
Os argumentos para métodos <xref:System.Console.WriteLine%2A>como, <xref:System.Console.Write%2A>e <xref:System.String.Format%2A> consistem em uma cadeia de caracteres de formato seguida <xref:System.Object?displayProperty=fullName> por várias instâncias. A cadeia de caracteres de formato consiste em texto e itens de formato inseridos do formulário, {index [, Alignment] [: formatString]}. ' Index ' é um inteiro de base zero que indica qual dos objetos a serem formatados. Se um objeto não tiver um índice correspondente na cadeia de caracteres de formato, o objeto será ignorado. Se o objeto especificado por ' Index ' não existir, um <xref:System.FormatException?displayProperty=fullName> será lançado no tempo de execução.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, forneça um item de formato para cada argumento de objeto e forneça um argumento de objeto para cada item de formato.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra duas violações da regra.

[!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
[!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]