---
title: 'CA1414: marcar argumentos boolianos P-Invoke com MarshalAs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 588e16a6b21b320ad7012bd20d79a62d027679e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652685"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: marcar argumentos P/Invoke boolianos com MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Categoria|Microsoft. Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma declaração de método de invocação de plataforma inclui um parâmetro <xref:System.Boolean?displayProperty=fullName> ou valor de retorno, mas o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> não é aplicado ao parâmetro ou valor de retorno.

## <a name="rule-description"></a>Descrição da Regra
 Um método de invocação de plataforma acessa código não gerenciado e é definido usando a palavra-chave `Declare` no [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ou no <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> especifica o comportamento de marshaling que é usado para converter tipos de dados entre códigos gerenciados e não gerenciados. Muitos tipos de dados simples, como <xref:System.Byte?displayProperty=fullName> e <xref:System.Int32?displayProperty=fullName>, têm uma única representação em código não gerenciado e não exigem especificação de seu comportamento de marshaling; o Common Language Runtime fornece automaticamente o comportamento correto.

 O tipo de dados <xref:System.Boolean> tem várias representações em código não gerenciado. Quando o <xref:System.Runtime.InteropServices.MarshalAsAttribute> não é especificado, o comportamento de marshaling padrão para o tipo de dados <xref:System.Boolean> é <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Esse é um inteiro de 32 bits, que não é apropriado em todas as circunstâncias. A representação booliana exigida pelo método não gerenciado deve ser determinada e corresponder ao <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> apropriado. UnmanagedType. Bool é o tipo BOOL do Win32, que é sempre 4 bytes. UnmanagedType. U1 deve ser usado para C++ `bool` ou outros tipos de 1 byte. Para obter mais informações, consulte [marshaling padrão para tipos Boolean](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, aplique <xref:System.Runtime.InteropServices.MarshalAsAttribute> ao parâmetro <xref:System.Boolean> ou ao valor de retorno. Defina o valor do atributo para o <xref:System.Runtime.InteropServices.UnmanagedType> apropriado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Mesmo que o comportamento de marshaling padrão seja apropriado, o código será mantido mais facilmente quando o comportamento for especificado explicitamente.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra dois métodos de invocação de plataforma que são marcados com os atributos de <xref:System.Runtime.InteropServices.MarshalAsAttribute> apropriados.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1901: as declarações P/Invoke devem ser portáteis](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: especificar marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> o [marshaling padrão para tipos Boolean](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [interoperar com código não gerenciado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
