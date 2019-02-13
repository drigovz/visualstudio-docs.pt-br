---
title: Atributo (propriedade dinâmica de XElement)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ec27fe2d7824ca32cbf97dbabac8b7ea6c4aed6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948492"
---
# <a name="attribute-xelement-dynamic-property"></a>Atributo (propriedade dinâmica de XElement)

Obtém um indexador usado para recuperar a instância do atributo que corresponde ao nome especificado expandido.

## <a name="syntax"></a>Sintaxe

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno

Um indicador de tipo `XAttribute Item(String expandedName)`. Esse marcador utiliza o nome do atributo especificado e retorna <xref:System.Xml.Linq.XAttribute>correspondente, ou `null` se não houver nenhum atributo com o nome especificado.

## <a name="remarks"></a>Comentários

Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XElement.Attribute%2A> da classe de <xref:System.Xml.Linq.XElement?displayProperty=fullName> .

## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Propriedades dinâmicas da classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Valor](../designers/value-xattribute-dynamic-property.md)