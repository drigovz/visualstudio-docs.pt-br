---
title: XML (propriedade dinâmica de XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d58dea02a45ccc84e7829da2acdb479eb17dda3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931241"
---
# <a name="xml-xelement-dynamic-property"></a>XML (propriedade dinâmica de XElement)

Obtém o conteúdo sem formatação XML do elemento.

## <a name="syntax"></a>Sintaxe

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor retornado

<xref:System.String> que representa o conteúdo sem formatação XML do elemento.

## <a name="remarks"></a>Comentários

Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> da classe de <xref:System.Xml.Linq.XNode?displayProperty=fullName> , com o parâmetro de `SaveOptions` definido como <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Consulte também

- [Propriedades dinâmicas da classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Valor](../designers/value-xelement-dynamic-property.md)