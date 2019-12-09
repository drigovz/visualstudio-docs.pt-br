---
title: 'CA1404: chamar GetLastError imediatamente após P-Invoke | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2664837c17894f7ca336d650a7e08e21c45d955f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661318"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: chamar GetLastError logo depois de P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Categoria|Microsoft. Interoperability|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 É feita uma chamada para o método <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> ou a função equivalente do Win32 `GetLastError`, e a chamada que vem imediatamente antes não é para um método de invocação de plataforma.

## <a name="rule-description"></a>Descrição da Regra
 Um método de invocação de plataforma acessa código não gerenciado e é definido usando a palavra-chave `Declare` em [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ou no atributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Geralmente, após a falha, as funções não gerenciadas chamam a função Win32 `SetLastError` para definir um código de erro associado à falha. O chamador da função com falha chama a função Win32 `GetLastError` para recuperar o código de erro e determinar a causa da falha. O código de erro é mantido por thread e é substituído pela próxima chamada para `SetLastError`. Depois de uma chamada para um método de invocação de plataforma com falha, o código gerenciado pode recuperar o código de erro chamando o método <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Como o código de erro pode ser substituído por chamadas internas de outros métodos de biblioteca de classes gerenciadas, o método `GetLastError` ou <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> deve ser chamado imediatamente após a chamada de método de invocação de plataforma.

 A regra ignora chamadas para os seguintes membros gerenciados quando eles ocorrem entre a chamada para o método de invocação de plataforma e a chamada para <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Esses membros não alteram o código de erro e são úteis para determinar o sucesso de algumas chamadas de método de invocação de plataforma.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, mova a chamada para <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> para que ela imediatamente siga a chamada para o método de invocação de plataforma.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se o código entre a chamada de método de invocação de plataforma e a chamada do método <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> não puder explicitamente ou implicitamente causar a alteração do código de erro.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método que viola a regra e um método que satisfaz a regra.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1060: mover P/Invokes para a classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: os pontos de entrada de P-Invoke devem existir](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: os P/Invokes não devem estar visíveis](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: especificar marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: usar equivalentes gerenciados da API do Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
