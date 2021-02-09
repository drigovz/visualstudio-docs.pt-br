---
title: Automatizar o Word usando objetos estendidos
description: Saiba como você pode usar itens de host e controles de host em suas soluções ao desenvolver soluções do Word no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 42784e27c26d729a87d5363ca41b6d2c70a364d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882499"
---
# <a name="automate-word-by-using-extended-objects"></a>Automatizar o Word usando objetos estendidos
  Ao desenvolver soluções do Word no Visual Studio, você pode usar *itens de host* e de *controle de host* s em suas soluções. Esses são objetos que estendem determinados objetos comumente usados no modelo de objeto do Word (ou seja, o modelo de objeto que é exposto pelo assembly de interoperabilidade primário do Word), como os <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.ContentControl> objetos e. Os objetos estendidos se comportam como os objetos do Word em que se baseiam, mas adicionam eventos adicionais e recursos de associação de dados aos objetos.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Os itens de host e os controles de host estão disponíveis nos suplementos do VSTO e nas personalizações no nível do documento, embora o contexto no qual eles possam ser usados seja diferente para cada tipo de solução. Para obter mais informações, consulte [visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md).

## <a name="document-host-item"></a>Item de host do documento
 Os projetos do Word fornecem acesso ao <xref:Microsoft.Office.Tools.Word.Document> item do host. O <xref:Microsoft.Office.Tools.Word.Document> item de host atua como um contêiner para outros controles, incluindo controles de host e controles de Windows Forms, e mantém informações sobre os controles em sua superfície. O <xref:Microsoft.Office.Tools.Word.Document> item de host também fornece a maioria dos mesmos membros que a <xref:Microsoft.Office.Interop.Word.Document> classe, que é a classe correspondente no modelo de objeto do Word.

 Para obter mais informações, consulte [documentar item de host](../vsto/document-host-item.md).

## <a name="word-host-controls"></a>controles de host do Word
 Há vários controles de host para o Word que ajudam a criar, organizar e automatizar documentos. A maioria de suas funcionalidades envolve a importação, a apresentação e a proteção de dados. Esses controles de host fornecem eventos e recursos de associação de dados que suas contrapartes no modelo de objeto do Word nativo não têm.

 Em projetos de nível de documento, você pode adicionar qualquer controle de host ao seu documento em tempo de design ou pode adicionar controles de conteúdo e de indicador em tempo de execução. Em projetos de suplemento do VSTO, você pode adicionar controles de conteúdo e controles de indicador a qualquer documento aberto em tempo de execução.

 Para obter mais informações sobre os controles de host que você pode usar em projetos do Word, consulte os seguintes tópicos:

- [Controles de conteúdo](../vsto/content-controls.md)

- [Controle de indicador](../vsto/bookmark-control.md)

- [Controle XMLNode](../vsto/xmlnode-control.md)

- [Controle de XMLNodes](../vsto/xmlnodes-control.md)

## <a name="see-also"></a>Confira também
- [Como: adicionar controles de conteúdo a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Como: adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Como: adicionar controles XMLNode a documentos do Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Como: adicionar controles de XMLNodes a documentos do Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Como: redimensionar controles de indicador](../vsto/how-to-resize-bookmark-controls.md)
- [Walkthrough: criar um modelo usando controles de conteúdo](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Walkthrough: associar controles de conteúdo a partes XML personalizadas](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
- [Walkthrough: criar menus de atalho para indicadores](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Soluções do Word](../vsto/word-solutions.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Estenda documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
