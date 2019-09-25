---
title: 'CA2220: Os finalizadores devem chamar o finalizador de classe base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5af6b7872f0fa05183334e6acd2bc4922f84990
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231169"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Os finalizadores devem chamar o finalizador de classe base

|||
|-|-|
|NomeDoTipo|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Categoria|Microsoft.Usage|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um tipo que substitui <xref:System.Object.Finalize%2A?displayProperty=fullName> não chama o <xref:System.Object.Finalize%2A> método em sua classe base.

## <a name="rule-description"></a>Descrição da regra

A finalização deve ser propagada em toda a hierarquia de herança. Para garantir isso, os tipos devem chamar seu método <xref:System.Object.Finalize%2A> de classe base de dentro <xref:System.Object.Finalize%2A> de seu próprio método. O C# compilador adiciona automaticamente a chamada ao finalizador de classe base.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, chame o método do <xref:System.Object.Finalize%2A> tipo base do seu <xref:System.Object.Finalize%2A> método.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. Alguns compiladores que se destinam ao Common Language Runtime inserir uma chamada para o finalizador do tipo base na MSIL (Microsoft Intermediate Language). Se um aviso dessa regra for relatado, o compilador não inserirá a chamada e você deverá adicioná-la ao seu código.

## <a name="example"></a>Exemplo

O exemplo a seguir Visual Basic mostra um `TypeB` tipo que chama corretamente <xref:System.Object.Finalize%2A> o método em sua classe base.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Consulte também

- [Padrão de descarte](/dotnet/standard/design-guidelines/dispose-pattern)