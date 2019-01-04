---
title: 'CA2145: Métodos transparentes não devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c3d2fe5c2c4e75376f88af7679f6838561848c2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949346"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Métodos transparentes não devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute

|||
|-|-|
|NomeDoTipo|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Um método transparente, um método marcado com o <xref:System.Security.SecuritySafeCriticalAttribute> método ou um tipo que contém um método é marcado com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.

## <a name="rule-description"></a>Descrição da regra

Os métodos decorados com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo têm um LinkDemand implícito colocado em qualquer método que o chama. Este LinkDemand requer que o código de chamada seja crítico de segurança. A marcação do método que usa SuppressUnmanagedCodeSecurity com o <xref:System.Security.SecurityCriticalAttribute> atributo torna esse requisito mais óbvio para chamadores do método.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, marque o método ou tipo com o <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

### <a name="code"></a>Código

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]