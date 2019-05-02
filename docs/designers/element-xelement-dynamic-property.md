---
title: Elemento (propriedade dinâmica de XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbd197082174bcd23ab6b47d64eb4eb0f7944ca2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62845536"
---
# <a name="element-xelement-dynamic-property"></a>Elemento (propriedade dinâmica de XElement)

Obtém um indexador usado para recuperar a instância do elemento filho que corresponde ao nome especificado expandido.

## <a name="syntax"></a>Sintaxe

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno

Um indicador de tipo `XElement Item(String expandedName)`. Esse marcador aceita um parâmetro expandido de nome e retorna <xref:System.Xml.Linq.XElement>correspondente, ou `null` se não houver nenhum elemento com o nome especificado.

## <a name="remarks"></a>Comentários

Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Element%2A> da classe de <xref:System.Xml.Linq.XContainer?displayProperty=fullName> .

## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Propriedades dinâmicas da classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Elementos](../designers/elements-xelement-dynamic-property.md)