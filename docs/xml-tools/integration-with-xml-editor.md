---
title: Integração do Designer de esquema XML com o editor de XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faad46c6ac2686de69fcb33f2fb482bdb0f4fe00
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525125"
---
# <a name="integration-with-xml-editor"></a>Integração com o editor de XML

O Designer de esquema XML está integrado com o editor de XML. Se você modificar um arquivo XSD no editor de XML, a alteração será refletida na [XML Schema Explorer](../xml-tools/xml-schema-explorer.md). Se você tiver o [exibição de gráfico](../xml-tools/graph-view.md) ou o [exibição de modelo de conteúdo](../xml-tools/content-model-view.md) aberto, a alteração será refletida também lá. Você pode navegar entre o Designer de esquema XML e o editor de XML das seguintes maneiras:

-   No editor de XML, um nó com o botão direito e selecione **Mostrar em XML Schema Explorer**.

-   No modo de gráfico e o **XML Schema Explorer**, clique duas vezes em um nó, ou um nó com o botão direito e selecione **Exibir código**. Na exibição do modelo de conteúdo, um nó com o botão direito e selecione **Exibir código**.

Captura de tela a seguir mostra um esquema XML aberto na **XML Schema Explorer**. O **XML Schema Explorer** exibe o esquema definido em uma exibição de árvore. O editor de XML exibe o modo de exibição de texto do nó que está atualmente ativo na **XML Schema Explorer**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

Às vezes é útil ver o código no editor de XML e o designer gráfico lado a lado. Para exibir os dois arquivos ao mesmo tempo, clique com botão direito em qualquer lugar no editor de XML e selecione **Designer de exibição**. No menu do Windows do Visual Studio, selecione **novo (Horizontal ou Vertical) grupo de guias**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Consulte também

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)