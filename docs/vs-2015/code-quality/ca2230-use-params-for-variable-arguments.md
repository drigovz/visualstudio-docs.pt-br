---
title: 'CA2230: usar params para argumentos de variável | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a690544a7ed03094587a2aaf1c44b7ed68e8f2a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662828"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: usar parâmetros para argumentos variáveis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|UseParamsForVariableArguments|
|CheckId|CA2230|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público ou protegido contém um método público ou protegido que usa a Convenção de chamada `VarArgs`.

## <a name="rule-description"></a>Descrição da Regra
 A Convenção de chamada `VarArgs` é usada com determinadas definições de método que usam um número variável de parâmetros. Um método que usa a Convenção de chamada `VarArgs` não é compatível com Common Language Specification (CLS) e pode não estar acessível em linguagens de programação.

 No C#, a Convenção de chamada `VarArgs` é usada quando a lista de parâmetros de um método termina com a palavra-chave `__arglist`. Visual Basic não dá suporte à Convenção de chamada de `VarArgs`, C++ e o Visual permite seu uso somente em código não gerenciado que usa a notação de `...` de elipse.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra no C#, use a palavra-chave [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) em vez de `__arglist`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra dois métodos, um que viola a regra e outra que satisfaz a regra.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Consulte também
 [independência de idioma <xref:System.Reflection.CallingConventions?displayProperty=fullName> e componentes independentes de linguagem](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
