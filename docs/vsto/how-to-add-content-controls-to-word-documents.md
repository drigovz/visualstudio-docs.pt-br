---
title: 'Como: Adicionar controles de conteúdo a documentos do Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c84ae02bd2cafde7b6232c73bc75f0976e81bd0
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254361"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Como: Adicionar controles de conteúdo a documentos do Word
  Em projetos de palavras em nível de documento, você pode adicionar controles de conteúdo ao documento em seu projeto em tempo de design ou em tempo de execução. Em projetos de suplemento do VSTO do Word, você pode adicionar controles de conteúdo a qualquer documento aberto em tempo de execução.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Este tópico descreve as seguintes tarefas:

- [Adicionar controles de conteúdo em tempo de design](#designtime)

- [Adicionar controles de conteúdo em tempo de execução em um projeto de nível de documento](#runtimedoclevel)

- [Adicionar controles de conteúdo em tempo de execução em um projeto de suplemento do VSTO](#runtimeaddin)

  Para obter informações sobre controles de conteúdo, consulte [controles de conteúdo](../vsto/content-controls.md).

## <a name="designtime"></a>Adicionar controles de conteúdo em tempo de design
 Há várias maneiras de adicionar controles de conteúdo ao documento em um projeto de nível de documento em tempo de design:

- Adicione um controle de conteúdo da guia **controles do Word** da **caixa de ferramentas**.

- Adicione um controle de conteúdo ao seu documento da mesma maneira que você adicionaria um controle de conteúdo nativo no Word.

- Arraste um controle de conteúdo para seu documento na janela **fontes de dados** . Isso é útil quando você deseja associar o controle aos dados quando o controle é criado. Para obter mais informações, confira [Como: Preencha documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md) e [como: Preencha documentos com dados de um banco](../vsto/how-to-populate-documents-with-data-from-a-database.md)de dado.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Para adicionar um controle de conteúdo a um documento usando a caixa de ferramentas

1. No documento hospedado no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer, coloque o cursor onde você deseja adicionar o controle de conteúdo ou selecione o texto que você deseja que o controle de conteúdo substitua.

2. Abra a **caixa de ferramentas** e clique na guia **controles do Word** .

3. Adicione o controle de uma das seguintes maneiras:

    - Clique duas vezes em um controle de conteúdo na **caixa de ferramentas**.

         ou

    - Clique em um controle de conteúdo na **caixa de ferramentas** e pressione a tecla **Enter** .

         ou

    - Arraste um controle de conteúdo da **caixa de ferramentas** para o documento. O controle de conteúdo é adicionado na seleção atual no documento, não no local do ponteiro do mouse.

> [!NOTE]
> Você não pode adicionar <xref:Microsoft.Office.Tools.Word.GroupContentControl> um usando a **caixa de ferramentas**. Você só pode adicionar um <xref:Microsoft.Office.Tools.Word.GroupContentControl> no Word ou em tempo de execução.

> [!NOTE]
> O Visual Studio não fornece um controle de conteúdo de caixa de seleção na Toolbox. Para adicionar um controle de conteúdo de caixa de seleção ao documento, você deve <xref:Microsoft.Office.Tools.Word.ContentControl> criar um objeto programaticamente. Para obter mais informações, consulte [controles de conteúdo](../vsto/content-controls.md).

#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Para adicionar um controle de conteúdo a um documento no Word

1. No documento hospedado no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer, coloque o cursor onde você deseja adicionar o controle de conteúdo ou selecione o texto que você deseja que o controle de conteúdo substitua.

2. Na faixa de faixas, clique na guia **desenvolvedor** .

    > [!NOTE]
    > Se a guia **desenvolvedor** não estiver visível, você deverá primeiro mostrá-la. Para obter mais informações, confira [Como: Mostre a guia Desenvolvedor na faixa de](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)faixas.

3. No grupo **controles** , clique no ícone do controle de conteúdo que você deseja adicionar.

## <a name="runtimedoclevel"></a>Adicionar controles de conteúdo em tempo de execução em um projeto de nível de documento
 Você pode adicionar controles de conteúdo programaticamente ao seu documento em tempo de execução usando <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> métodos da propriedade `ThisDocument` da classe em seu projeto. Cada método tem três sobrecargas que você pode usar para adicionar um controle de conteúdo das seguintes maneiras:

- Adicionar um controle na seleção atual.

- Adicione um controle em um intervalo especificado.

- Adicione um controle baseado em um controle de conteúdo nativo no documento.

  Controles de conteúdo criados dinamicamente não são persistidos no documento quando o documento é fechado. No entanto, um controle de conteúdo nativo permanece no documento. Você pode recriar um controle de conteúdo baseado em um controle de conteúdo nativo na próxima vez em que o documento for aberto. Para obter mais informações, consulte [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).

> [!NOTE]
> Para adicionar um controle de conteúdo de caixa de seleção a um documento em um projeto do Word 2010, <xref:Microsoft.Office.Tools.Word.ContentControl> você deve criar um objeto. Para obter mais informações, consulte [controles de conteúdo](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Para adicionar um controle de conteúdo na seleção atual

1. Use um <xref:Microsoft.Office.Tools.Word.ControlCollection> método que tenha a classe `Add`de *controle*de nome \<> (em que *classe de controle* é o nome de classe <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>do controle de conteúdo que você deseja adicionar, como), e que tem um único parâmetro para o nome do novo controle.

     O exemplo de código a seguir <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> usa o método para adicionar <xref:Microsoft.Office.Tools.Word.RichTextContentControl> um novo no início do documento. Para executar esse código, adicione o código à `ThisDocument` classe em seu projeto e chame o `AddRichTextControlAtSelection` método do `ThisDocument_Startup` manipulador de eventos.

     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]

### <a name="to-add-a-content-control-at-a-specified-range"></a>Para adicionar um controle de conteúdo em um intervalo especificado

1. Use um <xref:Microsoft.Office.Tools.Word.ControlCollection> método que tenha a classe `Add`de *controle*de nome \<> (em que *classe de controle* é o nome da classe de controle de conteúdo que você deseja <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>adicionar, como) e que <xref:Microsoft.Office.Interop.Word.Range> tem um meter.

     O exemplo de código a seguir <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> usa o método para adicionar <xref:Microsoft.Office.Tools.Word.RichTextContentControl> um novo no início do documento. Para executar esse código, adicione o código à `ThisDocument` classe em seu projeto e chame o `AddRichTextControlAtRange` método do `ThisDocument_Startup` manipulador de eventos.

     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]

### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Para adicionar um controle de conteúdo baseado em um controle de conteúdo nativo

1. Use um <xref:Microsoft.Office.Tools.Word.ControlCollection> método que tenha a classe `Add`de *controle*de nome \<> (em que *classe de controle* é o nome da classe de controle de conteúdo que você deseja <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>adicionar, como) e que `Microsoft.Office.Interop.Word.ContentControl` tem um meter.

     O exemplo de código a seguir <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> usa o método para criar <xref:Microsoft.Office.Tools.Word.RichTextContentControl> um novo para cada controle de Rich Text nativo que está no documento. Para executar esse código, adicione o código à `ThisDocument` classe em seu projeto e chame o `CreateRichTextControlsFromNativeControls` método do `ThisDocument_Startup` manipulador de eventos.

     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]

## <a name="runtimeaddin"></a>Adicionar controles de conteúdo em tempo de execução em um projeto de suplemento do VSTO
 Você pode adicionar controles de conteúdo programaticamente a qualquer documento aberto em tempo de execução usando um suplemento do VSTO. Para fazer isso, gere um <xref:Microsoft.Office.Tools.Word.Document> item de host baseado em um documento aberto e, em seguida, use os <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> métodos da propriedade desse item de host. Cada método tem três sobrecargas que você pode usar para adicionar um controle de conteúdo das seguintes maneiras:

- Adicionar um controle na seleção atual.

- Adicione um controle em um intervalo especificado.

- Adicione um controle baseado em um controle de conteúdo nativo no documento.

  Controles de conteúdo criados dinamicamente não são persistidos no documento quando o documento é fechado. No entanto, um controle de conteúdo nativo permanece no documento. Você pode recriar um controle de conteúdo baseado em um controle de conteúdo nativo na próxima vez em que o documento for aberto. Para obter mais informações, consulte [manter controles dinâmicos em documentos do Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

  Para obter mais informações sobre como gerar itens de host em projetos de suplemento do VSTO, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

> [!NOTE]
> Para adicionar um controle de conteúdo de caixa de seleção a um documento, você <xref:Microsoft.Office.Tools.Word.ContentControl> deve criar um objeto. Para obter mais informações, consulte [controles de conteúdo](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Para adicionar um controle de conteúdo na seleção atual

1. Use um <xref:Microsoft.Office.Tools.Word.ControlCollection> método que tenha a classe `Add`de *controle*de nome \<> (em que *classe de controle* é o nome de classe <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>do controle de conteúdo que você deseja adicionar, como), e que tem um único parâmetro para o nome do novo controle.

     O exemplo de código a seguir <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> usa o método para adicionar <xref:Microsoft.Office.Tools.Word.RichTextContentControl> um novo no início do documento ativo. Para executar esse código, adicione o código à `ThisAddIn` classe em seu projeto e chame o `AddRichTextControlAtSelection` método do `ThisAddIn_Startup` manipulador de eventos.

     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]

### <a name="to-add-a-content-control-at-a-specified-range"></a>Para adicionar um controle de conteúdo em um intervalo especificado

1. Use um <xref:Microsoft.Office.Tools.Word.ControlCollection> método que tenha a classe `Add`de *controle*de nome \<> (em que *classe de controle* é o nome da classe de controle de conteúdo que você deseja <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>adicionar, como) e que <xref:Microsoft.Office.Interop.Word.Range> tem um meter.

     O exemplo de código a seguir <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> usa o método para adicionar <xref:Microsoft.Office.Tools.Word.RichTextContentControl> um novo no início do documento ativo. Para executar esse código, adicione o código à `ThisAddIn` classe em seu projeto e chame o `AddRichTextControlAtRange` método do `ThisAddIn_Startup` manipulador de eventos.

     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]

#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Para adicionar um controle de conteúdo baseado em um controle de conteúdo nativo

1. Use um <xref:Microsoft.Office.Tools.Word.ControlCollection> método que tenha a classe `Add`de *controle*de nome \<> (em que *classe de controle* é o nome da classe de controle de conteúdo que você deseja <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>adicionar, como) e que `Microsoft.Office.Interop.Word.ContentControl` tem um meter.

     O exemplo de código a seguir <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> usa o método para criar <xref:Microsoft.Office.Tools.Word.RichTextContentControl> um novo para cada controle de Rich Text nativo que está em um documento, depois que o documento é aberto. Para executar esse código, adicione o código à `ThisAddIn` classe em seu projeto.

     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]

     Para C# `Application_DocumentOpen` o<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> , você também deve anexar o manipulador de eventos ao evento.

     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]

## <a name="see-also"></a>Consulte também
- [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Adicionar controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)
- [Programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md)
