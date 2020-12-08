---
title: Controle de gráfico
description: Saiba que, quando você adiciona um gráfico a uma planilha, o Visual Studio cria um objeto de gráfico com o qual você pode programar diretamente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 45de5170ca8a8b7e8a71521e18523e73ebc24046
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847814"
---
# <a name="chart-control"></a>Controle de gráfico
  O <xref:Microsoft.Office.Tools.Excel.Chart> controle é um objeto de gráfico que expõe eventos. Quando você adiciona um gráfico a uma planilha, o Visual Studio cria um <xref:Microsoft.Office.Tools.Excel.Chart> objeto que você pode programar diretamente sem precisar atravessar o Microsoft Office modelo de objeto do Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Criar o controle
 Você pode adicionar <xref:Microsoft.Office.Tools.Excel.Chart> controles a uma Microsoft Office planilha do Excel em tempo de design ou em tempo de execução em um projeto de nível de documento.

 Você pode adicionar <xref:Microsoft.Office.Tools.Excel.Chart> controles a uma planilha em tempo de execução em um suplemento do VSTO. Para obter mais informações, consulte [como: adicionar controles de gráfico a planilhas](../vsto/how-to-add-chart-controls-to-worksheets.md).

> [!NOTE]
> Objetos de gráfico criados dinamicamente não são persistidos na planilha como controles de host quando a planilha é fechada. Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="formatting"></a>Formatação
 Toda a formatação que pode ser aplicada a um <xref:Microsoft.Office.Interop.Excel.Chart> também pode ser aplicada a um <xref:Microsoft.Office.Tools.Excel.Chart> controle. Isso inclui bordas, fontes, tipo de gráfico, linhas de grade, legenda e rótulos de dados.

## <a name="events"></a>Eventos
 Os eventos a seguir estão disponíveis para o <xref:Microsoft.Office.Tools.Excel.Chart> controle:

- <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>

- <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>

- <xref:Microsoft.Office.Tools.Excel.Chart.Resize>

- <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>

## <a name="see-also"></a>Confira também
- [Exemplos e orientações de desenvolvimento do Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Estenda documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Como: adicionar controles de gráfico a planilhas](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
