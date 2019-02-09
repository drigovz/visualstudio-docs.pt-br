---
title: Integração do Designer de esquema XML com o Editor de XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e06141eb6f6d7383a433a1f9b0ba29944e26a329
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930292"
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