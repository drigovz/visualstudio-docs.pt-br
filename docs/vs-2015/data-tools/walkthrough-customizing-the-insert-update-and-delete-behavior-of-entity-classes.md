---
title: 'Walkthrough: Personalizando o comportamento de inserção, atualização e exclusão de classes de entidade | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9901d917de2babf4992519ffe6b360454542aad1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602568"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Passo a passo: personalizando a inserção, a atualização e o comportamento de exclusão de classes de entidade
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As [ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornecem uma superfície de Design Visual para criar e editar [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] classes (classes de entidade) que se baseiam em objetos em um banco de dados. Usando [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655), você pode usar a tecnologia LINQ para acessar bancos de dados SQL. Para saber mais, veja [LINQ (Consulta Integrada à Linguagem)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).

 Por padrão, a lógica para executar atualizações é fornecida pelo tempo de execução do [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. O runtime cria instruções padrão Insert, Update e Delete com base no esquema da tabela (as definições de coluna e as informações da chave primária). Quando você não deseja usar o comportamento padrão, poderá configurar o comportamento de atualização e designar procedimentos armazenados específicos para executar as inserções, as atualizações e as exclusões necessárias para trabalhar com os dados no banco de dados. Você também pode fazer isso quando o comportamento padrão não é gerado, por exemplo, quando as classes de entidade mapeiam para as exibições. Além disso, você pode substituir o comportamento de atualização padrão quando o banco de dados exige acesso à tabela por meio dos procedimentos armazenados. Para obter mais informações, consulte [Personalizando operações usando procedimentos armazenados](https://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).

> [!NOTE]
> Essa explicação passo a passo exige a disponibilidade dos procedimentos armazenados **InsertCustomer**, **UpdateCustomer** e **DeleteCustomer** para o banco de dados Northwind.

 Essa explicação passo a passo fornece as etapas que você deve seguir para substituir o comportamento padrão de runtime LINQ to SQL para salvar dados de volta para um banco de dados usando procedimentos armazenados.

 Durante essa explicação passo a passo, será ensinado como realizar as seguintes tarefas:

- Crie um novo aplicativo do Windows Forms e adicione um arquivo [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] a ele.

- Crie uma classe de entidade que está mapeada para a tabela Customers Northwind.

- Crie uma fonte de dados de objeto que referencia a classe de cliente LINQ to SQL.

- Crie um Windows Form que contém um <xref:System.Windows.Forms.DataGridView> que está associado à classe Customer.

- Implemente a funcionalidade de salvar para o formulário.

- Crie métodos de <xref:System.Data.Linq.DataContext> adicionando procedimentos armazenados ao [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

- Configure a classe Customer para usar procedimentos armazenados para executar inserções, atualizações e exclusões.

## <a name="prerequisites"></a>Prerequisites
 Para concluir esta explicação passo a passo, você precisará do seguinte:

- Acessar a versão do SQL Server do banco de dados de exemplo Northwind.

- Os procedimentos armazenados **InsertCustomer**, **UpdateCustomer**e **DeleteCustomer** para o banco de dados Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Criando um aplicativo e adicionando classes LINQ to SQL
 Como você estará trabalhando com classes do [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] e exibindo os dados em um Windows Form, crie um novo aplicativo do Windows Forms e adicione um arquivo de classes LINQ to SQL.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>Para criar um novo projeto de aplicativo do Windows que contém classes LINQ to SQL

1. No menu **arquivo** , crie um novo projeto.

2. Nomeie o projeto **UpdatingwithSProcsWalkthrough**.

    > [!NOTE]
    > O [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tem suporte em projetos de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] e C#. Portanto, crie o novo projeto em uma dessas linguagens.

3. Clique no modelo de **aplicativo Windows Forms** e clique em **OK**. Para obter mais informações, consulte [aplicativos cliente](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     O projeto UpdatingwithSProcsWalkthrough é criado e adicionado ao **Gerenciador de soluções**.

4. No menu **Projeto**, clique em **Adicionar Novo Item**.

5. Clique no modelo **Classes LINQ to SQL** e digite **Northwind.dbml** na caixa **Nome**.

6. Clique em **Adicionar**.

     Um arquivo de classes LINQ to SQL vazio (Northwind.dbml) é adicionado ao projeto, e o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] é aberto.

## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Criando a Classe Entidade de Cliente e o Objeto de Fonte de Dados
 Crie [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] classes que são mapeadas para tabelas de banco de dados arrastando tabelas de **Gerenciador de Servidores** /**Gerenciador de Banco de Dados** para o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. O resultado são classes de entidade do LINQ to SQL que mapeiam para as tabelas no banco de dados. Depois de criar classes de entidade, elas podem ser usadas como fontes de dados de objeto assim como outras classes que têm propriedades públicas.

#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Para criar uma classe de entidade Customer e configurar uma fonte de dados com ela

1. Em **Gerenciador de Servidores** /**Gerenciador de banco de dados**, localize a tabela cliente na versão SQL Server do banco de dados de exemplo Northwind.

2. Arraste o nó **clientes** do **Gerenciador de servidores** /**Gerenciador de banco de dados** na superfície [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Uma classe de entidade chamada **Customer** é criada. Ela tem propriedades que correspondem às colunas na tabela Customers. A classe de entidade é chamada de **Customer** (e não **Customers**) porque representa um único cliente da tabela Customers.

    > [!NOTE]
    > Esse comportamento de renomeação é chamado de *pluralização*. Ele pode ser ativado ou desativado na caixa de [diálogo opções](../ide/reference/options-dialog-box-visual-studio.md). Para obter mais informações, consulte [como ativar e desativar a pluralização (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. No menu **Compilar**, clique em **Compilar UpdatingwithSProcsWalkthrough** para criar o projeto.

4. No menu **Dados**, clique em **Mostrar Fontes de Dados**.

5. Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados**.

6. Clique em **Objeto** na página **Escolher um Tipo de Fonte de Dados** e clique em **Avançar**.

7. Expanda o nó **UpdatingwithSProcsWalkthrough** e localize e selecione a classe **Customer**.

    > [!NOTE]
    > Se a classe **Customer** não estiver disponível, cancele o assistente, compile o projeto e execute o assistente novamente.

8. Clique em **Concluir** para criar a fonte de dados e adicionar a classe de entidade **Customer** à janela **Fontes de Dados**.

## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Criando um DataGridView para exibir os dados do cliente em um Windows Form
 Crie controles associados a classes de entidade arrastando [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] itens de fonte de dados da janela **fontes de dados** para um formulário do Windows.

#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Para adicionar controles que estão associados às classes de entidade

1. Abrir Form1 na exibição Design.

2. Na janela **fontes de dados** , arraste o nó **cliente** para o Form1.

    > [!NOTE]
    > Para exibir a janela **Fontes de Dados**, clique em **Mostrar Fontes de Dados** no menu **Dados**.

3. Abra o Form1 no Editor de Códigos.

4. Adicione o seguinte código ao formulário, global para o formulário, fora de qualquer método específico, mas dentro da classe Form1:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();

    ```

5. Crie um manipulador de eventos para o evento `Form_Load` e adicione o seguinte código ao manipulador:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;

    ```

## <a name="implementing-save-functionality"></a>Implementando a funcionalidade de salvar
 Por padrão, o botão de salvar não está habilitado e a funcionalidade de salvar não está implementada. Além disso, o código não será automaticamente adicionado para salvar dados modificados no banco de dados quando os controles associados a dados forem criados para fontes de dados de objeto. Esta seção explica como habilitar o botão salvar e implementar a funcionalidade salvar para objetos do [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].

#### <a name="to-implement-save-functionality"></a>Para implementar a funcionalidade de salvar

1. Abrir Form1 na exibição Design.

2. Selecione o botão de salvar no **CustomerBindingNavigator** (o botão com o ícone de disquete).

3. Na janela **Propriedades**, defina a propriedade **Habilitado** como **True**.

4. Clique duas vezes no botão de salvar para criar um manipulador de eventos e alternar para o Editor de Códigos.

5. Adicione o código a seguir no manipulador de eventos do botão de salvar:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Substituindo o comportamento padrão para realizar atualizações (inserções, atualizações e exclusões)

#### <a name="to-override-the-default-update-behavior"></a>Para substituir o comportamento padrão de atualização

1. Abra o arquivo LINQ to SQL no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Clique duas vezes no arquivo **Northwind.dbml** no **Gerenciador de Soluções**.)

2. Em **Gerenciador de Servidores** /**Gerenciador de banco de dados**, expanda o nó **procedimentos armazenados** de bancos de dados Northwind e localize os procedimentos armazenados **InsertCustomers**, **UpdateCustomers**e **DeleteCustomers** .

3. Arraste os três procedimentos armazenados para o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Os procedimentos armazenados são adicionados ao painel dos métodos como métodos <xref:System.Data.Linq.DataContext>. Para obter mais informações, consulte [métodos DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Selecione a classe de entidade **Customer** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

5. Na janela **Propriedades**, selecione a propriedade **Insert**.

6. Clique nas reticências (...) ao lado de **usar tempo de execução** para abrir a caixa de diálogo **Configurar comportamento** .

7. Selecione **Personalizar**.

8. Selecione o método **InsertCustomers** na lista **Personalizar**.

9. Clique em **Aplicar** para salvar a configuração para a Classe e o Comportamento selecionados.

    > [!NOTE]
    > Você pode continuar a configurar o comportamento para cada combinação de classe/comportamento quando você clica em **Aplicar** depois de cada alteração. Se você alterar a classe ou o comportamento antes de clicar em **aplicar**, uma caixa de diálogo de aviso que fornece uma oportunidade para aplicar todas as alterações será exibida.

10. Selecione **Atualizar** na lista **Comportamento**.

11. Selecione **Personalizar**.

12. Selecione o método **UpdateCustomers** na lista **Personalizar**.

     Inspecione a lista de **Argumentos de Método** e de **Propriedades de Classe** e observe que há dois **Argumentos de Método** e duas **Propriedades de Classe** para algumas colunas na tabela. Isso facilita controlar as alterações e criar as instruções que conferem a existência de violações de simultaneidade.

13. Mapeie o argumento do método **Original_CustomerID** para a propriedade de classe **CustomerID (Original)** .

    > [!NOTE]
    > Por padrão, os argumentos do método mapearão para as propriedades da classe quando os nomes corresponderem. Se os nomes de propriedade forem modificados e não corresponderem entre a tabela e a classe de entidade, você poderá ter que selecionar a propriedade da classe equivalente para a qual mapear se o Designer Relacional de Objetos não puder determinar o mapeamento correto. Além disso, se os argumentos do método não tiverem propriedades da classe válidas para a qual mapear, você poderá definir o valor de **Propriedades de Classe** como **(Nenhum)** .

14. Clique em **Aplicar** para salvar a configuração para a Classe e o Comportamento selecionados.

15. Selecione **Excluir** na lista **Comportamento**.

16. Selecione **Personalizar**.

17. Selecione o método **DeleteCustomers** na lista **Personalizar**.

18. Mapeie o argumento do método **Original_CustomerID** para a propriedade de classe **CustomerID (Original)** .

19. Clique em **OK**.

> [!NOTE]
> Embora isso não seja um problema para essa explicação passo a passo específica, vale observar que o [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] manipula automaticamente os valores gerados por banco de dados para as colunas identidade (incremento automático), rowguidcol (GUID gerado por banco de dados) e carimbo de data/hora durante inserções e atualizações. Os valores gerados pelo banco de dados em outros tipos de coluna resultarão inesperadamente em um valor nulo. Para retornar os valores gerados pelo banco de dados, você deve definir manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> para `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> a um dos seguintes: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> ou <xref:System.Data.Linq.Mapping.AutoSync>.

## <a name="testing-the-application"></a>Testando o aplicativo
 Execute o aplicativo novamente para verificar se o procedimento armazenado **UpdateCustomers** atualiza corretamente o registro do cliente no banco de dados.

#### <a name="to-test-the-application"></a>Para testar o aplicativo

1. Pressione F5.

2. Modifique um registro na grade para testar o comportamento de atualização.

3. Adicione um novo registro para testar o comportamento de inserção.

4. Clique no botão de salvar para salvar as alterações de volta para o banco de dados.

5. Feche o formulário.

6. Pressione F5 e verifique se o registro atualizado e o registro inserido recentemente persistiram.

7. Exclua o novo registro que você criou na etapa 3 para testar o comportamento de exclusão.

8. Clique no botão de salvar para enviar as alterações e remova o registro excluído do banco de dados

9. Feche o formulário.

10. Pressione F5 e verifique se o registro excluído foi removido do banco de dados.

    > [!NOTE]
    > Se seu aplicativo usar a edição SQL Server Express, dependendo do valor da propriedade **copiar para diretório de saída** do arquivo de banco de dados, as alterações poderão não aparecer quando você pressionar F5 na etapa 10.

## <a name="next-steps"></a>Próximas etapas
 Dependendo dos requisitos do aplicativo, há várias etapas que você pode querer executar depois de criar [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] classes de entidade. Entre algumas das melhorias que você pode fazer neste aplicativo estão:

- Implementar verificação de simultaneidade durante atualizações. Para obter informações, consulte [simultaneidade otimista: visão geral](https://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).

- Adicionar consultas LINQ para filtrar dados. Para obter informações, consulte [introdução às consultas LINQC#()](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).

## <a name="see-also"></a>Consulte também
 [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [LINQ to SQL consulta](https://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae) [métodos DataContext (o/r designer)](../data-tools/datacontext-methods-o-r-designer.md) [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (o/r designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [pavimentar o que há de novo para Desenvolvimento de aplicativos de dados no Visual Studio 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1)
