---
title: Visão geral do painel Ações
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6cbade56f80d75e6ab8d735aaf586d45d2dedb42
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926678"
---
# <a name="actions-pane-overview"></a>Visão geral do painel Ações
  Um painel Ações é um painel de tarefas de **ações de documento** personalizável que é anexado a um documento do Word Microsoft Office específico ou Microsoft Office pasta de trabalho do Excel. O painel Ações é hospedado no painel de tarefas do Office junto com outros painéis de tarefas internos, como o painel de tarefas **origem XML** no Excel ou o painel de tarefas **estilos e formatação** no Word. Você pode usar controles de Windows Forms ou controles WPF para criar a interface do usuário do painel Ações.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Você pode criar um painel de ações somente em uma personalização no nível do documento do Word ou Excel. Você não pode criar um painel de ações em um suplemento do VSTO. Para obter mais informações, consulte [recursos disponíveis por aplicativo do Office e tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> O painel Ações difere dos painéis de tarefas personalizados. Os painéis de tarefas personalizados são associados ao aplicativo, não a um documento específico. Você pode criar painéis de tarefas personalizados em suplementos do VSTO para alguns Microsoft Office aplicativos. Para obter mais informações, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).

 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") Para ver uma demonstração de vídeo relacionada [, consulte Como fazer: Usar controles WPF dentro de um painel de ações do Excel? ](http://go.microsoft.com/fwlink/?LinkId=132763).

## <a name="display-the-actions-pane"></a>Exibir o painel Ações
 O painel Ações é representado pela <xref:Microsoft.Office.Tools.ActionsPane> classe. Quando você cria um projeto de nível de documento, uma instância dessa classe está disponível para seu código usando o `ActionsPane` campo `ThisWorkbook` da classe (para Excel) ou `ThisDocument` (para Word) em seu projeto. Para exibir o painel Ações, adicione um controle de Windows Forms à <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propriedade `ActionsPane` do campo. O exemplo de código a seguir adiciona um `actions` controle chamado ao painel Ações.

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

 O painel Ações torna-se visível no tempo de execução assim que você adiciona explicitamente um controle a ele. Depois que o painel Ações for exibido, você poderá adicionar ou remover dinamicamente os controles em resposta às ações do usuário. Normalmente, você adiciona o código para exibir o painel Ações no `Startup` manipulador de eventos do `ThisDocument` ou `ThisWorkbook` para que o painel Ações fique visível quando o usuário abrir o documento pela primeira vez. No entanto, talvez você queira exibir o painel Ações somente em resposta à ação de um usuário no documento. Por exemplo, você pode adicionar o código ao `Click` evento de um controle no documento.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Adicionar vários controles ao painel Ações
 Quando você adiciona vários controles ao painel Ações, deve agrupar os controles em um controle de usuário e, em seguida, adicionar o controle de <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> usuário à propriedade. Esse processo inclui as seguintes etapas:

1. Crie a interface do usuário (IU) do painel Ações adicionando um **controle painel de ações** ou um item de **controle de usuário** ao seu projeto. Ambos os dois itens incluem uma classe de <xref:System.Windows.Forms.UserControl> Windows Forms personalizada. O **controle do painel Ações** e os itens de **controle de usuário** são equivalentes; a única diferença é seu nome.

2. Adicione controles de Windows Forms ao <xref:System.Windows.Forms.UserControl> usando o designer ou escrevendo código.

   > [!NOTE]
   > Você também pode adicionar controles WPF ao painel Ações adicionando um WPF <xref:System.Windows.Controls.UserControl> ao Windows Forms. <xref:System.Windows.Forms.UserControl> Para obter mais informações, consulte [usar controles WPF em soluções do Office](../vsto/using-wpf-controls-in-office-solutions.md).

3. Adicione uma instância do controle de usuário personalizado aos controles contidos no `ActionsPane` campo `ThisWorkbook` da classe (para Excel) ou `ThisDocument` (para Word) em seu projeto.

   Para obter exemplos que demonstram esse processo mais detalhadamente [, consulte Como: Adicione um painel ações a documentos do Word ou a pastas](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)de trabalho do Excel.

## <a name="hide-the-actions-pane"></a>Ocultar o painel Ações
 Embora a <xref:Microsoft.Office.Tools.ActionsPane> classe tenha um <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> método e uma <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> Propriedade, você não pode remover o painel ações da interface do <xref:Microsoft.Office.Tools.ActionsPane> usuário usando todos os membros da própria classe. Chamar o <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> método ou definir a <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> Propriedade como **false** oculta somente os controles no painel Ações; ele não oculta o painel de tarefas.

 Para ocultar o painel de tarefas em sua solução, você tem várias opções:

