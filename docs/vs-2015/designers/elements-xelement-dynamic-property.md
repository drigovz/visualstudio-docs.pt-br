---
title: Elements (propriedade dinâmica de XElement)| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 158e200a33b4783df9f63f42a1eca7bb8957d449
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777695"
---
# <a name="elements-xelement-dynamic-property"></a>Elementos (propriedade dinâmica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtém um indexador usado para recuperar elementos filho do elemento atual que corresponde ao nome especificado expandido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
elem.Elements[{namespaceName}localName]   
```  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 Um indicador de tipo `IEnumerable<XElement> Item(String expandedName)`. Esse marcador utiliza o nome expandido de elementos filhos desejados e retorna os elementos filho correspondentes em uma coleção de <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` .  
  
## <a name="remarks"></a>Comentários  
 Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> da classe de <xref:System.Xml.Linq.XContainer> .  
  
 Os elementos na coleção retornada estão na ordem de documento-fonte XML.  
  
 Esta propriedade usa a execução adiada.  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades Dinâmicas da Classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elemento](../designers/element-xelement-dynamic-property.md)   
 [Descendentes](../designers/descendants-xelement-dynamic-property.md)
