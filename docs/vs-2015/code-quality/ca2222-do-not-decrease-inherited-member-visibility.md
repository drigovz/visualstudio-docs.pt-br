---
title: 'CA2222: Não diminuir a visibilidade de membro herdado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ee6228359e84687023a713ee866ebfbb760b206b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58927480"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Não diminuir a visibilidade dos membros herdados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um método privado em um tipo não selado tem uma assinatura que é idêntica a um método público declarado em um tipo base. O método particular não é final.

## <a name="rule-description"></a>Descrição da Regra
 Você não deve alterar o modificador de acesso para membros herdados. A alteração de um membro herdado para particular não impede que os chamadores acessem a implementação da classe base do método. Se o membro é privado e o tipo é sem lacre, a herança de tipos pode chamar a implementação de pública último do método na hierarquia de herança. Se você precisar alterar o modificador de acesso, o método deve ser marcado como final ou seu tipo deve ser lacrado para impedir que o método que está sendo substituído.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere o acesso para ser não privado. Como alternativa, se sua linguagem de programação der suporte a ele, você pode tornar o método final.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola essa regra.

 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]
