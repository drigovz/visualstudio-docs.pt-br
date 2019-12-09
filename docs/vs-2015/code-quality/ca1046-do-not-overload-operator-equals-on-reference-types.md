---
title: 'CA1046: não sobrecarregar o operador Equals em tipos de referência | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 519faf2d49cb74d60d342d6bcf449f211076b0b4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661094"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: não sobrecarregar igualdades de operador em tipos de referência
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Categoria|Microsoft. Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo de referência pública pública ou aninhada sobrecarrega o operador de igualdade.

## <a name="rule-description"></a>Descrição da Regra
 Para tipos de referência, a implementação padrão do operador de igualdade está quase sempre correta. Por padrão, duas referências só serão iguais se apontarem para o mesmo objeto.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova a implementação do operador de igualdade.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra quando o tipo de referência se comporta como um tipo de valor interno. Se for significativo fazer adição ou subtração em instâncias do tipo, provavelmente será correto implementar o operador de igualdade e suprimir a violação.

## <a name="example"></a>Exemplo
 O exemplo a seguir demonstra o comportamento padrão ao comparar duas referências.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Exemplo
 O aplicativo a seguir compara algumas referências.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 Este exemplo gerencia a seguinte saída.

 **a = New (2, 2) e b = New (2, 2) são iguais? Não** 
**c e a são iguais? Sim** 
**b e a são = =? Não** 
**c e a são = =? Sim**
## <a name="related-rules"></a>Regras relacionadas
 [CA1013: sobrecarregar operador Equals ao sobrecarregar adicionar e subtrair](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Consulte também
 [operadores de igualdade](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a) <xref:System.Object.Equals%2A?displayProperty=fullName>
