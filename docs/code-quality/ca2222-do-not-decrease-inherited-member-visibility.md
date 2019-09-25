---
title: 'CA2222: Não diminuir a visibilidade dos membros herdados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c737a30569ab4cd59931a3fca0e500ebe96e62de
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230975"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Não diminuir a visibilidade dos membros herdados

|||
|-|-|
|NomeDoTipo|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Categoria|Microsoft.Usage|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um método particular em um tipo sem lacre tem uma assinatura que é idêntica a um método público declarado em um tipo base. O método particular não é final.

## <a name="rule-description"></a>Descrição da regra

Não altere o modificador de acesso para membros herdados. A alteração de um membro herdado para particular não impede que os chamadores acessem a implementação da classe base do método. Se o membro for tornado privado e o tipo não for lacrado, a herança de tipos poderá chamar a última implementação pública do método na hierarquia de herança. Se você precisar alterar o modificador de acesso, o método deverá ser marcado como final ou seu tipo deve ser lacrado para impedir que o método seja substituído.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, altere o acesso para não privado. Como alternativa, se a linguagem de programação oferecer suporte a ela, você poderá tornar o método final.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um tipo que viola essa regra.

[!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
[!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]