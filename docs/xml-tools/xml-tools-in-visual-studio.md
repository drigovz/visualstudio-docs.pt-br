---
title: Editor de XML e o designer de esquema
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8854aee047fa961c4f0973397cfc2fe6ac6e6ad
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526562"
---
# <a name="xml-tools-in-visual-studio"></a>Ferramentas XML no Visual Studio

*Extensible Markup Language (XML)* é uma linguagem de marcação que fornece um formato para descrever dados. O XML separa os dados e sua apresentação usando associados folhas de estilo, como Extensible Stylesheet Language (XSL) e folhas de estilo em cascata (CSS). O Visual Studio inclui ferramentas e recursos que facilitam trabalhar com os esquemas XML, XSLT e XML.

## <a name="xml-editor"></a>Editor de XML

O [editor de XML](xml-editor.md) é usado para editar documentos XML. Ele fornece a sintaxe XML completa, verificação de validação de esquema enquanto você digita, codificação por cores e IntelliSense. Se um esquema ou um definição de tipo de documento forem fornecidos, ele é usado pelo IntelliSense para listar os elementos e atributos permitidos.

Os recursos adicionais incluem:

- Suporte a trechos de XML, incluindo trechos gerados por esquema

- Para que os elementos podem ser expandidos e recolhidos de estrutura de tópicos de documento

- A capacidade de executar transformações XSLT e para exibir os resultados como texto, XML ou HTML

- A capacidade de gerar esquemas XSD (linguagem) de definição de esquema XML do documento de instância XML

- Suporte para editar folhas de estilos XSLT, incluindo suporte ao IntelliSense

- XML Schema Explorer

## <a name="xml-schema-designer"></a>Designer de Esquema XML

O [Designer de esquema XML](xml-schema-designer.md) é integrado ao Visual Studio e o editor de XML para que você possa trabalhar com esquemas XSD (linguagem) de definição de esquema XML.

## <a name="xslt-debugging"></a>Depuração de XSLT

O Visual Studio suporta [depuração de folhas de estilos XSLT](../xml-tools/debugging-xslt.md). Usando o depurador, você pode definir pontos de quebra em uma folha de estilos XSLT, entrar em uma folha de estilos XSLT a partir do código, e assim por diante.

> [!NOTE]
> O depurador XSLT só está disponível na edição Enterprise do Visual Studio.

## <a name="see-also"></a>Consulte também

- <xref:System.Xml?displayProperty=fullName>
- [Transformações XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Processar dados XML usando o modelo de dados XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [DOM (Modelo de Objeto do Documento) de XML](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [XML Schema Object Model (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som) [SOM (Modelo de Objeto de Esquema) XML]