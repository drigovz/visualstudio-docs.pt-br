---
title: Ferramentas XML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2812e45460778a3527f55522c6d3fc98285a548d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58927415"
---
# <a name="xml-tools-in-visual-studio"></a>Ferramentas XML no (Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Extensible Markup Language (XML) * é uma linguagem de marcação que fornece um formato para descrever dados. Isso facilita declarações mais precisas de conteúdo e mais resultados de pesquisa significativos nas diversas plataformas. Além disso, o XML permite a separação da apresentação dos dados. Por exemplo, em HTML, usam-se marcas para dizer ao navegador para exibir dados como negrito ou itálico; em XML, usam-se marcas somente para descrever dados, como nome da cidade, temperatura e pressão barométrica. Em XML, são usadas folhas de estilo como linguagem XSL e CSS (folhas de estilos em cascata) para apresentar os dados em um navegador. O XML separa os dados da apresentação e do processo. Isso permite exibir e processar os dados como desejar, aplicando diferentes folhas de estilo e aplicações.

 O XML é um subconjunto do SGML que é otimizado para entrega na Web. Ele é definido pelo World Wide Web Consortium (W3C). Essa padronização garante que dados estruturados serão uniformes e independentes de aplicativos ou fornecedores.

 O XML está no cerne de muitos recursos do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Os tópicos a seguir indicam os nomes de ferramentas e os recursos relacionados ao XML que são oferecidos no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e no [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Para obter mais informações, consulte o [Developer Center XML](http://go.microsoft.com/fwlink/?LinkID=100176), que fornece a documentação mais recente, informações técnicas, downloads, grupos de notícias e outros recursos para desenvolvedores XML.

## <a name="in-this-section"></a>Nesta seção
 [Trabalhar com dados XML](../xml-tools/working-with-xml-data.md) aborda a função do XML nos dados de maneira é tratada no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Depuração XSLT](../xml-tools/debugging-xslt.md) fornece links para tópicos sobre como usar o depurador do Visual Studio para depurar o XSLT.

## <a name="reference"></a>Referência
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) expõe o [Editor de XML](http://go.microsoft.com/fwlink/?LinkId=228249) árvore por meio de análise [LINQ](http://go.microsoft.com/fwlink/?LinkId=228250) para todos os documentos XML.

 [Referência a padrões XML](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) fornece informações sobre tecnologias XML, incluindo XML, definição de tipo de documento (DTD), linguagem de definição de esquema XML (XSD) e XSLT.

 <xref:System.Xml?displayProperty=fullName> Descreve as classes e outros elementos que compõem o <xref:System.Xml> namespace e fornece links para informações mais detalhadas sobre cada item.

 <xref:System.Xml.Serialization?displayProperty=fullName> Descreve as classes e outros elementos que compõem o <xref:System.Xml.Serialization> namespace e fornece links para informações mais detalhadas sobre cada item.

## <a name="related-sections"></a>Seções relacionadas
 [Modelo de objeto de documento (DOM) XML](http://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) descreve como o <xref:System.Xml.XmlDocument> e suas classes associadas estão em conformidade com as especificações de suporte de namespace de nível 2 e W3C Document Object Model (núcleos) de nível 1.

 [Lendo XML com XmlReader](http://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) descreve como o <xref:System.Xml.XmlReader> fornece não armazenado em cache, encaminhar somente, somente leitura, acesso a dados XML em um fluxo XML.

 [Escrevendo XML com o XmlWriter](http://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) descreve como o <xref:System.Xml.XmlWriter> fornece não armazenado em cache, somente encaminhamento maneira de gerar fluxos XML e ajuda você a criar documentos XML em conformidade com o padrão W3C.

 [Transformações XSLT](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) descreve como o <xref:System.Xml.Xsl.XslCompiledTransform> classe implementa a recomendação XSLT 1.0.

 [Processar dados XML usando o modelo de dados XPath](http://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) descreve como o <xref:System.Xml.XPath.XPathNavigator> classe pode processar dados XML armazenados em um <xref:System.Xml.XPath.XPathDocument> ou um <xref:System.Xml.XmlDocument> objeto. A classe <xref:System.Xml.XPath.XPathNavigator> é baseada no Modelo de Dados XQuery 1.0 e XPath 2.0 ou pode ser usada para navegar e editar dados XML.

 [Modelo de objeto de esquema XML (SOM)](http://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) descreve as classes usadas para criar e manipular esquemas XML, fornecendo um <xref:System.Xml.Schema.XmlSchema> classe para carregar e editar um esquema.
