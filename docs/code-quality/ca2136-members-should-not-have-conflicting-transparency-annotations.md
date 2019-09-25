---
title: 'CA2136: Membros não devem ter anotações de transparência conflitantes'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f9455e83d7cb128a34696ae5e849fd0901f1891
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232215"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Membros não devem ter anotações de transparência conflitantes

|||
|-|-|
|NomeDoTipo|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Categoria|Microsoft.Security|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Essa regra é acionada quando um membro de tipo é <xref:System.Security> marcado com um atributo de segurança que tem uma transparência diferente do atributo de segurança de um contêiner do membro.

## <a name="rule-description"></a>Descrição da regra
Os atributos de transparência são aplicados com base nos elementos de código de escopo maior a elementos de escopo menor. Os atributos de transparência dos elementos de código com escopo maior têm precedência sobre atributos de transparência dos elementos de código contidos no primeiro elemento. Por exemplo, uma classe marcada com o <xref:System.Security.SecurityCriticalAttribute> atributo não pode conter um método marcado com o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir essa violação, remova o atributo de segurança do elemento de código que tem escopo inferior ou altere seu atributo para que seja o mesmo que o elemento de código que o contém.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprimir avisos desta regra.

## <a name="example"></a>Exemplo
No exemplo a seguir, um método é marcado com o <xref:System.Security.SecuritySafeCriticalAttribute> atributo e é um membro de uma classe que é marcada com o <xref:System.Security.SecurityCriticalAttribute> atributo. O atributo seguro de segurança deve ser removido.

[!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]