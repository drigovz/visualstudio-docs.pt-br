---
title: Integração do designer de esquema XML com o editor de XML
description: Saiba mais sobre a integração entre o designer de esquema XML e o editor de XML e como as alterações feitas em um são refletidas no outro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fe1bfcd422dbfc5f010ae7819e2fccbeafb8227
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934618"
---
# <a name="integration-with-xml-editor"></a>Integração com editor XML

O designer de esquema XML é integrado ao editor de XML. Se você modificar um arquivo XSD no editor de XML, a alteração será refletida no [XML Schema Explorer](../xml-tools/xml-schema-explorer.md). Se você tiver a [exibição de gráfico](../xml-tools/graph-view.md) ou a [exibição de modelo de conteúdo](../xml-tools/content-model-view.md) aberta, a alteração também será refletida ali. Você pode navegar entre o designer de esquema XML e o editor de XML das seguintes maneiras:

- No editor de XML, clique com o botão direito do mouse em um nó e selecione **Mostrar no Gerenciador de esquema XML**.

- Na exibição de gráfico e no **Gerenciador de esquema XML**, clique duas vezes em um nó ou clique com o botão direito do mouse em um nó e selecione **Exibir código**. Na exibição modelo de conteúdo, clique com o botão direito do mouse em um nó e selecione **Exibir código**.

A captura de tela a seguir mostra um esquema XML aberto no **XML Schema Explorer**. O **XML Schema Explorer** exibe o conjunto de esquema em um modo de exibição de árvore. O editor de XML exibe a exibição de texto do nó que está atualmente ativo no **XML Schema Explorer**.

![Captura de tela de um projeto do Visual Studio mostrando um nó XML no painel do editor de XML e uma exibição de árvore do conjunto de esquema no painel do Gerenciador de esquema XML.](../xml-tools/media/xsddesignerwithxmleditor.gif)

Às vezes, é útil ver o código no editor de XML e o designer gráfico lado a lado. Para exibir os dois arquivos ao mesmo tempo, clique com o botão direito do mouse em qualquer lugar no editor de XML e selecione **Exibir Designer**. No menu do Windows do Visual Studio, selecione **novo grupo de guias horizontal (ou vertical)**.

![Captura de tela de um projeto do Visual Studio mostrando o painel do designer de exibição, o painel do editor de XML e o painel do Gerenciador de esquema XML.](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Confira também

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
