---
title: 'CA2142: O código transparente não deve ser protegido com LinkDemands'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf5bb8320a8876582cc325ecf973c83593777193
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920503"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: O código transparente não deve ser protegido com LinkDemands

|||
|-|-|
|NomeDoTipo|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um método transparente requer uma <xref:System.Security.Permissions.SecurityAction> ou outras demandas de segurança.

## <a name="rule-description"></a>Descrição da regra
Essa regra é acionada em métodos transparentes que exigem LinkDemands para acessá-las. O código transparente de segurança não deve ser responsável por verificar a segurança de uma operação e, assim, não deve exigir permissões. Como os métodos transparentes devem ser neutros à segurança, eles não devem tomar decisões de segurança. Além disso, o código crítico seguro, que toma decisões de segurança, não deve depender do código Transparent para ter feito essa decisão anteriormente.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, remova a demanda de link no método transparente ou marque o método com <xref:System.Security.SecuritySafeCriticalAttribute> atributo se ele estiver executando verificações de segurança, como demandas de segurança.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
No exemplo a seguir, a regra é acionada no método porque o método é transparente e é marcado com um <xref:System.Security.PermissionSet> LinkDemand que contém <xref:System.Security.Permissions.SecurityAction>um.

[!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

Não suprima um aviso nessa regra.