- Para o Word, defina <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> a propriedade <xref:Microsoft.Office.Interop.Word.TaskPane> do objeto que representa o painel de tarefas ações do documento como **falso**. O exemplo de código a seguir deve ser executado da `ThisDocument` classe em seu projeto.

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]

- Para o Excel, defina <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> a propriedade <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> do objeto como **false**. O exemplo de código a seguir deve ser executado da `ThisWorkbook` classe em seu projeto.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]

- Para o Word ou Excel, você pode definir como alternativa <xref:Microsoft.Office.Core.CommandBar.Visible%2A> a propriedade da barra de comandos que representa o painel de tarefas como **false**. O exemplo de código a seguir deve ser executado a `ThisDocument` partir da classe ou `ThisWorkbook` no seu projeto.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Limpar o painel ações quando o documento é aberto
 Quando um usuário salva o documento enquanto o painel Ações está visível, o painel Ações fica visível toda vez que o documento é aberto, independentemente de o painel Ações conter ou não controles. Se você quiser controlar quando ele aparece, chame o <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> método `ActionsPane` do campo no `Startup` manipulador de eventos do `ThisDocument` ou `ThisWorkbook` para garantir que o painel ações não esteja visível quando o documento for aberto.

### <a name="determine-when-the-actions-pane-is-closed"></a>Determinar quando o painel de ações é fechado
 Não há evento que seja gerado quando o painel Ações for fechado. Embora a <xref:Microsoft.Office.Tools.ActionsPane> classe tenha um <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> evento, esse evento não é gerado quando o usuário final fecha o painel Ações. Em vez disso, esse evento é gerado quando os controles no painel ações são ocultados chamando <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> o método ou definindo a <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> Propriedade como **false**.

 Quando o usuário fecha o painel Ações, o usuário pode exibi-lo novamente executando um dos procedimentos a seguir na interface do usuário do aplicativo.

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Para exibir o painel ações usando a interface do usuário do Word ou Excel

1. Na faixa de visão, clique na guia **Exibir** .

2. No grupo **Mostrar/ocultar** , clique no botão de alternância **ações do documento** .

## <a name="program-actions-pane-events"></a>Eventos do painel Ações do programa
 Você pode adicionar vários controles de usuário ao painel Ações e, em seguida, escrever código para responder a eventos no documento mostrando e ocultando os controles de usuário. Se você mapear elementos de esquema XML para o documento, poderá mostrar determinados controles de usuário no painel ações sempre que o ponto de inserção estiver dentro de um dos elementos XML. Para obter mais informações, confira [Como: Mapeie esquemas para documentos do Word dentro do Visual](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) Studio [e como: Mapeie esquemas para planilhas dentro do Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).

 Você também pode escrever código para responder aos eventos de qualquer objeto, incluindo eventos de controle de host, aplicativo ou documento. Para obter mais informações, confira [Passo a passo: Programar contra eventos de um controle](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)NamedRange.

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Associar dados a controles no painel Ações
 Os controles no painel Ações têm os mesmos recursos de vinculação de dados que os controles em Windows Forms. Você pode associar os controles a fontes de dados, como conjuntos de dados, conjuntos de dados tipados e XML. Para obter mais informações, consulte [vinculação de dados e Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 Você pode associar controles no painel Ações e controles no documento para o mesmo conjunto de mesmos. Por exemplo, você pode criar uma relação de mestre/detalhes entre os controles no painel Ações e os controles na planilha. Para obter mais informações, confira [Passo a passo: Associar dados a controles em um painel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)de ações do Excel.

## <a name="validate-data-in-actions-pane-controls"></a>Validar dados em controles do painel Ações
 Se você exibir uma caixa de mensagem no <xref:System.Windows.Forms.Control.Validating> manipulador de eventos de um controle no painel Ações, o evento poderá ser gerado uma segunda vez quando o foco for movido do controle para a caixa de mensagem. Para evitar esse problema, use um <xref:System.Windows.Forms.ErrorProvider> controle para exibir todas as mensagens de erro de validação.

## <a name="user-control-stacking-order"></a>Ordem de empilhamento de controle de usuário
 Se você estiver usando vários controles de usuário, poderá escrever código para empilhar corretamente os controles de usuário no painel ações se ele estiver encaixado verticalmente ou horizontalmente. Você pode definir a ordem de empilhamento dos controles de usuário no painel ações usando a <xref:Microsoft.Office.Tools.StackStyle> enumeração <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> da propriedade. Para obter mais informações, confira [Como: Gerencie o layout de controle em](../vsto/how-to-manage-control-layout-on-actions-panes.md)painéis de ações.

 A <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> propriedade pode assumir os valores <xref:Microsoft.Office.Tools.StackStyle> de enumeração a seguir.

|Estilo de empilhamento|Definição|
|--------------------|----------------|
|FromBottom|Empilhar na parte inferior do painel de ações.|
|FromLeft|Empilhar na parte esquerda do painel de ações.|
|FromRight|Empilhar na parte direita do painel de ações.|
|FromTop|Empilhar na parte superior do painel de ações.|
|Nenhum|Nenhuma ordem de empilhamento definida, a ordem é controlada pelo desenvolvedor.|

 O código a seguir define <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> a propriedade para empilhar os controles de usuário da parte superior do painel Ações.

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]

