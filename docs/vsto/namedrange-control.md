---
title: Controle NamedRange
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e2b5b5d246e1033148bc199da6e7d2bdfb7aa9b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254723"
---
# <a name="namedrange-control"></a>Controle NamedRange
  O <xref:Microsoft.Office.Tools.Excel.NamedRange> controle é um intervalo que tem um nome exclusivo, expõe eventos e pode ser associado a dados. Para obter mais informações, consulte [visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Criar o controle
 Você pode adicionar <xref:Microsoft.Office.Tools.Excel.NamedRange> controles a uma Microsoft Office planilha do Excel em tempo de design ou em tempo de execução em projetos de nível de documento.

 Você pode adicionar <xref:Microsoft.Office.Tools.Excel.NamedRange> controles a uma planilha em tempo de execução em um suplemento do VSTO. Para obter mais informações, consulte [como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

> [!NOTE]
> Por padrão, os intervalos nomeados criados dinamicamente não são mantidos na planilha como controles de host quando a planilha é fechada. Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

 <xref:Microsoft.Office.Tools.Excel.NamedRange> os controles só podem consistir em intervalos em planilhas específicas. <xref:Microsoft.Office.Tools.Excel.NamedRange> os controles não podem ter nomes relativos que se aplicam a todas as planilhas e não podem consistir em intervalos que abrangem duas ou mais planilhas em uma pasta de trabalho (intervalos 3D).

## <a name="bind-data-to-the-control"></a>Associar dados ao controle
 Um intervalo nomeado pareceria ser um bom candidato para associação de dados complexa, pois ele pode ter várias células; no entanto, um intervalo é meramente uma coleção de células que não podem ser facilmente mapeadas para uma coluna específica de um conjunto de dado. Portanto, os <xref:Microsoft.Office.Tools.Excel.NamedRange> controles só oferecem suporte à vinculação de dados simples. O <xref:Microsoft.Office.Tools.Excel.ListObject> controle pode ser usado para associação de dados complexa. Para obter mais informações, consulte o [controle ListObject](../vsto/listobject-control.md).

 O <xref:Microsoft.Office.Tools.Excel.NamedRange> controle pode ser associado a uma fonte de dados usando as <xref:System.Windows.Forms.Control.DataBindings%2A> Propriedades. A propriedade de associação de dados padrão do <xref:Microsoft.Office.Tools.Excel.NamedRange> controle é <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> .

 Se os dados no DataSet associado forem atualizados por meio de qualquer mecanismo, o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle refletirá as alterações.

## <a name="formatting"></a>Formatação
 A formatação que pode ser aplicada a um <xref:Microsoft.Office.Interop.Excel.Range> pode ser aplicada a um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle. Isso inclui bordas, fontes, formatos de número e estilos.

## <a name="rename-the-control"></a>Renomear o controle
 Quando você adiciona um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle à sua planilha da **caixa de ferramentas**, o Visual Studio gera automaticamente um nome para o controle. Você pode alterar o nome na janela **Propriedades** .

## <a name="events"></a>Eventos
 Os eventos a seguir estão disponíveis para o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle:

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>

## <a name="see-also"></a>Confira também
- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Exemplos e orientações de desenvolvimento do Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Estenda documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Como: redimensionar controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Walkthrough: programa em relação a eventos de um controle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
