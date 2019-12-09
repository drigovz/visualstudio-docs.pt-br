---
title: 'Como: Gerenciar o layout de controle em painéis de ações'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 043f93c12181d34e9d2a92435c854cdf76f18904
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255818"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Como: Gerenciar o layout de controle em painéis de ações
  Um painel Ações é encaixado à direita de um documento ou planilha por padrão; no entanto, ele pode ser encaixado à esquerda, à parte superior ou inferior. Se você estiver usando vários controles de usuário, poderá escrever código para empilhar corretamente os controles de usuário no painel Ações. Para obter mais informações, consulte [visão geral do painel Ações](../vsto/actions-pane-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 A ordem de pilha dos controles depende se o painel Ações está encaixado verticalmente ou horizontalmente.

> [!NOTE]
> Se o usuário redimensionar o painel Ações em tempo de execução, você poderá definir os controles a serem redimensionados com o painel Ações. Você pode usar a <xref:System.Windows.Forms.Control.Anchor%2A> propriedade de um controle de Windows Forms para ancorar controles no painel Ações. Para obter mais informações, confira [Como: Controles de ancoragem](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)em Windows Forms.

> [!NOTE]
> Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Para definir a ordem de pilha dos controles do painel Ações

1. Abra um projeto de nível de documento para Microsoft Office Word que inclui um painel Ações com vários controles de usuário ou controles do painel Ações aninhadas. Para obter mais informações, confira [Como: Adicione um painel ações a documentos do Word ou a pastas](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)de trabalho do Excel.

2. Clique com o botão direito do mouse em **ThisDocument.cs** ou **ThisDocument. vb** em **Gerenciador de soluções** e clique em **Exibir código**.

3. No manipulador de eventos do painel Ações, verifique se a orientação do painel Ações é horizontal. <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged>

     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]

4. Se a orientação for horizontal, empilhe os controles do painel de ação da esquerda; caso contrário, empilhe-os da parte superior.

     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]

5. No C#, você deve adicionar um manipulador de eventos para `ActionsPane` o para <xref:Microsoft.Office.Tools.Word.Document.Startup> o manipulador de eventos. Para obter informações sobre como criar manipuladores de [eventos, consulte Como: Crie manipuladores de eventos em projetos](../vsto/how-to-create-event-handlers-in-office-projects.md)do Office.

     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]

6. Execute o projeto e verifique se os controles do painel ações estão empilhados da esquerda para a direita quando o painel Ações está encaixado na parte superior do documento, e os controles são empilhados de cima para baixo quando o painel Ações é encaixado no lado direito do documento.

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer:

- Um projeto de nível de documento do Word com um painel ações que contém vários controles de usuário ou controles de painel de ações aninhadas.

## <a name="see-also"></a>Consulte também
- [Visão geral do painel Ações](../vsto/actions-pane-overview.md)
- [Como: Adicionar um painel de ações a documentos do Word ou a pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Como: Adicionar um painel de ações a documentos do Word ou a pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Passo a passo: Inserir texto em um documento a partir de um painel Ações](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Passo a passo: Inserir texto em um documento a partir de um painel Ações](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
