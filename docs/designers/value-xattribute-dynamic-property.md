---
title: Valor (propriedade dinâmica de XAttribute)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b97e33bdcb28a3c8790af752d5ab9786dc5ef3d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882887"
---
# <a name="value-xattribute-dynamic-property"></a>Valor (propriedade dinâmica de XAttribute)

Obtém ou define o valor de atributo XML.

## <a name="syntax"></a>Sintaxe

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor retornado

<xref:System.String> que contém o valor deste atributo.

## <a name="exceptions"></a>Exceções

|Tipo de exceção|Condição|
| - |---------------|
|<xref:System.ArgumentNullException>|Ao definir, `value` é `null`.|

## <a name="remarks"></a>Comentários

Esta propriedade é equivalente à propriedade de <xref:System.Xml.Linq.XAttribute.Value%2A> da classe de <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> , mas suporta essa propriedade dinâmica também alterar notificações.

## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Propriedades dinâmicas da classe XAttribute](../designers/xattribute-class-dynamic-properties.md)
- [Atributo](../designers/attribute-xelement-dynamic-property.md)