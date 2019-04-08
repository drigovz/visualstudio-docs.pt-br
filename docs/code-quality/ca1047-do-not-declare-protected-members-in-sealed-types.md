---
title: 'CA1047: Não declarar membros protegidos em tipos selados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c138c05d755b05275755f96776764604997cbbcd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921543"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Não declarar membros protegidos em tipos selados

|||
|-|-|
|NomeDoTipo|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 É um tipo público `sealed` (`NotInheritable` no Visual Basic) e declara um membro protegido ou um tipo aninhado protegido. Essa regra não relata violações para <xref:System.Object.Finalize%2A> métodos, que devem seguir esse padrão.

## <a name="rule-description"></a>Descrição da regra
 Os tipos declaram membros protegidos de forma que a herança de tipos possa acessar ou substituir o membro. Por definição, você não pode herdar de um tipo selado, o que significa que métodos em tipos lacrados protegidos não pode ser chamada.

 O compilador C# emite um aviso para esse erro.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, altere o nível de acesso do membro particular ou tornar o tipo herdável.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra. Deixar o tipo em seu estado atual pode causar problemas de manutenção e não oferece nenhum benefício.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola essa regra.

 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]