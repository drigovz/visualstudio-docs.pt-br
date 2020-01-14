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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9a46523c4c856367e77c345c7e44d0dbc87508f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845985"
---
# <a name="xml-tools-in-visual-studio"></a>Ferramentas XML no (Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Linguagem XML (XML) * é uma linguagem de marcação que fornece um formato para descrever os dados. Isso facilita declarações mais precisas de conteúdo e mais resultados de pesquisa significativos nas diversas plataformas. Além disso, o XML permite a separação da apresentação dos dados. Por exemplo, em HTML, usam-se marcas para dizer ao navegador para exibir dados como negrito ou itálico; em XML, usam-se marcas somente para descrever dados, como nome da cidade, temperatura e pressão barométrica. Em XML, são usadas folhas de estilo como linguagem XSL e CSS (folhas de estilos em cascata) para apresentar os dados em um navegador. O XML separa os dados da apresentação e do processo. Isso permite exibir e processar os dados como desejar, aplicando diferentes folhas de estilo e aplicações.

 O XML é um subconjunto do SGML que é otimizado para entrega na Web. Ele é definido pelo World Wide Web Consortium (W3C). Essa padronização garante que dados estruturados serão uniformes e independentes de aplicativos ou fornecedores.

 O XML está no cerne de muitos recursos do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Os tópicos a seguir indicam os nomes de ferramentas e os recursos relacionados ao XML que são oferecidos no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e no [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Para obter mais informações, consulte o [centro de desenvolvedores XML](https://msdn.microsoft.com/data/bb190600.aspx), que fornece a documentação, informações técnicas, downloads, grupos de notícias e outros recursos mais recentes para desenvolvedores de XML.

## <a name="in-this-section"></a>Nesta seção
 [Trabalhando com dados XML](../xml-tools/working-with-xml-data.md) Discute a função de XML na maneira como os dados são manipulados em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Depuração XSLT](../xml-tools/debugging-xslt.md) Fornece links para tópicos sobre como usar o depurador do Visual Studio para depurar o XSLT.

## <a name="reference"></a>Referência
 [Microsoft.VisualStudio.XmlEditor](https://msdn.microsoft.com/library/microsoft.visualstudio.xmleditor.aspx) expõe o [Editor de XML](https://msdn.microsoft.com/library/ms255810.aspx) árvore por meio de análise [LINQ](https://msdn.microsoft.com/library/system.xml.linq.aspx) para todos os documentos XML.

 [Referência a padrões XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) fornece informações sobre tecnologias XML, incluindo XML, definição de tipo de documento (DTD), linguagem de definição de esquema XML (XSD) e XSLT.

 <xref:System.Xml?displayProperty=fullName> Descreve as classes e outros elementos que compõem o <xref:System.Xml> namespace e fornece links para informações mais detalhadas sobre cada item.

 <xref:System.Xml.Serialization?displayProperty=fullName> Descreve as classes e outros elementos que compõem o <xref:System.Xml.Serialization> namespace e fornece links para informações mais detalhadas sobre cada item.

## <a name="related-sections"></a>Seções Relacionadas
 [Modelo de objeto de documento (DOM) XML](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) descreve como o <xref:System.Xml.XmlDocument> e suas classes associadas estão em conformidade com as especificações de suporte de namespace de nível 2 e W3C Document Object Model (núcleos) de nível 1.

 [Lendo XML com XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) Descreve como a <xref:System.Xml.XmlReader> fornece acesso não armazenado em cache, somente encaminhamento e somente leitura a dados XML por meio de um fluxo XML.

 [Escrevendo XML com o XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) Descreve como a <xref:System.Xml.XmlWriter> fornece o modo não armazenado em cache, somente encaminhamento, a maneira de gerar fluxos XML e ajuda a criar documentos XML que estão em conformidade com o padrão W3C.

 [Transformações XSLT](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) Descreve como a classe <xref:System.Xml.Xsl.XslCompiledTransform> implementa a recomendação do XSLT 1,0.

 [Processar dados XML usando o modelo de dados XPath](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) Descreve como a classe <xref:System.Xml.XPath.XPathNavigator> pode processar dados XML armazenados em um <xref:System.Xml.XPath.XPathDocument> ou um objeto <xref:System.Xml.XmlDocument>. A classe <xref:System.Xml.XPath.XPathNavigator> é baseada no Modelo de Dados XQuery 1.0 e XPath 2.0 ou pode ser usada para navegar e editar dados XML.

 [Modelo de objeto de esquema XML (SOM)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) descreve as classes usadas para criar e manipular esquemas XML, fornecendo um <xref:System.Xml.Schema.XmlSchema> classe para carregar e editar um esquema.
