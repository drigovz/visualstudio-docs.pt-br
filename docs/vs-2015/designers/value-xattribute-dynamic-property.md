---
title: Valor (propriedade dinâmica de XAttribute) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9a31b4c4182ed67a3e67d3c25c2c5ccf50e083f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664056"
---
# <a name="value-xattribute-dynamic-property"></a>Valor (propriedade dinâmica de XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtém ou define o valor de atributo XML.

## <a name="syntax"></a>Syntax

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/Valor do retorno
 <xref:System.String> que contém o valor deste atributo.

## <a name="exceptions"></a>Exceções

|Tipo de exceção|Condição|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|Ao definir, `value` é `null`.|

## <a name="remarks"></a>Comentários
 Esta propriedade é equivalente à propriedade de <xref:System.Xml.Linq.XAttribute.Value%2A> da classe de <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> , mas suporta essa propriedade dinâmica também alterar notificações.

## <a name="see-also"></a>Consulte Também
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>[Atributo](../designers/attribute-xelement-dynamic-property.md) de [propriedades dinâmicas da classe XAttribute](../designers/xattribute-class-dynamic-properties.md)
