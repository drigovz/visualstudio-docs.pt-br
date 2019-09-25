---
title: 'CA1404: Chamar GetLastError imediatamente após P-Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ab789e578dd8603f604cdb00aa5d236250d13670
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235050"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Chamar GetLastError imediatamente após P/Invoke

|||
|-|-|
|NomeDoTipo|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Categoria|Microsoft. Interoperability|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

É feita uma chamada ao <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> método ou à função Win32 `GetLastError` equivalente, e a chamada que vem imediatamente antes não é para um método de invocação de plataforma.

## <a name="rule-description"></a>Descrição da regra
Um método de invocação de plataforma acessa código não gerenciado e é definido usando a `Declare` palavra- [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] chave in <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> ou o atributo. Geralmente, após a falha, as funções não gerenciadas chamam `SetLastError` a função do Win32 para definir um código de erro associado à falha. O chamador da função com falha chama a função `GetLastError` do Win32 para recuperar o código de erro e determinar a causa da falha. O código de erro é mantido por thread e é substituído pela próxima chamada para `SetLastError`. Depois de uma chamada para um método de invocação de plataforma com falha, o código gerenciado pode recuperar <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> o código de erro chamando o método. Como o código de erro pode ser substituído por chamadas internas de outros métodos de biblioteca de classes gerenciadas <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> , o `GetLastError` método ou deve ser chamado imediatamente após a chamada de método de invocação de plataforma.

A regra ignora chamadas para os seguintes membros gerenciados quando eles ocorrem entre a chamada para o método de invocação de plataforma e <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>a chamada para. Esses membros não alteram o código de erro e são úteis para determinar o sucesso de algumas chamadas de método de invocação de plataforma.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, mova a chamada para <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> para que ela imediatamente siga a chamada para o método de invocação de plataforma.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra se o código entre a chamada de método da plataforma Invoke e a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> chamada do método não puder explicitamente ou implicitamente fazer com que o código de erro seja alterado.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um método que viola a regra e um método que satisfaz a regra.

[!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
[!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA1060: Mover P/Invokes para a classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

[CA1400: Os pontos de entrada P/Invoke devem existir](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

[CA1401: P/Invokes não devem ser visíveis](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

[CA2101: Especificar o marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

[CA2205: Usar equivalentes gerenciados da API do Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)