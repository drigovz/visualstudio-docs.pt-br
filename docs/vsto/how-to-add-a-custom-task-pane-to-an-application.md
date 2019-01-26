---
title: 'Como: Adicionar um painel de tarefas personalizado a um aplicativo'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24053fcc8918b80e05031739c36059e82ea024a7
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874387"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Como: Adicionar um painel de tarefas personalizado a um aplicativo
  Você pode adicionar um painel de tarefas personalizado para os aplicativos listados acima por meio do suplemento do VSTO. Para obter mais informações, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="add-a-custom-task-pane-to-an-application"></a>Adicionar um painel de tarefas personalizado a um aplicativo  
  
### <a name="to-add-a-custom-task-pane-to-an-application"></a>Para adicionar um painel de tarefas personalizado a um aplicativo  
  
1.  Abra ou crie um projeto de suplemento do VSTO para um dos aplicativos listados acima. Para obter mais informações, confira [Como: Criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Sobre o **Project** menu, clique em **adicionar controle de usuário**.  
  
3.  No **Adicionar Novo Item** diálogo caixa, altere o nome do novo controle de usuário para **MyUserControl**e, em seguida, clique em **adicionar**.  
  
     O controle de usuário é aberto no designer.  
  
4.  Adicionar um ou mais controles de formulários do Windows do **caixa de ferramentas** ao controle de usuário.  
  
5.  Abra o **ThisAddIn.cs** ou **ThisAddIn. vb** arquivo de código.  
  
6.  Adicione o código a seguir à classe `ThisAddIn`. Esse código declara as instâncias de `MyUserControl` e <xref:Microsoft.Office.Tools.CustomTaskPane> como membros do `ThisAddIn` classe.  
  
     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]  
  
7.  Adicione o seguinte código ao manipulador de eventos do `ThisAddIn_Startup`. Esse código cria uma nova <xref:Microsoft.Office.Tools.CustomTaskPane> adicionando o `MyUserControl` do objeto para o `CustomTaskPanes` coleção. O código também exibe o painel de tarefas.  
  
     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
    > [!NOTE]  
    >  Esse código associa o seu painel de tarefas personalizado com a janela ativa no aplicativo. Para alguns aplicativos, você talvez queira modificar este código para garantir que o painel de tarefas é exibida com outros documentos ou itens no aplicativo. Para obter mais informações, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>Consulte também  
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Painéis de tarefas personalizados](../vsto/custom-task-panes.md)   
 [Passo a passo: Automatizar um aplicativo de um painel de tarefas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
