---
title: 'CA1009: Declarar manipuladores de eventos corretamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e923730213ca31a4429d8547fdaaf980692f9a96
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236486"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Declarar manipuladores de eventos corretamente

|||
|-|-|
|NomeDoTipo|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Categoria|Microsoft.Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um delegado que manipula um evento público ou protegido não tem a assinatura, o tipo de retorno ou os nomes de parâmetro corretos.

## <a name="rule-description"></a>Descrição da regra
Os métodos de manipulador de eventos utilizam dois parâmetros. O primeiro é do tipo <xref:System.Object?displayProperty=fullName> e é chamado de ' Remetente '. Este é o objeto que acionou o evento. O segundo parâmetro é do tipo <xref:System.EventArgs?displayProperty=fullName> e é denominado ' e '. Esses são os dados associados ao evento. Por exemplo, se o evento for gerado sempre que um arquivo for aberto, os dados do evento normalmente conterá o nome do arquivo.

Os métodos do manipulador de eventos não devem retornar um valor. Na linguagem C# de programação, isso é indicado pelo tipo `void`de retorno. Um manipulador de eventos pode invocar vários métodos em vários objetos. Se os métodos tivessem permissão para retornar um valor, vários valores de retorno ocorreriam para cada evento, e somente o valor do último método que foi invocado estaria disponível.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, corrija a assinatura, o tipo de retorno ou os nomes de parâmetro do delegado. Para obter detalhes, consulte o exemplo a seguir.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um delegado que é adequado para manipular eventos. Os métodos que podem ser invocados por esse manipulador de eventos estão em conformidade com a assinatura especificada nas diretrizes de design. `AlarmEventHandler`é o nome do tipo do delegado. `AlarmEventArgs`deriva da classe base para dados de evento, <xref:System.EventArgs>e mantém dados de evento de alarme.

[!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
[!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
[!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
[CA2109: Examinar os manipuladores de eventos visíveis](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Consulte também

- <xref:System.EventArgs?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
- [Manipulando e gerando eventos](/dotnet/standard/events/index)