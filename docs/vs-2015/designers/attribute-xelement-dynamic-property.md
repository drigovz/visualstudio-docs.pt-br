---
title: Atributo (Propriedade Dinâmica XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 551e072b05e7a88ff9624c5d16e4aa199a6afd66
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657977"
---
# <a name="attribute-xelement-dynamic-property"></a>Atributo (propriedade dinâmica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtém um indexador usado para recuperar a instância do atributo que corresponde ao nome especificado expandido.

## <a name="syntax"></a>Sintaxe

```
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno
 Um indicador de tipo `XAttribute Item(String expandedName)`. Esse marcador utiliza o nome do atributo especificado e retorna <xref:System.Xml.Linq.XAttribute>correspondente, ou `null` se não houver nenhum atributo com o nome especificado.

## <a name="remarks"></a>Comentários
 Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XElement.Attribute%2A> da classe de <xref:System.Xml.Linq.XElement?displayProperty=fullName> .

## <a name="see-also"></a>Consulte também
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName> o [valor](../designers/value-xattribute-dynamic-property.md) [das propriedades dinâmicas da classe XElement](../designers/xelement-class-dynamic-properties.md)
