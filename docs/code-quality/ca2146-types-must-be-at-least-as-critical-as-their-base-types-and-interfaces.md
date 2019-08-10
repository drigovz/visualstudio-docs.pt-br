---
title: 'CA2146: Os tipos devem ser pelo menos tão críticos quanto seus tipos base e interfaces'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a70e999505bd900a7b3d89693ef4f6a1cef9de7d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920419"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Os tipos devem ser pelo menos tão críticos quanto seus tipos base e interfaces

|||
|-|-|
|NomeDoTipo|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo transparente é derivado de um tipo que é marcado com o <xref:System.Security.SecuritySafeCriticalAttribute> ou o <xref:System.Security.SecurityCriticalAttribute>, ou um tipo marcado com o <xref:System.Security.SecuritySafeCriticalAttribute> atributo é derivado de um tipo que é marcado com o <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="rule-description"></a>Descrição da regra
Esta regra é acionada quando um tipo derivado tem um atributo de transparência de segurança que não é tão crítico quanto seu tipo de base ou interface implementada. Apenas os tipos críticos podem derivar os tipos de base críticos ou implementar interfaces críticos, e apenas os tipos críticos ou de segurança crítica podem derivar dos tipos de base críticos de segurança ou implementar interfaces críticas de segurança. As violações dessa regra na transparência de nível 2 resultam <xref:System.TypeLoadException> em um para o tipo derivado.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir essa violação, marque o tipo derivado ou de implementação com um atributo de transparência que seja pelo menos tão crítico quanto o tipo base ou a interface.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
[!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]