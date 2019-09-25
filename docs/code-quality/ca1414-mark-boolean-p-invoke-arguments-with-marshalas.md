---
title: 'CA1414: Marcar argumentos P-Invoke boolianos com MarshalAs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 22e62a1e3209399be4b10a3ec28db4afdd6f0f20
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234668"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Marcar argumentos P/Invoke boolianos com MarshalAs

|||
|-|-|
|NomeDoTipo|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Categoria|Microsoft. Interoperability|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Uma declaração de método de invocação <xref:System.Boolean?displayProperty=fullName> de plataforma inclui um parâmetro ou <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> valor de retorno, mas o atributo não é aplicado ao parâmetro ou valor de retorno.

## <a name="rule-description"></a>Descrição da regra
Um método de invocação de plataforma acessa código não gerenciado e é definido usando a `Declare` palavra- [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] chave no <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>ou no. <xref:System.Runtime.InteropServices.MarshalAsAttribute>Especifica o comportamento de marshaling que é usado para converter tipos de dados entre código gerenciado e não gerenciado. Muitos tipos de dados simples, <xref:System.Byte?displayProperty=fullName> como e <xref:System.Int32?displayProperty=fullName>, têm uma única representação em código não gerenciado e não exigem especificação de seu comportamento de marshaling; o Common Language Runtime fornece automaticamente o comportamento correto.

O <xref:System.Boolean> tipo de dados tem várias representações em código não gerenciado. Quando o <xref:System.Runtime.InteropServices.MarshalAsAttribute> não é especificado, o comportamento de marshaling padrão para <xref:System.Boolean> o tipo de <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>dados é. Esse é um inteiro de 32 bits, que não é apropriado em todas as circunstâncias. A representação booliana exigida pelo método não gerenciado deve ser determinada e corresponder ao apropriado <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. Bool é o tipo BOOL do Win32, que é sempre 4 bytes. UnmanagedType. U1 deve ser usado para C++ `bool` ou outros tipos de 1 byte.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, aplique <xref:System.Runtime.InteropServices.MarshalAsAttribute> ao parâmetro ou ao valor de <xref:System.Boolean> retorno. Defina o valor do atributo como o apropriado <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra. Mesmo que o comportamento de marshaling padrão seja apropriado, o código será mantido mais facilmente quando o comportamento for especificado explicitamente.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra os métodos de invocação de plataforma que <xref:System.Runtime.InteropServices.MarshalAsAttribute> são marcados com os atributos apropriados.

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Regras relacionadas
[CA1901: As declarações P/Invoke devem ser portáteis](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

[CA2101: Especificar o marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Interoperação com código não gerenciado](/dotnet/framework/interop/index)