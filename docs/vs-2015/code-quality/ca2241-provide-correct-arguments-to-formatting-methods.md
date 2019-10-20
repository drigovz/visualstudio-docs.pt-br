---
title: 'CA2241: fornecer argumentos corretos aos métodos de formatação | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 112065b2a8b9a88241ce62dda7b32a2f2c22fc75
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672021"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: fornecer argumentos corretos para métodos de formatação
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 O argumento de cadeia de caracteres `format` passado para um método como <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> ou <xref:System.String.Format%2A?displayProperty=fullName> não contém um item de formato que corresponde a cada argumento de objeto ou vice-versa.

## <a name="rule-description"></a>Descrição da Regra
 Os argumentos para métodos como <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> e <xref:System.String.Format%2A> consistem em uma cadeia de caracteres de formato seguida por várias instâncias de <xref:System.Object?displayProperty=fullName>. A cadeia de caracteres de formato consiste em texto e itens de formato inseridos do formulário, {index [, Alignment] [: formatString]}. ' Index ' é um inteiro de base zero que indica qual dos objetos a serem formatados. Se um objeto não tiver um índice correspondente na cadeia de caracteres de formato, o objeto será ignorado. Se o objeto especificado por ' Index ' não existir, um <xref:System.FormatException?displayProperty=fullName> será lançado em tempo de execução.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, forneça um item de formato para cada argumento de objeto e forneça um argumento de objeto para cada item de formato.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra duas violações da regra.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
