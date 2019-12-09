---
title: 'CA2135: os assemblies de nível 2 não devem conter LinkDemands | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1248ac41a757ba2fc26ef0659c0f93ee325bc605
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602942"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: os assemblies de nível 2 não devem conter LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um membro de classe ou classe está usando um <xref:System.Security.Permissions.SecurityAction> em um aplicativo que está usando segurança de nível 2.

## <a name="rule-description"></a>Descrição da Regra
 LinkDemands são preteridos no conjunto de regras de segurança nível 2. Em vez de usar LinkDemands para impor a segurança em tempo de compilação JIT (just-in-time), marque os métodos, os tipos e os campos com o atributo <xref:System.Security.SecurityCriticalAttribute>.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova o <xref:System.Security.Permissions.SecurityAction> e marque o tipo ou o membro com o atributo <xref:System.Security.SecurityCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 No exemplo a seguir, o <xref:System.Security.Permissions.SecurityAction> deve ser removido e o método marcado com o atributo <xref:System.Security.SecurityCriticalAttribute>.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135.cs#1)]
