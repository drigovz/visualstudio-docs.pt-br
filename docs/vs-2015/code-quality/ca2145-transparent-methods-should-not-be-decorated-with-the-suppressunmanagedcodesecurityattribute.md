---
title: 'CA2145: métodos transparentes não devem ser decorados com SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6bffa680fa39014ffa96feec997b5eca63ee08ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610217"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: os métodos transparentes não devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método transparente, um método que é marcado com o método <xref:System.Security.SecuritySafeCriticalAttribute> ou um tipo que contém um método é marcado com o atributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.

## <a name="rule-description"></a>Descrição da Regra
 Os métodos decorados com o atributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> têm um LinkDemand implícito colocado sobre qualquer método que o chame. Este LinkDemand requer que o código de chamada seja crítico de segurança. Marcar o método que usa SuppressUnmanagedCodeSecurity com o atributo <xref:System.Security.SecurityCriticalAttribute> torna esse requisito mais óbvio para os chamadores do método.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, marque o método ou o tipo com o atributo <xref:System.Security.SecurityCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Comentários
