---
title: 'Como: Copiar dados e formatar em planilhas de forma programática'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 77feefe7a2d274403e483dbaa3167f53f72ae168
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575293"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Como: Copiar dados e formatar em planilhas de forma programática
  Você pode copiar dados de um intervalo em uma folha para todas as outras planilhas em uma pasta de trabalho usando o <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> método. Especifique um intervalo, e se você deseja copiar os dados, formatação ou ambos.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer um intervalo chamado `rangeData` em uma planilha.

## <a name="see-also"></a>Consulte também
- [Trabalhar com planilhas](../vsto/working-with-worksheets.md)
- [Como: Adicionar novas planilhas a pastas de trabalho programaticamente](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Como: Alterar programaticamente a formatação em linhas de planilhas que contêm células selecionadas](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
