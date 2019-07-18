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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 368b18e7524e0cff31139de67f8092f9069246bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148051"
---
# <a name="xml-xelement-dynamic-property"></a>XML (propriedade dinâmica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtém o conteúdo sem formatação XML do elemento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 <xref:System.String> que representa o conteúdo sem formatação XML do elemento.  
  
## <a name="remarks"></a>Comentários  
 Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> da classe de <xref:System.Xml.Linq.XNode?displayProperty=fullName> , com o parâmetro de `SaveOptions` definido como <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>Veja também  
 [Propriedades Dinâmicas da Classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valor](../designers/value-xelement-dynamic-property.md)
