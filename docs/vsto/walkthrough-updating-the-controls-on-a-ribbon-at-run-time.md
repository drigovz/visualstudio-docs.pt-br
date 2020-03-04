---
title: 'Passo a passo: Atualizar os controles em uma faixa de faixas em tempo de execução'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 425918ea32c14e6ba905d6b32864a2844d2b5a90
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255344"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>Passo a passo: Atualizar os controles em uma faixa de faixas em tempo de execução

Este tutorial demonstra como usar o modelo de objeto Ribbon para atualizar os controles em uma faixa de faixas depois que a faixa de faixas é carregada no aplicativo do Office.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

O exemplo extrai dados do banco de dado de exemplo Northwind para preencher uma caixa de combinação e um menu no Microsoft Office Outlook. Os itens que você selecionar nesses controles preencherão automaticamente campos como **para** e **assunto** em uma mensagem de email.

Esta explicação passo a passo ilustra as seguintes tarefas:

- Crie um novo projeto de suplemento do VSTO do Outlook.

- Crie um grupo de faixas de faixa personalizado.

- Adicione o grupo personalizado a uma guia interna.

- Atualizar controles na faixa de faixas em tempo de execução.

> [!NOTE]
> Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisites

Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Criar um novo projeto de suplemento do VSTO do Outlook

Primeiro, crie um projeto de suplemento do VSTO do Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Para criar um novo projeto de suplemento do VSTO do Outlook

1. No [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], crie um projeto de suplemento do VSTO do Outlook com o nome **Ribbon_Update_At_Runtime**.

2. Na caixa de diálogo **novo projeto** , selecione **criar diretório para solução**.

