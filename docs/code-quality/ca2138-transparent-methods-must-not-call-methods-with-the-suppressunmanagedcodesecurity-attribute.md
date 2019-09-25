---
title: 'CA2138: Métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d88b2f5c15d51ff840cc6ff116396ffd6b5efd60
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232204"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity

|||
|-|-|
|NomeDoTipo|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Categoria|Microsoft.Security|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um método transparente de segurança chama um método que é marcado com <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> o atributo.

## <a name="rule-description"></a>Descrição da regra
Essa regra é acionada em qualquer método transparente que chama diretamente em código nativo, por exemplo, usando uma chamada P/Invoke (invocação de plataforma). Os métodos de interoperabilidade P/Invoke e com que <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> são marcados com o atributo resultam em um LinkDemand sendo feito em relação ao método de chamada. Como o código Transparent Security não pode satisfazer LinkDemands, o código também não pode chamar métodos que são marcados com o atributo SuppressUnmanagedCodeSecurity ou métodos de classe que são marcados com o atributo SuppressUnmanagedCodeSecurity. O método falhará ou a demanda será convertida em uma demanda completa.

As violações dessa regra levam a um <xref:System.MethodAccessException> no modelo de transparência de segurança de nível 2 e uma demanda completa <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> pelo modelo de transparência de nível 1.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, remova o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo e marque o método com o <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atributo ou.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
[!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]