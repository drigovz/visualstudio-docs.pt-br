---
title: Usar controles de Windows Forms em planilhas do Excel
description: Saiba como você pode adicionar controles de Windows Forms às suas pastas de trabalho do Microsoft Excel da mesma maneira que adiciona controles a Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 015fffa51358c3a7a13d98950392d0749560c089
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526513"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Usar controles de Windows Forms em planilhas do Excel
  Você pode adicionar Windows Forms controles às suas pastas de trabalho do Microsoft Office Excel da mesma maneira que adiciona controles ao Windows Forms. Para obter informações gerais sobre como trabalhar com controles em documentos, consulte [visão geral dos controles de Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Considerações de controle para o Excel
 Há algumas considerações específicas para o Excel.

### <a name="match-control-size-to-cell-size"></a>Corresponder o tamanho do controle ao tamanho da célula
 Você pode definir o controle a ser redimensionado automaticamente quando o tamanho da célula pai for alterado. Para obter mais informações, consulte [como: redimensionar controles nas células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Adicionar componentes que são compartilhados por todas as planilhas
 Você pode adicionar componentes que deseja compartilhar entre todas as planilhas, como um <xref:System.Data.DataSet> , ao designer de pasta de trabalho em vez de às planilhas. O componente será exibido na bandeja do componente.

### <a name="formula-for-embedding-controls"></a>Fórmula para inserir controles
 Ao selecionar um controle no Excel, você verá **= Inserir ("WinForms. Control. host", "")** na **barra de fórmulas**. Esse texto é necessário e não deve ser excluído.

## <a name="see-also"></a>Veja também
- [Como: redimensionar controles nas células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Como: Ocultar controles em planilhas ao imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Walkthrough: alterar a formatação da planilha usando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Walkthrough: exibir texto em uma caixa de texto em uma planilha usando um botão](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Walkthrough: atualizar um gráfico em uma planilha usando botões de opção](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
