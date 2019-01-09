---
title: Elementos (propriedade dinâmica de XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 01bca0771fb02ab8442132eaff4759fe7277ad6f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837047"
---
# <a name="elements-xelement-dynamic-property"></a>Elementos (propriedade dinâmica de XElement)

Obtém um indexador usado para recuperar elementos filho do elemento atual que corresponde ao nome especificado expandido.

## <a name="syntax"></a>Sintaxe

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno

Um indicador de tipo `IEnumerable<XElement> Item(String expandedName)`. Esse marcador utiliza o nome expandido de elementos filhos desejados e retorna os elementos filho correspondentes em uma coleção de <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` .

## <a name="remarks"></a>Comentários

Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> da classe de <xref:System.Xml.Linq.XContainer> .

Os elementos na coleção retornada estão na ordem de documento-fonte XML.

Esta propriedade usa a execução adiada.

## <a name="see-also"></a>Consulte também

- [Propriedades dinâmicas da classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Elemento](../designers/element-xelement-dynamic-property.md)
- [Descendentes](../designers/descendants-xelement-dynamic-property.md)