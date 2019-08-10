---
title: 'CA2130: Constantes críticas de segurança devem ser transparentes'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a33b650570981f5496813f575b1ae2413a960026
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920769"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Constantes críticas de segurança devem ser transparentes

|||
|-|-|
|NomeDoTipo|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um campo constante ou um membro de enumeração é marcado com <xref:System.Security.SecurityCriticalAttribute>o.

## <a name="rule-description"></a>Descrição da regra
A imposição de transparência não é imposta para valores constantes porque compiladores têm valores constantes internos de modo que nenhuma pesquisa seja necessária no tempo de execução. Os campos constantes devem ter segurança transparente de forma que os revisores de código não pressuponham que o código transparente não pode acessar a constante.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, remova o atributo SecurityCritical do campo ou valor.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
Nos exemplos a seguir, o valor `EnumWithCriticalValues.CriticalEnumValue` de enumeração e a constante `CriticalConstant` geram esse aviso. Para corrigir os problemas, remova o atributo`SecurityCritical`[] para torná-los transparente para a segurança.

[!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]