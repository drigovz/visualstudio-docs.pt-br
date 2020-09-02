---
title: XML (propriedade dinâmica de XElement)| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c794d79d62fc580001efc5cf16993d4ac5fef48b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663842"
---
# <a name="xml-xelement-dynamic-property"></a>XML (propriedade dinâmica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtém o conteúdo sem formatação XML do elemento.

## <a name="syntax"></a>Syntax

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/Valor do retorno
 <xref:System.String> que representa o conteúdo sem formatação XML do elemento.

## <a name="remarks"></a>Comentários
 Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> da classe de <xref:System.Xml.Linq.XNode?displayProperty=fullName> , com o parâmetro de `SaveOptions` definido como <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Consulte Também
 [Valor](../designers/value-xelement-dynamic-property.md) de [propriedades dinâmicas da classe XElement](../designers/xelement-class-dynamic-properties.md)
