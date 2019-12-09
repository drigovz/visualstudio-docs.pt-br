---
title: 'CA2215: os métodos Dispose devem chamar a classe base Dispose | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 89f3705169fb9d28a1ec773671d460f00b98d892
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662862"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: os métodos de descarte devem chamar o descarte da classe base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo que implementa <xref:System.IDisposable?displayProperty=fullName> é herdado de um tipo que também implementa <xref:System.IDisposable>. O método de <xref:System.IDisposable.Dispose%2A> do tipo herdado não chama o método <xref:System.IDisposable.Dispose%2A> do tipo pai.

## <a name="rule-description"></a>Descrição da Regra
 Se um tipo for herdado de um tipo descartável, ele deverá chamar o método <xref:System.IDisposable.Dispose%2A> do tipo base de dentro de seu próprio método <xref:System.IDisposable.Dispose%2A>. Chamar o método de tipo base Dispose garante que todos os recursos criados pelo tipo base sejam liberados.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, chame `base`. <xref:System.IDisposable.Dispose%2A> em seu método de <xref:System.IDisposable.Dispose%2A>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se a chamada para `base`. <xref:System.IDisposable.Dispose%2A> ocorre em um nível de chamada mais profundo do que as verificações de regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `TypeA` que implementa <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `TypeB` que herda do tipo `TypeA` e chama corretamente seu método <xref:System.IDisposable.Dispose%2A>.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Consulte também
 [padrão de descarte](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb) de <xref:System.IDisposable?displayProperty=fullName>
