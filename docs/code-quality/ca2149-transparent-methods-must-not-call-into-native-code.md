---
title: 'CA2149: Métodos transparentes não devem chamar código nativo'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8e75b12b820b3ff3ac5a26f83148a49ca87c12ad
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231960"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: Métodos transparentes não devem chamar código nativo

|||
|-|-|
|NomeDoTipo|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Categoria|Microsoft.Security|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um método chama uma função nativa por meio de um stub de método, como P/Invoke.

## <a name="rule-description"></a>Descrição da regra
Essa regra é acionada em qualquer método transparente que chama diretamente em código nativo, por exemplo, por meio de um P/Invoke. As violações dessa regra levam a um <xref:System.MethodAccessException> no modelo de transparência de nível 2 e uma demanda completa para <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> o modelo de transparência de nível 1.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, marque o método que chama o código nativo com o <xref:System.Security.SecurityCriticalAttribute> atributo ou. <xref:System.Security.SecuritySafeCriticalAttribute>

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
[!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]