---
title: 'CA2220: Os finalizadores devem chamar o finalizador da classe base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 432d973a64c7ee7f4264841e2a1277f66c9259da
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922374"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Os finalizadores devem chamar o finalizador de classe base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um tipo que substitui <xref:System.Object.Finalize%2A?displayProperty=fullName> não chama o <xref:System.Object.Finalize%2A> método na sua classe base.

## <a name="rule-description"></a>Descrição da Regra
 A finalização deve ser propagada em toda a hierarquia de herança. Para garantir isso, os tipos devem chamar sua classe base <xref:System.Object.Finalize%2A> método de dentro de seus próprios <xref:System.Object.Finalize%2A> método. O compilador C# adiciona a chamada para o finalizador da classe base automaticamente.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, chame o tipo base <xref:System.Object.Finalize%2A> método de sua <xref:System.Object.Finalize%2A> método.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Alguns compiladores que direcionam o common language runtime inserir uma chamada para o finalizador do tipo base em Microsoft intermediate language (MSIL). Se um aviso nessa regra for relatado, o compilador não insere a chamada e você deve adicioná-lo ao seu código.

## <a name="example"></a>Exemplo
 O exemplo de Visual Basic a seguir mostra um tipo `TypeB` que chama corretamente o <xref:System.Object.Finalize%2A> método na sua classe base.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Consulte também
 [Padrão de descarte](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
