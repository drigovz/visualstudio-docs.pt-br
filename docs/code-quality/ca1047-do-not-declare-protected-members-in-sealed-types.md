---
title: 'CA1047: não declarar membros protegidos em tipos lacrados'
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
ms.openlocfilehash: b55da06cdaee07e0d5c30dc6c5220ef2d50f8d0b
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449108"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: não declarar membros protegidos em tipos lacrados

|||
|-|-|
|NomeDoTipo|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Categoria|Microsoft. Design|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um tipo público é `sealed` (`NotInheritable` no Visual Basic) e declara um membro protegido ou um tipo aninhado protegido. Essa regra não relata violações para os métodos <xref:System.Object.Finalize%2A>, que devem seguir esse padrão.

## <a name="rule-description"></a>Descrição da regra
Os tipos declaram membros protegidos de forma que a herança de tipos possa acessar ou substituir o membro. Por definição, você não pode herdar de um tipo lacrado, o que significa que métodos protegidos em tipos lacrados não podem ser chamados.

O C# compilador emite um aviso para esse erro.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, altere o nível de acesso do membro para privado ou torne o tipo herdável.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra. Deixar o tipo em seu estado atual pode causar problemas de manutenção e não fornece nenhum benefício.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo que viola essa regra.

[!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
[!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]
