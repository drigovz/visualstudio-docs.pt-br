---
title: 'CA2230: Usar parâmetros para argumentos variáveis'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0639d30771b3a6bb288ddbf9644dda2efcd5f90d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231357"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Usar parâmetros para argumentos variáveis

|||
|-|-|
|NomeDoTipo|UseParamsForVariableArguments|
|CheckId|CA2230|
|Categoria|Microsoft.Usage|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo público ou protegido contém um método público ou protegido que usa a `VarArgs` Convenção de chamada.

## <a name="rule-description"></a>Descrição da regra
A `VarArgs` Convenção de chamada é usada com determinadas definições de método que usam um número variável de parâmetros. Um método que usa `VarArgs` a Convenção de chamada não é compatível com CLS (Common Language Specification) e pode não estar acessível em linguagens de programação.

No C#, a `VarArgs` Convenção de chamada é usada quando a lista de parâmetros de um método `__arglist` termina com a palavra-chave. Visual Basic não oferece suporte à `VarArgs` Convenção de chamada, e C++ o Visual permite seu uso somente em código não gerenciado que usa a `...` notação de elipse.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra no C#, use a palavra-chave [params](/dotnet/csharp/language-reference/keywords/params) em `__arglist`vez de.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra dois métodos, um que viola a regra e outra que satisfaz a regra.

[!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [Componentes de independência de linguagem e componentes independentes da linguagem](/dotnet/standard/language-independence-and-language-independent-components)