---
title: 'Como: Adicionar controles do Windows Forms a documentos do Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a745794bb23902872f4b09c39eb8a3b3c1706137
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255876"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Como: Adicionar controles de Windows Forms a documentos do Office
  Você pode adicionar Windows Forms controles para Microsoft Office documentos do Excel e do Microsoft Office Word em tempo de design em projetos de nível de documento. Em tempo de execução, você pode adicionar controles em personalizações em nível de documento e em suplementos do VSTO. Por exemplo, você pode adicionar um <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> controle à sua planilha para que os usuários possam selecionar em uma lista de opções.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 Este tópico descreve as seguintes tarefas:

- [Adicionar controles em tempo de design](#designtime)

- [Adicionar controles em tempo de execução em projetos de nível de documento](#runtimedoclevel)

- [Adicionar controles em tempo de execução em suplementos do VSTO](#runtimeaddin)

  ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") Para ver uma demonstração de vídeo relacionada [, consulte Como fazer: Adicionar controles a uma superfície de documento em tempo de execução? ](http://go.microsoft.com/fwlink/?LinkId=132782).

## <a name="designtime"></a>Adicionar controles em tempo de design
 Há várias maneiras de adicionar controles de Windows Forms ao documento em um projeto de nível de documento em tempo de design.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Para arrastar um controle de Windows Forms para o documento

1. Crie ou abra um projeto de pasta de trabalho do Excel ou um projeto de documento do Word no Visual Studio para que o documento fique visível no designer. Para obter informações sobre como criar projetos [, consulte Como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

2. Na guia **controles comuns** da caixa de **ferramentas**, clique no controle que você deseja adicionar e arraste-o para o documento.

    > [!NOTE]
    > Ao selecionar um controle no Excel, você verá **= Inserir ("WinForms. Control. host", "")** na **barra de fórmulas**. Esse texto é necessário e não deve ser excluído.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Para desenhar um controle de Windows Forms no documento

1. Crie ou abra um projeto de pasta de trabalho do Excel ou um projeto de documento do Word no Visual Studio para que o documento fique visível no designer. Para obter informações sobre como criar projetos [, consulte Como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

2. Na guia **controles comuns** da caixa de **ferramentas**, clique no controle que você deseja adicionar.

3. No documento, clique no local em que você deseja que o canto superior esquerdo do controle seja localizado e arraste para onde você deseja que o canto inferior direito do controle seja localizado.

     O controle é adicionado ao documento com o local e o tamanho especificados.

    > [!NOTE]
    > Ao selecionar um controle no Excel, você verá **= Inserir ("WinForms. Control. host", "")** na **barra de fórmulas**. Esse texto é necessário e não deve ser excluído.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Para adicionar um controle de Windows Forms ao documento clicando uma vez no controle

1. Crie ou abra um projeto de pasta de trabalho do Excel ou um projeto de documento do Word no Visual Studio para que o documento fique visível no designer. Para obter informações sobre como criar projetos [, consulte Como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

2. Na guia **controles comuns** da caixa de **ferramentas**, clique no controle que você deseja adicionar

3. Um documento, clique no local onde você deseja que o controle seja adicionado.

     O controle é adicionado ao documento com o tamanho padrão.

    > [!NOTE]
    > Ao selecionar um controle no Excel, você verá **= Inserir ("WinForms. Control. host", "")** na **barra de fórmulas**. Esse texto é necessário e não deve ser excluído.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Para adicionar um controle de Windows Forms ao documento clicando duas vezes no controle

1. Crie ou abra um projeto de pasta de trabalho do Excel ou um projeto de documento do Word no Visual Studio para que o documento fique visível no designer. Para obter informações sobre como criar projetos [, consulte Como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

2. Na guia **controles comuns** da caixa de **ferramentas**, clique duas vezes no controle que você deseja adicionar.

     O controle é adicionado ao documento no centro do documento ou painel ativo.

    > [!NOTE]
    > Ao selecionar um controle no Excel, você verá **= Inserir ("WinForms. Control. host", "")** na **barra de fórmulas**. Esse texto é necessário e não deve ser excluído.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Para adicionar um controle de Windows Forms ao documento pressionando a tecla Enter

1. Crie ou abra um projeto de pasta de trabalho do Excel ou um projeto de documento do Word no Visual Studio para que o documento fique visível no designer. Para obter informações sobre como criar projetos [, consulte Como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

2. Na guia **controles comuns** da caixa de **ferramentas**, clique no controle que você deseja adicionar e pressione a tecla **Enter** .

     O controle é adicionado ao documento no centro do documento ou painel ativo.

    > [!NOTE]
    > Ao selecionar um controle no Excel, você verá **= Inserir ("WinForms. Control. host", "")** na **barra de fórmulas**. Esse texto é necessário e não deve ser excluído.

## <a name="runtimedoclevel"></a>Adicionar controles em tempo de execução em projetos de nível de documento
 Você pode adicionar com programação Windows Forms controles a um documento em tempo de execução. No Word, use métodos da <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> propriedade `ThisDocument` da classe. No Excel, use métodos da <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> propriedade de uma `Sheet`classe *n* . Cada método tem várias sobrecargas que permitem especificar o local do controle de maneiras diferentes.

 Quando você adiciona um controle de Windows Forms a um documento em tempo de execução, o controle não é persistido no documento quando o documento é fechado. Você pode recriar o controle na próxima vez em que o documento for aberto. Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Para adicionar um controle de Windows Forms em tempo de execução

1. Use um método que tenha o nome adicionar\<*classe de controle*> (em que *classe de controle* é o nome de classe do controle de Windows Forms que você <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>deseja adicionar, como).

     O exemplo de código a seguir demonstra como adicionar <xref:Microsoft.Office.Tools.Excel.Controls.Button> uma a célula C5 `Sheet1` de em um projeto de nível de documento para o Excel.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]

## <a name="runtimeaddin"></a>Adicionar controles em tempo de execução em suplementos do VSTO
 Você pode adicionar Windows Forms controles programaticamente a qualquer documento aberto em tempo de execução. Primeiro, gere um item de host baseado em um documento ou planilha aberta. Em seguida, no Word, use os <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> métodos da Propriedade do novo item de host. No Excel, use métodos da <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> Propriedade do novo item de host. Cada método tem várias sobrecargas que permitem especificar o local do controle de maneiras diferentes.

 Quando você adiciona um controle de Windows Forms a um documento em tempo de execução, o controle não é persistido no documento quando o documento é fechado. Você pode recriar o controle na próxima vez em que o documento for aberto. Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Para obter mais informações sobre como gerar itens de host em projetos de suplemento do VSTO, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Para adicionar um controle de Windows Forms em tempo de execução

1. Use um método que tenha o nome adicionar\<*classe de controle*> (em que *classe de controle* é o nome de classe do controle de Windows Forms que você <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>deseja adicionar, como).

    > [!NOTE]
    > Em projetos de suplemento do VSTO destinados ao [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve adicionar uma referência ao assembly *Microsoft. Office. Tools. Excel. v 4.0. Utilities. dll* ou *Microsoft. Office. Tools. Word. v 4.0. Utilities. dll* antes de poder acessar a adição classe de controle > métodos. \<

     O exemplo de código a seguir demonstra como adicionar <xref:Microsoft.Office.Tools.Word.Controls.Button> um ao primeiro parágrafo do documento ativo usando um suplemento do VSTO do Word.

     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]

## <a name="see-also"></a>Consulte também
- [Visão geral dos controles de Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Como: Redimensionar controles dentro de células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