3. Salve o projeto no diretório de projeto padrão.

     Para obter mais informações, confira [Como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

## <a name="design-a-custom-ribbon-group"></a>Criar um grupo de faixa de uma personalizada

A faixa de para este exemplo aparecerá quando um usuário compor uma nova mensagem de email. Para criar um grupo personalizado para a faixa de faixas, primeiro adicione um item da faixa de uma ao seu projeto e, em seguida, crie o grupo no designer de faixa de faixas. Esse grupo personalizado ajudará você a gerar mensagens de email de acompanhamento para clientes ao extrair nomes e ordenar históricos de um banco de dados.

### <a name="to-design-a-custom-group"></a>Para criar um grupo personalizado

1. No menu **Projeto**, clique em **Adicionar Novo Item**.

2. Na caixa de diálogo **Adicionar novo item** , selecione **faixa de opções (designer visual)** .

3. Altere o nome da nova faixa de forma para **CustomerRibbon**e clique em **Adicionar**.

     O arquivo *CustomerRibbon.cs* ou *CustomerRibbon. vb* é aberto no designer de faixa de faixas e exibe uma guia e um grupo padrão.

4. Clique no designer de faixa de opções para selecioná-lo.

5. Na janela **Propriedades** , clique na seta suspensa ao lado da propriedade **RibbonType** e, em seguida, clique em **Microsoft. Outlook. mail. Compose**.

     Isso permite que a faixa de faixas apareça quando o usuário compõe uma nova mensagem de email no Outlook.

6. No designer de faixa de opções, clique em **grupo1** para selecioná-lo.

7. Na janela **Propriedades** , defina **rótulo** como **compras do cliente**.

8. Na guia **controles da faixa** de ferramentas do Office, arraste uma **caixa**de **combinação** para o grupo **compras do cliente** .

9. Clique em **comboBox1** para selecioná-lo.

10. Na janela **Propriedades** , defina **rótulo** como **clientes**.

11. Na guia **controles da faixa** de **ferramentas**do Office, arraste um **menu** para o grupo **compras de clientes** .

12. Na janela **Propriedades** , defina **rótulo** como **produto comprado**.

13. Defina **dinâmico** como **verdadeiro**.

     Isso permite que você adicione e remova controles no menu em tempo de execução depois que a faixa de faixas é carregada no aplicativo do Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Adicionar o grupo personalizado a uma guia interna

Uma guia interna é uma guia que já está na faixa de bits de um Explorer ou Inspetor do Outlook. Neste procedimento, você adicionará o grupo personalizado a uma guia interna e, em seguida, especificará a posição do grupo personalizado na guia.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Para adicionar o grupo personalizado a uma guia interna

1. Clique na guia **TabAddins (interna)** para selecioná-la.

2. Na janela **Propriedades** , expanda a propriedade **ControlID** e, em seguida, defina **OfficeId** como **TabNewMailMessage**.

     Isso adiciona o grupo **compras do cliente** à guia **mensagens** da faixa de faixas que aparece em uma nova mensagem de email.

3. Clique no grupo **compras de clientes** para selecioná-lo.

4. Na janela **Propriedades** , expanda a propriedade **posição** , clique na seta suspensa ao lado da propriedade **PositionType** e clique em **BeforeOfficeId**.

5. Defina a propriedade **OfficeId** como **GroupClipboard**.

     Isso posiciona o grupo **compras do cliente** antes do grupo área de **transferência** da guia **mensagens** .

## <a name="create-the-data-source"></a>Criar a fonte de dados

Use a janela **Data Sources** para adicionar um conjunto de dados tipado ao seu projeto.

### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1. No menu **Dados**, clique em **Adicionar Nova Fonte de Dados**.

     Isso inicia o **Assistente de configuração da fonte de dados**.

2. Selecione **banco de dados**e clique em **Avançar**.

3. Selecione **DataSet**e clique em **Avançar**.

4. Selecione uma conexão de dados com o exemplo Northwind Microsoft SQL Server Compact banco de dado 4,0 ou adicione uma nova conexão usando o botão **nova conexão** .

5. Depois que uma conexão for selecionada ou criada, clique em **Avançar**.

6. Clique em **Avançar** para salvar a cadeia de conexão.

7. Na página **escolher seus objetos de banco de dados** , expanda **tabelas**.

8. Marque a caixa de seleção ao lado de cada uma das tabelas a seguir:

    1. **Utilizam**

    2. **Detalhes do pedido**

    3. **Solicitar**

    4. **Produto**

9. Clique em **Finalizar**.

## <a name="update-controls-in-the-custom-group-at-run-time"></a>Atualizar controles no grupo personalizado em tempo de execução

Use o modelo de objeto da faixa de opções para executar as seguintes tarefas:

- Adicione nomes de clientes à caixa de combinação **clientes** .

- Adicione controles de menu e botão ao menu **produtos comprados** que representam pedidos de vendas e produtos vendidos.

- Preencha os campos para, assunto e corpo de novas mensagens de email usando dados do menu caixa de combinação **clientes** e **produtos comprados** .

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Para atualizar controles no grupo personalizado usando o modelo de objeto da faixa de faixas

1. No menu **Projeto**, clique em **Adicionar Referência**.

2. Na caixa de diálogo **Adicionar referência** , clique na guia **.net** , selecione o assembly **System. Data. Linq** e clique em **OK**.

    Esse assembly contém classes para usar consultas integradas à linguagem (LINQ). Você usará o LINQ para popular os controles no grupo personalizado com os dados do Northwind.

3. Em **Gerenciador de soluções**, clique em **CustomerRibbon.cs** ou **CustomerRibbon. vb** para selecioná-lo.

4. No menu **Exibir** , clique em **código**.

    O arquivo de código da faixa de Ribbon é aberto no editor de código.

5. Adicione as instruções a seguir à parte superior do arquivo de código da faixa de opções. Essas instruções fornecem acesso fácil aos namespaces LINQ e ao namespace do PIA (assembly de interoperabilidade primária) do Outlook.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Adicione o código a seguir dentro `CustomerRibbon` da classe. Esse código declara a tabela de dados e os adaptadores de tabela que você usará para armazenar informações do cliente, pedidos, detalhes do pedido e tabelas de produtos do banco de dados Northwind.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Adicione o seguinte bloco de código à `CustomerRibbon` classe. Esse código adiciona três métodos auxiliares que criam controles para a faixa de, em tempo de execução.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Substitua o `CustomerRibbon_Load` método do manipulador de eventos pelo código a seguir. Esse código usa uma consulta LINQ para executar as seguintes tarefas:

   - Preencha a caixa de combinação **clientes** usando a ID e o nome de 20 clientes no banco de dados Northwind.

   - Chama o `PopulateSalesOrderInfo` método auxiliar. Esse método atualiza o menu **ProductsPurchased** com números de ordem de venda que pertencem ao cliente selecionado no momento.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Adicione o código a seguir à classe `CustomerRibbon`. Esse código usa consultas LINQ para executar as seguintes tarefas:

   - Adiciona um submenu ao menu **ProductsPurchased** para cada ordem de venda relacionada ao cliente selecionado.

   - Adiciona botões a cada submenu para os produtos relacionados à ordem de venda.

   - Adiciona manipuladores de eventos a cada botão.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. Em **Gerenciador de soluções**, clique duas vezes no arquivo de código da faixa de bits.

     O designer de faixa de faixas é aberto.

11. No designer de faixa de faixas, clique duas vezes na caixa de combinação **clientes** .

     O arquivo de código da faixa de faixas é aberto no editor `ComboBox1_TextChanged` de códigos e o manipulador de eventos é exibido.

12. Substitua o `ComboBox1_TextChanged` manipulador de eventos pelo código a seguir. Esse código executa as seguintes tarefas:

    - Chama o `PopulateSalesOrderInfo` método auxiliar. Esse método atualiza o menu **produtos comprados** com pedidos de vendas relacionados ao cliente selecionado.

    - Chama o `PopulateMailItem` método auxiliar e passa o texto atual, que é o nome do cliente selecionado. Esse método popula os campos para, assunto e corpo de novas mensagens de email.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Adicione o seguinte `Click` manipulador de eventos `CustomerRibbon` à classe. Esse código adiciona o nome dos produtos selecionados ao campo corpo de novas mensagens de email.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Adicione o código a seguir à classe `CustomerRibbon`. Esse código executa as seguintes tarefas:

    - Popula a linha para de novas mensagens de email usando o endereço de email do cliente selecionado no momento.

    - Adiciona texto aos campos de assunto e corpo de novas mensagens de email.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Testar os controles no grupo personalizado

Quando você abre um novo formulário de email no Outlook, um grupo personalizado chamado **compras do cliente** é exibido na guia **mensagens** da faixa de faixas.

Para criar uma mensagem de email de acompanhamento do cliente, selecione um cliente e, em seguida, selecione os produtos comprados pelo cliente. Os controles no grupo **compras de clientes** são atualizados em tempo de execução com dados do banco de dados Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Para testar os controles no grupo personalizado

1. Pressione **F5** para executar o projeto.

     O Outlook é iniciado.

2. No Outlook, no menu **arquivo** , aponte para **novo**e clique em mensagem de **email**.

     Ocorrem as seguintes ações:

    - Uma nova janela Inspetor de mensagem de email é exibida.

    - Na guia **mensagem** da faixa de faixas, o grupo **compras do cliente** é exibido antes do grupo da área de **transferência** .

    - A caixa de combinação **clientes** no grupo é atualizada com os nomes de clientes no banco de dados Northwind.

3. Na guia **mensagem** da faixa de opções, no grupo **compras de clientes** , selecione um cliente na caixa de combinação **clientes** .

     Ocorrem as seguintes ações:

    - O menu **produtos comprados** é atualizado para mostrar cada pedido de vendas do cliente selecionado.

    - Cada submenu ordem de venda é atualizado para mostrar os produtos comprados nessa ordem.

    - O endereço de email do cliente selecionado é adicionado à linha **para** da mensagem de email, e o assunto e o corpo da mensagem de email são preenchidos com texto.

4. Clique no menu **produtos compras** , aponte para qualquer ordem de venda e clique em um produto da ordem de venda.

     O nome do produto é adicionado ao corpo da mensagem de email.

## <a name="next-steps"></a>Próximas etapas

Você pode aprender mais sobre como personalizar a interface do usuário do Office a partir destes tópicos:

- Adicione a interface do usuário baseada em contexto a qualquer personalização no nível do documento. Para obter mais informações, consulte [visão geral do painel Ações](../vsto/actions-pane-overview.md).

- Estenda um formulário padrão ou personalizado do Microsoft Office Outlook. Para obter mais informações, confira [Passo a passo: Criar uma região](../vsto/walkthrough-designing-an-outlook-form-region.md)de formulário do Outlook.

- Adicione um painel de tarefas personalizado ao Outlook. Para obter mais informações, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Consulte também

- [Acessar a faixa de faixas em tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)
- [Visão geral da faixa de faixas](../vsto/ribbon-overview.md)
- [LINQ (Consulta Integrada à Linguagem)](/dotnet/csharp/linq/index)
- [Como: Introdução à personalização da faixa de faixas](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Designer da faixa de opções](../vsto/ribbon-designer.md)
- [Passo a passo: Criar uma guia personalizada usando o designer de faixa de faixas](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Visão geral do modelo de objeto Ribbon](../vsto/ribbon-object-model-overview.md)
- [Personalizar uma faixa de faixas para o Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Como: Alterar a posição de uma guia na faixa de posições](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Como: Personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md)
- [Como: Adicionar controles ao modo de exibição de Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Como: Exportar uma faixa de faixas do designer de faixa de das para XML da faixa de das](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Como: Mostrar erros da interface do usuário do suplemento](../vsto/how-to-show-add-in-user-interface-errors.md)