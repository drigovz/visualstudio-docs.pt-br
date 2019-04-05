---
title: 'CA2138: Métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4e9a9e10f928efe6bcff6fb3d49c1b1cd7b1bd1c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58927795"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método de segurança transparente chama um método que é marcado com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra é acionada em qualquer método transparente chamado diretamente no código nativo, por exemplo, usando um por meio de um P/Invoke (invocação de plataforma) chamar. Métodos de interoperabilidade P/Invoke e COM que são marcados com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> resultam em um LinkDemand que está sendo feito em relação ao método de chamada do atributo. Porque o código transparente de segurança não é possível atender a LinkDemands, o código também não é possível chamar métodos que são marcados com o atributo SuppressUnmanagedCodeSecurity ou métodos da classe que é marcado com o atributo SuppressUnmanagedCodeSecurity. O método irá falhar ou a demanda será convertida em uma demanda completa.

 As violações dessa regra resultam em uma <xref:System.MethodAccessException> no modelo de transparência de segurança de nível 2 e uma demanda completa para <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> no modelo de transparência de nível 1.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova os <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> de atributos e marcar o método com o <xref:System.Security.SecurityCriticalAttribute> ou o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
