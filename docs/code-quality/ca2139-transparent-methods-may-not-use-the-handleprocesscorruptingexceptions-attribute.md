---
title: 'CA2139: Métodos transparentes podem não usar o atributo HandleProcessCorruptingExceptions'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6808c5e9b5d35ab6ec8d4012f08e15cba9a159d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920565"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Métodos transparentes podem não usar o atributo HandleProcessCorruptingExceptions

|||
|-|-|
|NomeDoTipo|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um método transparente é marcado com o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo.

## <a name="rule-description"></a>Descrição da regra
Essa regra dispara qualquer método que é transparente e tenta manipular um processo que corrompe a exceção usando o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo. Uma exceção de corrompimento de processo é uma classificação de exceção do CLR versão <xref:System.AccessViolationException>4,0 de exceções, como. O atributo HandleProcessCorruptedStateExceptionsAttribute só pode ser usado por métodos de segurança crítica e será ignorado se for aplicado a um método transparente. Para lidar com exceções que corrompem o processo, esse método deve se tornar crítico de segurança ou de segurança.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, remova o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo ou marque o método com o <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atributo ou.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
Neste exemplo, um método transparente é marcado com o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo e falhará na regra. O método também deve ser marcado com o <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atributo ou.

[!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]