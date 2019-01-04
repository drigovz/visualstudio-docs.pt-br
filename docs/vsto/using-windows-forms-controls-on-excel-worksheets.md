---
title: Use os controles de Windows Forms em planilhas do Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: abc3e08a867af9b04d7ce1da1449f108a099b238
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823413"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Use os controles de Windows Forms em planilhas do Excel
  Você pode adicionar controles dos Windows Forms para suas pastas de trabalho do Microsoft Office Excel da mesma maneira que você adicione controles ao Windows Forms. Para obter informações gerais sobre como trabalhar com controles em documentos, consulte [controles de formulários do Windows de visão geral de documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Considerações sobre o controle para Excel  
 Há algumas considerações que são específicas para o Excel.  
  
### <a name="match-control-size-to-cell-size"></a>Tamanho do controle de correspondência para o tamanho da célula  
 Você pode definir o controle a ser redimensionado automaticamente quando o tamanho da célula pai é alterado. Para obter mais informações, confira [Como: Redimensionar controles dentro de células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>Adicionar componentes que são compartilhados por todas as planilhas  
 Você pode adicionar componentes que você deseja compartilhar entre todas as planilhas, como um <xref:System.Data.DataSet>, para o Designer de pasta de trabalho, em vez de para planilhas. O componente será exibido na bandeja de componentes.  
  
### <a name="formula-for-embedding-controls"></a>Fórmula para a inserção de controles  
 Quando você seleciona um controle no Excel, você verá **=EMBED("WinForms.Control.Host","")** na **barra de fórmulas**. Esse texto é necessário e não deve ser excluído.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Redimensionar controles dentro de células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Como: Ocultar controles em planilhas durante a impressão](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Passo a passo: Alterar a formatação da planilha usando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Passo a passo: Exibir texto em uma caixa de texto em uma planilha usando um botão](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Passo a passo: Um gráfico em uma planilha usando botões de opção de atualização](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
