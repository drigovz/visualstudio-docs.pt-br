---
title: 'CA1049: tipos que possuem recursos nativos devem ser descartáveis | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aaaf95346c51e2cb5cadb01a39e482bb508bc764
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668900"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: tipos que tenham recursos nativos devem ser descartáveis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Categoria|Microsoft. Design|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo faz referência a um campo <xref:System.IntPtr?displayProperty=fullName>, um campo <xref:System.UIntPtr?displayProperty=fullName> ou um campo <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, mas não implementa <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra pressupõe que os campos <xref:System.IntPtr>, <xref:System.UIntPtr> e <xref:System.Runtime.InteropServices.HandleRef> armazenem ponteiros para recursos não gerenciados. Os tipos que alocam recursos não gerenciados devem implementar <xref:System.IDisposable> para permitir que os chamadores liberem esses recursos sob demanda e reduzam os tempos de vida dos objetos que contêm os recursos.

 O padrão de design recomendado para limpar recursos não gerenciados é fornecer um meio implícito e explícito para liberar esses recursos usando o método <xref:System.Object.Finalize%2A?displayProperty=fullName> e o método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, respectivamente. O coletor de lixo chama o método <xref:System.Object.Finalize%2A> de um objeto em algum momento indeterminado depois que o objeto não é mais acessível. Depois que <xref:System.Object.Finalize%2A> é chamado, uma coleta de lixo adicional é necessária para liberar o objeto. O método <xref:System.IDisposable.Dispose%2A> permite que o chamador libere explicitamente os recursos sob demanda, antes dos recursos que seriam liberados se deixassem para o coletor de lixo. Depois de limpar os recursos não gerenciados, <xref:System.IDisposable.Dispose%2A> deve chamar o método <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para permitir que o coletor de lixo saiba que <xref:System.Object.Finalize%2A> não precisa mais ser chamado; Isso elimina a necessidade de coleta de lixo adicional e reduz o tempo de vida do objeto.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, implemente <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se o tipo não fizer referência a um recurso não gerenciado. Caso contrário, não omita um aviso dessa regra porque a falha na implementação de <xref:System.IDisposable> pode fazer com que os recursos não gerenciados se tornem indisponíveis ou subutilizados.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que implementa <xref:System.IDisposable> para limpar um recurso não gerenciado.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2115: chamar GC.KeepAlive durante o uso de recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: chamar GC.SuppressFinalize corretamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: os tipos descartáveis devem declarar o finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: tipos que têm campos descartáveis devem ser descartáveis](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Consulte também
  [Padrão de descarte](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
