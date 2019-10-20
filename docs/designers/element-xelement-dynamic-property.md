---
title: Elemento (propriedade dinâmica de XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08b2f7f008c1522c5f65b5ee7a58c3ed98e8a845
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637335"
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
- [Propriedades dinâmicas da classe XElement](../designers/attribute-xelement-dynamic-property.md)
- [Elementos](../designers/elements-xelement-dynamic-property.md)