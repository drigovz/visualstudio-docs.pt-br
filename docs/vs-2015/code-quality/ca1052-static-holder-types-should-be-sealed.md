---
title: 'CA1052: Tipos de suporte estático devem ser lacrados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 165ad365ea094a9f0b5771490e14e889160f3f96
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924607"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Tipos de suporte estático devem ser selados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público ou protegido contém apenas membros estáticos e não é declarado com o [lacrado](http://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](http://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)) modificador.

## <a name="rule-description"></a>Descrição da Regra
 Esta regra pressupõe que um tipo que contém apenas membros estáticos não foi projetado para ser herdadas, pois o tipo não fornece nenhuma funcionalidade que pode ser substituída em um tipo derivado. Um tipo que não se destina a ser herdada que deve ser marcado com o `sealed` modificador para proibir o uso como um tipo base.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, marque o tipo como `sealed`. Se você estiver direcionando [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 ou anterior, uma abordagem melhor é marcar o tipo como `static`. Dessa forma, você não precisa declarar um construtor particular para impedir que a classe que está sendo criado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprima um aviso nessa regra somente se o tipo foi projetado para ser herdada. A ausência do `sealed` modificador sugere que o tipo é útil como um tipo base.

## <a name="example-of-a-violation"></a>Exemplo de uma violação

### <a name="description"></a>Descrição
 O exemplo a seguir mostra um tipo que viola a regra.

### <a name="code"></a>Código
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Corrigir com o modificador estático

### <a name="description"></a>Descrição
 O exemplo a seguir mostra como corrigir uma violação dessa regra, marcando o tipo com o `static` modificador.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1053: Tipos de espaços reservados estáticos não devem ter construtores](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
