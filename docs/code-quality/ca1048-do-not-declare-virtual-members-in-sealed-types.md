---
title: 'CA1048: Não declarar membros virtuais em tipos selados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 531590eee7804debfc8ccfb9a8e508107fba71df
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006718"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Não declarar membros virtuais em tipos selados

|||
|-|-|
|NomeDoTipo|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público é selado e declara um método que se deve tanto `virtual` (`Overridable` no Visual Basic) e não final. Essa regra não relata violações para tipos de delegado, que devem seguir esse padrão.

## <a name="rule-description"></a>Descrição da regra
 Os tipos declaram métodos como virtuais de forma que a herança de tipos possa substituir a implementação do método virtual. Por definição, você não pode herdar de um tipo selado, tornando um método virtual em um tipo lacrado sem sentido.

 Os compiladores do Visual Basic e c# não permitem tipos violar essa regra.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, tornar o método não virtual ou tornar o tipo herdável.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra. Deixar o tipo em seu estado atual pode causar problemas de manutenção e não oferece nenhum benefício.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola essa regra.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]