---
title: Elemento (Propriedade Dinâmica XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e7789a94c38f7c6d7db22d9214b19857e4c62055
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753881"
---
# <a name="element-xelement-dynamic-property"></a>Elemento (propriedade dinâmica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtém um indexador usado para recuperar a instância do elemento filho que corresponde ao nome especificado expandido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 Um indicador de tipo `XElement Item(String expandedName)`. Esse marcador aceita um parâmetro expandido de nome e retorna <xref:System.Xml.Linq.XElement>correspondente, ou `null` se não houver nenhum elemento com o nome especificado.  
  
## <a name="remarks"></a>Comentários  
 Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Element%2A> da classe de <xref:System.Xml.Linq.XContainer?displayProperty=fullName> .  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Propriedades Dinâmicas da Classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elementos](../designers/elements-xelement-dynamic-property.md)
