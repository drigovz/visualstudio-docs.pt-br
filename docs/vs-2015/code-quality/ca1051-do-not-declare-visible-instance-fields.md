---
title: 'CA1051: não declarar campos de instância visíveis | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 41332ab7d729f7b2187ccace6b05fe2d17763a0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672512"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: não declarar campos de instância visíveis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Categoria|Microsoft. Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo visível externamente tem um campo de instância visível externamente.

## <a name="rule-description"></a>Descrição da Regra
 O principal uso de um campo deve ser um como um detalhe da implementação. Os campos devem ser `private` ou `internal` e devem ser expostos usando as propriedades. É tão fácil acessar uma propriedade quanto é acessar um campo, e o código nos acessadores de uma propriedade pode ser alterado à medida que os recursos do tipo se expandem sem introduzir alterações significativas. As propriedades que retornam apenas o valor de um campo privado ou interno são otimizadas para serem executadas em par com o acesso a um campo; um pequeno lucro de desempenho está associado ao uso de campos externos visíveis em Propriedades.

 Externamente visível refere-se aos níveis de acessibilidade `public`, `protected` e `protected internal` (`Public`, `Protected` e `Protected Friend` em Visual Basic).

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, torne o campo `private` ou `internal` e expor-o usando uma propriedade visível externamente.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Os campos visíveis externamente não fornecem nenhum benefício que não esteja disponível para propriedades. Além disso, os campos públicos não podem ser protegidos por [demandas de link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d). Consulte [CA2112: tipos protegidos não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo (`BadPublicInstanceFields`) que viola essa regra. `GoodPublicInstanceFields` mostra o código corrigido.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2112: os tipos seguros não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Consulte também
 [Demandas de link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
