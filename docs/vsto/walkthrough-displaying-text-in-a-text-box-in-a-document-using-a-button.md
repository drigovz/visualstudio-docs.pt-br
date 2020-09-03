---
title: Exibir texto na caixa de texto no documento usando o botão
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f3c467abcee8fb4faafd2da06ba261e7f3039fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328746"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Walkthrough: exibir texto em uma caixa de texto em um documento usando um botão
  Este tutorial demonstra como usar botões e caixas de texto em uma personalização em nível de documento para Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Este passo a passo ilustra as seguintes tarefas:

- Adicionar controles ao documento do Word em um projeto de nível de documento em tempo de design.

- Populando uma caixa de texto quando um botão é clicado.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Pré-requisitos
 Você precisará dos seguintes componentes para concluir este passo a passo:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Criar o projeto
 A primeira etapa é criar um projeto de Documento do Word.

### <a name="to-create-a-new-project"></a>Para criar um novo projeto

1. Crie um projeto de documento do Word com o **botão nome My Word**. No assistente, selecione **criar um novo documento**.

     Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     O Visual Studio abre o novo documento do Word no designer e adiciona o projeto de **botão meu Word** a **Gerenciador de soluções**.

## <a name="add-controls-to-the-word-document"></a>Adicionar controles ao documento do Word
 Os controles da interface do usuário consistem em um botão e uma caixa de texto no documento do Word.

### <a name="to-add-a-button-and-a-text-box"></a>Para adicionar um botão e uma caixa de texto

1. Verifique se o documento está aberto no designer do Visual Studio.

2. Na guia **controles comuns** da caixa de **ferramentas**, arraste um <xref:Microsoft.Office.Tools.Word.Controls.TextBox> controle para o documento.

   > [!NOTE]
   > No Word, os controles são descartados em linha com texto por padrão. Você pode modificar o modo como os controles e objetos de forma são inseridos alterando o padrão na guia **Editar** da caixa de diálogo **Opções** no Word.

3. No menu **Exibir** , clique em **Janela Propriedades**.

4. Localize **TextBox1** na caixa suspensa janela de **Propriedades** e altere a propriedade **Name** da caixa de texto para **exibirtexto**.

5. Arraste um controle de **botão** para o documento e altere as propriedades a seguir.

   |Propriedade|Valor|
   |--------------|-----------|
   |**Nome**|**insertText**|
   |**Text**|**Inserir texto**|

   Agora você pode escrever o código que será executado quando o botão for clicado.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Preencher a caixa de texto quando o botão for clicado
 Toda vez que o usuário clica no botão, **Olá, mundo!** é adicionado à caixa de texto.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Para gravar na caixa de texto quando o botão é clicado

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse em **ThisDocument**e clique em **Exibir código** no menu de atalho.

2. Adicione o código a seguir ao <xref:System.Windows.Forms.Control.Click> manipulador de eventos do botão.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]

3. No C#, você deve adicionar um manipulador de eventos para o botão ao <xref:Microsoft.Office.Tools.Word.Document.Startup> evento. Para obter informações sobre como criar manipuladores de eventos, consulte [como criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]

## <a name="test-the-application"></a>Testar o aplicativo
 Agora você pode testar seu documento para certificar-se de que a mensagem **Olá, mundo!** aparece na caixa de texto quando você clica no botão.

### <a name="to-test-your-document"></a>Para testar o documento

1. Pressione **F5** para executar o projeto.

2. Clique no botão.

3. Confirme se **Olá, mundo!** aparece na caixa de texto.

## <a name="next-steps"></a>Próximas etapas
 Este tutorial mostra as noções básicas de como usar botões e caixas de texto em documentos do Word. Estas são algumas tarefas que podem vir a seguir:

- Usando uma caixa de combinação para alterar a formatação. Para obter mais informações, consulte [Walkthrough: alterar a formatação do documento usando controles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

- Usando botões de opção para selecionar estilos de gráfico. Para obter mais informações, consulte [Walkthrough: atualizar um gráfico em um documento usando botões de opção](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Confira também
- [Visão geral dos controles de Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Passo a passos usando o Word](../vsto/walkthroughs-using-word.md)
- [Exemplos e orientações de desenvolvimento do Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Como: adicionar controles de Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
