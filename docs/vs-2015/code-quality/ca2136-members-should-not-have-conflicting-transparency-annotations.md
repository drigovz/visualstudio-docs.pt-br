---
title: 'CA2136: os membros não devem ter anotações de transparência conflitantes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f2fbb856ff53552ab99dabd4f650e9fd7f62a088
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602977"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: os membros não devem ter anotações de transparência conflitantes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Essa regra é acionada quando um membro de tipo é marcado com um atributo de segurança <xref:System.Security> que tem uma transparência diferente do atributo de segurança de um contêiner do membro.

## <a name="rule-description"></a>Descrição da Regra
 Os atributos de transparência são aplicados com base nos elementos de código de escopo maior a elementos de escopo menor. Os atributos de transparência dos elementos de código com escopo maior têm precedência sobre atributos de transparência dos elementos de código contidos no primeiro elemento. Por exemplo, uma classe marcada com o atributo <xref:System.Security.SecurityCriticalAttribute> não pode conter um método marcado com o atributo <xref:System.Security.SecuritySafeCriticalAttribute>.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir essa violação, remova o atributo de segurança do elemento de código que tem escopo inferior ou altere seu atributo para que seja o mesmo que o elemento de código que o contém.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprimir avisos desta regra.

## <a name="example"></a>Exemplo
 No exemplo a seguir, um método é marcado com o atributo <xref:System.Security.SecuritySafeCriticalAttribute> e ele é um membro de uma classe que é marcada com o atributo <xref:System.Security.SecurityCriticalAttribute>. O atributo seguro de segurança deve ser removido.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
