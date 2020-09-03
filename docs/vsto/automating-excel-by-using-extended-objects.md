---
title: Automatizar o Excel usando objetos estendidos
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65734f5397bae8c35fb8e312041d0600b8fa84e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254342"
---
# <a name="automate-excel-by-using-extended-objects"></a>Automatizar o Excel usando objetos estendidos
  Ao desenvolver soluções do Excel no Visual Studio, você pode usar *itens de host* e de *controle de host*s em suas soluções. Esses são objetos que estendem determinados objetos comumente usados no modelo de objeto do Excel (ou seja, o modelo de objeto que é exposto pelo assembly de interoperabilidade primário para o Excel), como os <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Range> objetos e. Os objetos estendidos se comportam como os objetos do Excel em que se baseiam, mas eles adicionam recursos adicionais, como novos eventos e recursos de vinculação de dados aos objetos.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Os itens de host e os controles de host estão disponíveis tanto no suplemento do VSTO quanto em personalizações no nível do documento, embora o contexto no qual eles possam ser usados seja diferente para cada tipo de solução. Para obter mais informações, consulte [visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md).

## <a name="excel-host-items"></a>Itens de host do Excel
 Os projetos do Excel oferecem acesso a vários itens de host:

- <xref:Microsoft.Office.Tools.Excel.Worksheet>. Este item de host contém e representa uma planilha em seu projeto. Ele também atua como um contêiner para controles gerenciados, incluindo controles de host e controles de Windows Forms, e mantém informações sobre os controles em sua superfície. Para obter mais informações, consulte [planilha de item de host](../vsto/worksheet-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.Workbook>. Esse item de host representa a pasta de trabalho em seu projeto e atua como um contêiner para componentes que são compartilhados por todas as planilhas na pasta de trabalho. Para obter mais informações, veja [item de host da pasta de trabalho](../vsto/workbook-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Esse item de host é uma planilha no Excel que contém apenas um gráfico e expõe eventos.

     Quando você adiciona uma planilha de gráfico em tempo de design como uma nova planilha em seu Microsoft Office projeto de personalização no nível de documento do Excel, o Visual Studio cria automaticamente um <xref:Microsoft.Office.Tools.Excel.ChartSheet> item de host.

     Embora um <xref:Microsoft.Office.Tools.Excel.ChartSheet> item de host seja uma planilha no Excel, você não pode adicionar nenhum controle à planilha de gráfico. Se você quiser ter outros controles em uma planilha com um gráfico, não use uma planilha de gráfico. Em vez disso, você pode inserir um gráfico como um objeto incorporado em uma planilha usando o <xref:Microsoft.Office.Tools.Excel.Chart> controle de host. Para obter mais informações, consulte [controle de gráfico](../vsto/chart-control.md).

## <a name="excel-host-controls"></a>controles de host do Excel
 Há vários controles de host para o Excel que ajudam a criar, organizar e automatizar pastas de trabalho e planilhas. Esses controles de host fornecem eventos e recursos de associação de dados que suas contrapartes no modelo de objeto nativo do Excel não têm.

 Para obter mais informações sobre os controles de host que você pode usar em projetos do Excel, consulte os seguintes tópicos:

- [Controle de gráfico](../vsto/chart-control.md)

- [Controle ListObject](../vsto/listobject-control.md)

- [Controle NamedRange](../vsto/namedrange-control.md)

- [Controle XmlMappedRange](../vsto/xmlmappedrange-control.md)

## <a name="see-also"></a>Confira também
- [Como preencher controles ListObject com dados](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Como: adicionar controles de gráfico a planilhas](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Como adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Como: adicionar controles XMLMappedRange a planilhas](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Como: redimensionar controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Como: redimensionar controles de ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Como validar dados quando uma nova linha é adicionada a um controle ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Como mapear colunas ListObject para dados](../vsto/how-to-map-listobject-columns-to-data.md)
- [Walkthrough: programa em relação a eventos de um controle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Estenda documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
