---
title: 'CA2143: Métodos transparentes não devem usar demandas de segurança'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a182beba738e583fad83c3f51d7efa312761906d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231979"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Métodos transparentes não devem usar demandas de segurança

|||
|-|-|
|NomeDoTipo|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Categoria|Microsoft.Security|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo ou método de transparente é marcado declarativamente com <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> uma `.Demand` demanda ou o método chama <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> o método.

## <a name="rule-description"></a>Descrição da regra
O código transparente de segurança não deve ser responsável por verificar a segurança de uma operação e, assim, não deve exigir permissões. O código transparente de segurança deve usar demandas completas para tomar decisões de segurança e o código crítico de segurança não deve confiar no código transparente para fazer a demanda completa. Qualquer código que executa verificações de segurança, como demandas de segurança, deve ser crítico para segurança.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Em geral, para corrigir uma violação dessa regra, marque o método com o <xref:System.Security.SecuritySafeCriticalAttribute> atributo. Você também pode remover a demanda.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
Os arquivos de regra no código a seguir porque um método transparente faz uma demanda de segurança declarativa.

[!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>Consulte também
[CA2142: O código transparent não deve ser protegido com LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)