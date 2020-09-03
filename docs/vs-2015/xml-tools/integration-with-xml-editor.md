---
title: Integração com o editor de XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c0d1088e9932613466209ef8517ac5035c0b613
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656249"
---
# <a name="integration-with-xml-editor"></a>Integração com editor XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O designer de esquema XML está integrado com o editor XML. Se você modificar um arquivo XSD no editor de XML, a alteração será refletida no [XML Schema Explorer](../xml-tools/xml-schema-explorer.md). Se você tiver a [exibição de gráfico](../xml-tools/graph-view.md) ou a [exibição de modelo de conteúdo](../xml-tools/content-model-view.md) aberta, a alteração também será refletida ali. Você pode navegar entre o designer de esquema XML e o editor XML das seguintes maneiras:

- No editor de XML, clique com o botão direito do mouse em um nó e selecione **Mostrar no Gerenciador de esquema XML**.

- Na exibição de gráfico e no Gerenciador de esquema XML, clique duas vezes em um nó ou clique com o botão direito do mouse em um nó e selecione **Exibir código**. Na exibição modelo de conteúdo, clique com o botão direito do mouse em um nó e selecione **Exibir código**.

  A captura de tela a seguir mostra um esquema XML aberto em XML Schema Explorer. XML Schema Explorer exibe o esquema definido em um modo de exibição de árvore. O editor XML exibe a exibição do texto do nó que está atualmente ativa em XML Schema Explorer.

  ![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")

  Às vezes é útil consulte o código no editor XML e no designer gráfico lado a lado. Para exibir os dois arquivos ao mesmo tempo, clique com o botão direito do mouse em qualquer lugar no editor de XML e selecione **Exibir Designer**. No menu do Windows do Visual Studio, selecione **novo grupo de guias horizontal (ou vertical)**.

  ![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")

## <a name="see-also"></a>Consulte Também
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