## <a name="anchor-controls"></a>Controles de âncora
 Se o usuário redimensionar o painel Ações em tempo de execução, os controles poderão ser redimensionados com o painel Ações. Você pode usar a <xref:System.Windows.Forms.Control.Anchor%2A> propriedade de um controle de Windows Forms para ancorar controles no painel Ações. Você também pode ancorar os controles de Windows Forms no controle de usuário da mesma maneira. Para obter mais informações, confira [Como: Controles de ancoragem](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)em Windows Forms.

## <a name="resize-the-actions-pane"></a>Redimensionar o painel Ações
 Não é possível alterar diretamente o tamanho de <xref:Microsoft.Office.Tools.ActionsPane> um porque <xref:Microsoft.Office.Tools.ActionsPane> o está inserido no painel de tarefas. No entanto, você pode alterar programaticamente a largura do painel de <xref:Microsoft.Office.Core.CommandBar.Width%2A> tarefas definindo a <xref:Microsoft.Office.Core.CommandBar> Propriedade do que representa o painel de tarefas. Você pode alterar a altura do painel de tarefas se ele estiver encaixado horizontalmente ou flutuando.

 O redimensionamento programático do painel de tarefas não é recomendado porque o usuário deve ser capaz de selecionar o tamanho do painel de tarefas que melhor atenda às suas necessidades. No entanto, se for necessário redimensionar a largura do painel de tarefas, você poderá usar o código a seguir para obter essa tarefa.

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]

## <a name="reposition-the-actions-pane"></a>Reposicionar o painel Ações
 Não é possível reposicionar <xref:Microsoft.Office.Tools.ActionsPane> diretamente o porque ele está inserido no painel de tarefas. No entanto, você pode mover o painel de tarefas programaticamente definindo <xref:Microsoft.Office.Core.CommandBar> a <xref:Microsoft.Office.Core.CommandBar.Position%2A> Propriedade do que representa o painel de tarefas.

 O reposicionamento programático do painel de tarefas não é recomendado porque o usuário deve ser capaz de escolher a posição do painel de tarefas na tela que melhor atenda às suas necessidades. No entanto, se for necessário mover o painel de tarefas para uma determinada posição, você poderá usar o código a seguir para obter essa tarefa.

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]

> [!NOTE]
> Os usuários finais podem reposicionar manualmente o painel de tarefas a qualquer momento. Não há como garantir que o painel de tarefas permanecerá encaixado na posição que você indicar programaticamente. No entanto, você pode verificar se há alterações de orientação e garantir que os controles no painel ações sejam empilhados na direção correta. Para obter mais informações, confira [Como: Gerencie o layout de controle em](../vsto/how-to-manage-control-layout-on-actions-panes.md)painéis de ações.

 Definir as <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> propriedades <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> e de <xref:Microsoft.Office.Tools.ActionsPane> não altera sua posição porque o <xref:Microsoft.Office.Tools.ActionsPane> objeto está inserido no painel de tarefas.

 Se o painel de tarefas não estiver encaixado, você poderá <xref:Microsoft.Office.Core.CommandBar.Top%2A> definir <xref:Microsoft.Office.Core.CommandBar.Left%2A> as propriedades e <xref:Microsoft.Office.Core.CommandBar> do que representa o painel de tarefas. O código a seguir move um painel de tarefas desencaixado para o canto superior esquerdo do documento.

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]

## <a name="see-also"></a>Consulte também
- [Usar controles WPF em soluções do Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)
- [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Como: Adicionar um painel de ações a documentos do Word ou a pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Passo a passo: Inserir texto em um documento a partir de um painel Ações](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Passo a passo: Associar dados a controles em um painel de ações do Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)
- [Passo a passo: Associar dados a controles em um painel de ações do Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)
- [Como: Gerenciar o layout de controle em painéis de ações](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Passo a passo: Inserir texto em um documento a partir de um painel Ações](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
