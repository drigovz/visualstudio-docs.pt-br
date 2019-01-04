---
title: Integração do Designer de esquema XML com o Editor de XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a4d97ce590929b6cc2cf56997255822b692cc9e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865005"
---
# <a name="integration-with-xml-editor"></a>Integração com o editor de XML

O designer de esquema XML está integrado com o editor XML. Se você modificar um arquivo XSD no Editor XML, a alteração será refletida na [XML Schema Explorer](../xml-tools/xml-schema-explorer.md). Se você tiver o [exibição de gráfico](../xml-tools/graph-view.md) ou o [exibição de modelo de conteúdo](../xml-tools/content-model-view.md) aberto, a alteração será refletida também lá. Você pode navegar entre o designer de esquema XML e o editor XML das seguintes maneiras:

-   No Editor de XML, um nó com o botão direito e selecione **Mostrar em XML Schema Explorer**.

-   No modo de gráfico e o **XML Schema Explorer**, clique duas vezes em um nó, ou um nó com o botão direito e selecione **Exibir código**. Na exibição do modelo de conteúdo, um nó com o botão direito e selecione **Exibir código**.

Captura de tela a seguir mostra um esquema XML aberto na **XML Schema Explorer**. O **XML Schema Explorer** exibe o esquema definido em uma exibição de árvore. O Editor de XML exibe o modo de exibição de texto do nó que está atualmente ativo na **XML Schema Explorer**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

Às vezes é útil consulte o código no editor XML e no designer gráfico lado a lado. Para exibir os dois arquivos ao mesmo tempo, clique com botão direito em qualquer lugar no Editor de XML e selecione **Designer de exibição**. No menu do Windows do Visual Studio, selecione **novo (Horizontal ou Vertical) grupo de guias**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Consulte também

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)