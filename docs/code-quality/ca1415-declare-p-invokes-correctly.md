---
title: 'CA1415: Declarar P-Invokes corretamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99274abee2c05a1bd33e34c9eb02cc928c1b54b0
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234621"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Declarar P/Invokes corretamente

|||
|-|-|
|NomeDoTipo|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Categoria|Microsoft. Interoperability|
|Alteração significativa|Não separável – se o P/Invoke que declara o parâmetro não puder ser visto fora do assembly. Quebra-se o P/Invoke que declara o parâmetro pode ser visto fora do assembly.|

## <a name="cause"></a>Causa
Um método de invocação de plataforma está declarado incorretamente.

## <a name="rule-description"></a>Descrição da regra
Um método de invocação de plataforma acessa código não gerenciado e é definido usando a `Declare` palavra- [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] chave no <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>ou no. Atualmente, essa regra procura declarações de método de invocação de plataforma que se destinam a funções Win32 que têm um ponteiro para um parâmetro de estrutura Sobreposto e o parâmetro <xref:System.Threading.NativeOverlapped?displayProperty=fullName> gerenciado correspondente não é um ponteiro para uma estrutura.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, declare corretamente o método Invoke da plataforma.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra os métodos de invocação de plataforma que violam a regra e satisfazem a regra.

[!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Consulte também
[Interoperação com código não gerenciado](/dotnet/framework/interop/index)