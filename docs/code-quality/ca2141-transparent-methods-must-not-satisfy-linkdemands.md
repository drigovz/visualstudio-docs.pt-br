---
title: CA2141:Transparent métodos não devem atender a LinkDemands
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0365d82917b8cfbaf291d557a6ac2d95c220562a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232127"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141:Transparent métodos não devem atender a LinkDemands

|||
|-|-|
|NomeDoTipo|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Categoria|Microsoft.Security|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um método transparente de segurança chama um método em um assembly que não está marcado com <xref:System.Security.AllowPartiallyTrustedCallersAttribute> o atributo (APTCA), ou um método transparente de segurança satisfaz <xref:System.Security.Permissions.SecurityAction> um `.LinkDemand` para um tipo ou um método.

## <a name="rule-description"></a>Descrição da regra
Satisfazer um LinkDemand é uma operação sensível à segurança que pode causar a elevação não intencional de privilégio. O código Transparent de segurança não deve satisfazer LinkDemands, pois não está sujeito aos mesmos requisitos de auditoria de segurança que o código crítico de segurança. Os métodos Transparent nos assemblies de nível 1 do conjunto de regras de segurança farão com que todas as LinkDemands que eles satisfazem sejam convertidas para solicitações completas em tempo de execução, o que pode causar problemas de desempenho Nos assemblies de nível 2 do conjunto de regras de segurança, os métodos transparentes não serão compilados no compilador JIT (just-in-time) se tentarem atender a um LinkDemand.

Em assemblies que usam segurança de nível 2, tentativas por um método transparente de segurança para satisfazer um LinkDemand ou chamar um método em um assembly não APTCA gera <xref:System.MethodAccessException>um; em assemblies de nível 1, LinkDemand torna-se uma demanda completa.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, marque o método de acesso com o <xref:System.Security.SecurityCriticalAttribute> atributo <xref:System.Security.SecuritySafeCriticalAttribute> ou ou remova LinkDemand do método acessado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
Neste exemplo, um método transparente tenta chamar um método que tem um LinkDemand. Esta regra será acionada neste código.

[!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]