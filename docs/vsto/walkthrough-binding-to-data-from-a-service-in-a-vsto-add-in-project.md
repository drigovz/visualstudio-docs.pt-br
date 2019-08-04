---
title: Associar a dados do serviço no projeto de suplemento do VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 60aefd40c48dc3789ab84ee5873aa6a53f4ee3fe
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68740114"
---
# <a name="walkthrough-bind-to-data-from-a-service-in-a-vsto-add-in-project"></a>Passo a passo: Associar a dados de um serviço em um projeto de suplemento do VSTO
  Você pode associar dados a controles de host em projetos de suplemento do VSTO. Este tutorial demonstra como adicionar controles a um Microsoft Office documento do Word, associar os controles aos dados recuperados do serviço de conteúdo do MSDN e responder a eventos em tempo de execução.

 **Aplica-se a:** As informações neste tópico se aplicam a projetos de nível de aplicativo para o Word 2010. Para obter mais informações, confira [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md) (Funcionalidades disponibilizadas pelo aplicativo do Office e pelo tipo de projeto).

 Esta explicação passo a passo ilustra as seguintes tarefas:

- Adicionar um <xref:Microsoft.Office.Tools.Word.RichTextContentControl> controle a um documento em tempo de execução.

- Ligação do <xref:Microsoft.Office.Tools.Word.RichTextContentControl> controle a dados de um serviço Web.

- Respondendo ao <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> evento de um <xref:Microsoft.Office.Tools.Word.RichTextContentControl> controle.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Pré-requisitos
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-project"></a>Criar um novo projeto
 A primeira etapa é criar um projeto de suplemento do VSTO do Word.

### <a name="to-create-a-new-project"></a>Para criar um novo projeto

1. Crie um projeto de suplemento do VSTO do Word com o nome **MTPS Content Service**, usando Visual Basic ou C#.

     Para obter mais informações, confira [Como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

     O Visual Studio abre `ThisAddIn.vb` o `ThisAddIn.cs` arquivo ou e adiciona o projeto a **Gerenciador de soluções**.

## <a name="add-a-web-service"></a>Adicionar um serviço Web
 Para esta explicação, use um serviço Web chamado serviço de conteúdo MTPS. Esse serviço Web retorna informações de um artigo do MSDN especificado na forma de uma cadeia de caracteres XML ou texto sem formatação. Uma etapa posterior mostra como exibir as informações retornadas em um controle de conteúdo.

### <a name="to-add-the-mtps-content-service-to-the-project"></a>Para adicionar o serviço de conteúdo MTPS ao projeto

1. No menu **Dados**, clique em **Adicionar Nova Fonte de Dados**.

2. No **Assistente de configuração da fonte de dados**, clique em **serviço**e em **Avançar**.

3. No campo **endereço** , digite a seguinte URL:

     **http:\//Services.msdn.Microsoft.com/ContentServices/ContentService.asmx**

4. Clique em **ir**.

5. No campo **namespace** , digite **ContentService**e clique em **OK**.

6. Na caixa de diálogo **Assistente de adição de referência** , clique em **concluir**.

## <a name="add-a-content-control-and-bind-to-data-at-runtime"></a>Adicionar um controle de conteúdo e associar a dados em tempo de execução
 Em projetos de suplemento do VSTO, você adiciona e associa controles em tempo de execução. Para esta explicação, configure o controle de conteúdo para recuperar dados do serviço Web quando um usuário clicar dentro do controle.

### <a name="to-add-a-content-control-and-bind-to-data"></a>Para adicionar um controle de conteúdo e associar a dados

1. `ThisAddIn` Na classe, declare as variáveis para o serviço de conteúdo MTPS, o controle de conteúdo e a associação de dados.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#2)]

2. Adicione o seguinte método à classe `ThisAddIn`. Esse método cria um controle de conteúdo no início do documento ativo.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#4)]

3. Adicione o seguinte método à classe `ThisAddIn`. Esse método inicializa os objetos necessários para criar e enviar uma solicitação para o serviço Web.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#6)]

4. Crie um manipulador de eventos para recuperar o documento da biblioteca MSDN sobre controles de conteúdo quando um usuário clicar dentro do controle de conteúdo e associar os dados ao controle de conteúdo.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#5)]

5. Chame os `AddRichTextControlAtRange` métodos `InitializeServiceObjects` e do `ThisAddIn_Startup` método. Para C# programadores, adicione um manipulador de eventos.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#3)]

## <a name="test-the-add-in"></a>Testar o suplemento
 Quando você abre o Word, <xref:Microsoft.Office.Tools.Word.RichTextContentControl> o controle é exibido. O texto no controle é alterado quando você clica dentro dele.

### <a name="to-test-the-vsto-add-in"></a>Para testar o suplemento do VSTO

1. Pressione **F5**.

2. Clique dentro do controle de conteúdo.

     As informações são baixadas do serviço de conteúdo do MTPS e exibidas dentro do controle de conteúdo.

## <a name="see-also"></a>Consulte também
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
