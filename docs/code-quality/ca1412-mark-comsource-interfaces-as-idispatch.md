---
title: 'CA1412: marcar interfaces ComSource como IDispatch'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 227cc5c47a2001cd6c3b71718ae2a29032bed71c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444204"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: marcar interfaces ComSource como IDispatch

|||
|-|-|
|NomeDoTipo|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Categoria|Microsoft. Interoperability|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo é marcado com o atributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> e pelo menos uma interface especificada não é marcada com o atributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> definido como o valor `InterfaceIsDispatch`.

## <a name="rule-description"></a>Descrição da regra

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> é usado para identificar as interfaces de evento que uma classe expõe para clientes Component Object Model (COM). Essas interfaces devem ser expostas como `InterfaceIsIDispatch` para permitir que Visual Basic COM clientes COM 6 recebam notificações de eventos. Por padrão, se uma interface não estiver marcada com o atributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, ela será exposta como uma interface dupla.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, adicione ou modifique o atributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> para que seu valor seja definido como InterfaceIsIDispatch para todas as interfaces especificadas com o atributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra uma classe em que uma das interfaces viola a regra.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Regras relacionadas

[CA1408: não usar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Consulte também

- [Interoperação com código não gerenciado](/dotnet/framework/interop/index)
