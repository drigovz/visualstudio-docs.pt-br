---
title: Integração do designer de esquema XML com o editor de XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9df2d97a6ff68299ab70545683970188eb1bfea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601778"
---
# <a name="integration-with-xml-editor"></a>Integração com editor XML

O designer de esquema XML é integrado ao editor de XML. Se você modificar um arquivo XSD no editor de XML, a alteração será refletida no [XML Schema Explorer](../xml-tools/xml-schema-explorer.md). Se você tiver a [exibição de gráfico](../xml-tools/graph-view.md) ou a [exibição de modelo de conteúdo](../xml-tools/content-model-view.md) aberta, a alteração também será refletida ali. Você pode navegar entre o designer de esquema XML e o editor de XML das seguintes maneiras:

- No editor de XML, clique com o botão direito do mouse em um nó e selecione **Mostrar no Gerenciador de esquema XML**.

- Na exibição de gráfico e no **Gerenciador de esquema XML**, clique duas vezes em um nó ou clique com o botão direito do mouse em um nó e selecione **Exibir código**. Na exibição modelo de conteúdo, clique com o botão direito do mouse em um nó e selecione **Exibir código**.

A captura de tela a seguir mostra um esquema XML aberto no **XML Schema Explorer**. O **XML Schema Explorer** exibe o conjunto de esquema em um modo de exibição de árvore. O editor de XML exibe a exibição de texto do nó que está atualmente ativo no **XML Schema Explorer**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

Às vezes, é útil ver o código no editor de XML e o designer gráfico lado a lado. Para exibir os dois arquivos ao mesmo tempo, clique com o botão direito do mouse em qualquer lugar no editor de XML e selecione **Exibir Designer**. No menu do Windows do Visual Studio, selecione **novo grupo de guias horizontal (ou vertical)** .

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Consulte também

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)