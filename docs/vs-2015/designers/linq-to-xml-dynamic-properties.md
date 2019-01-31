---
title: Propriedades dinâmicas de LINQ to XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6fce9bca76b604413dc5bd4962760ee4ce08a6ea
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790607"
---
# <a name="linq-to-xml-dynamic-properties"></a>Propriedades dinâmicas LINQ to XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta seção fornece informações de referência sobre as propriedades dinâmicas em LINQ to XML. Especificamente, essas propriedades são expostos por classes de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> , que estão no espaço de <xref:System.Xml.Linq> .  
  
 Conforme explicado no tópico [Visão geral de vinculação de dados de WPF com LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), cada uma das propriedades dinâmicas é equivalente a uma propriedade pública ou método padrão na mesma classe. Esses membros padrão devem ser usados para a maioria das finalidades; as propriedades dinâmicas são fornecidas especificamente para cenários de associação de dados LINQ to XML. Para obter mais informações sobre membros padrão dessas classes, consulte os tópicos de referência de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> .  
  
 Em relação a seus valores resolvidos, as propriedades dinâmicas nesta seção se enquadram em duas categorias:  
  
- O simples, como as propriedades de `Value` classes de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> , que são consideradas como um único valor.  
  
- Valores indexados, como as propriedades [Elementos](../designers/elements-xelement-dynamic-property.md) e [Descendentes](../designers/descendants-xelement-dynamic-property.md) de <xref:System.Xml.Linq.XElement>, que são resolvidas em um tipo de indexador. Para que os tipos do indexador são resolvidos com o valor desejado ou à coleção, um parâmetro expandido do nome deve ser-lhes passado.  
  
  Todas as propriedades dinâmicas que retornam um valor indexado de uso de <xref:System.Collections.Generic.IEnumerable%601> de tipo deffered a execução. Para obter mais informações sobre a execução adiada, consulte [Introdução a Consultas de LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Propriedades dinâmicas da classe XAttribute](../designers/xattribute-class-dynamic-properties.md)|Fornece detalhes sobre as propriedades dinâmicas expostos pela classe de <xref:System.Xml.Linq.XAttribute> .|  
|[Propriedades dinâmicas da classe XElement](../designers/xelement-class-dynamic-properties.md)|Fornece detalhes sobre as propriedades dinâmicas expostos pela classe de <xref:System.Xml.Linq.XElement> .|  
  
## <a name="reference"></a>Referência  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 [Vinculação de dados de WPF com LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Visão geral da vinculação de dados do WPF com LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introdução a consultas LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)
