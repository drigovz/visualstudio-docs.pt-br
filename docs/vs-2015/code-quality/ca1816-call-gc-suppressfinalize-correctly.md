---
title: 'CA1816: chamar GC. SuppressFinalize corretamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: acc86c278faa877897d294e72632762eff834a76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668394"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: chamar GC.SuppressFinalize corretamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Categoria|O. Uso|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa

- Um método que é uma implementação de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> não chama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Um método que não é uma implementação de chamadas de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Um método chama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> e passa algo diferente deste (eu em Visual Basic).

## <a name="rule-description"></a>Descrição da Regra
 O método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> permite que os usuários liberem recursos a qualquer momento antes que o objeto fique disponível para coleta de lixo. Se o método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> for chamado, ele liberará os recursos do objeto. Isso torna a finalização desnecessária. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> deve chamar <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para que o coletor de lixo não chame o finalizador do objeto.

 Para evitar que tipos derivados com finalizadores precisem reimplementar [System. IDisposable] (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) e chamá-lo, os tipos não lacrados sem os finalizadores ainda devem chamar <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra:

 Se o método for uma implementação de <xref:System.IDisposable.Dispose%2A>, adicione uma chamada para <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 Se o método não for uma implementação de <xref:System.IDisposable.Dispose%2A>, remova a chamada para <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> ou mova-a para a implementação de <xref:System.IDisposable.Dispose%2A> do tipo.

 Altere todas as chamadas para <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para passá-las (eu em Visual Basic).

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Apenas suprimir um aviso dessa regra se você estiver desliberando usando <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para controlar o tempo de vida de outros objetos. Não omita um aviso dessa regra se uma implementação de <xref:System.IDisposable.Dispose%2A> não chamar <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. Nessa situação, a falha ao suprimir a finalização degrada o desempenho e não fornece nenhum benefício.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método que chama incorretamente <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método que chama corretamente <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2215: métodos Dispose devem chamar o descarte da classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: os tipos descartáveis devem declarar o finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Consulte também
 [Padrão de descarte](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
