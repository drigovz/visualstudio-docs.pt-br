---
title: Classes LINQ to SQL com a herança de tabela única (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c99023f57cec8b920518ac702cf5c71988a163c
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66262875"
---
# <a name="walkthrough-create-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Passo a passo: Criar classes LINQ to SQL, usando a herança de tabela única (O/R Designer)
O [LINQ to SQL das ferramentas no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) dá suporte a herança de tabela única como geralmente é implementado em sistemas relacionais. Este passo a passo expande até as etapas genéricas fornecidas a [como: Configurar a herança usando o Designer relacional de objetos](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) tópico e fornece alguns dados reais para demonstrar o uso de herança no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

 Durante este passo a passo, você deve executar as seguintes tarefas:

- Criar uma tabela de banco de dados e adicione dados a ela.

- Criar um aplicativo do Windows Forms.

- Adicionar um arquivo do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a um projeto.

- Criar novas classes de entidade.

- Configurar as classes de entidade para usar herança.

- Consultar a classe herdada.

- Exibir os dados em um Windows Form.

## <a name="create-a-table-to-inherit-from"></a>Criar uma tabela da qual herdar
 Para ver como funciona a herança, você cria um pequeno `Person` de tabela, usá-lo como uma classe base e, em seguida, criar um `Employee` objeto que herda dela.

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Para criar uma tabela base para demonstrar a herança

1. Na **Gerenciador de servidores** ou **Database Explorer**, clique com botão direito a **tabelas** nó e clique em **adicionar nova tabela**.

    > [!NOTE]
    > Você pode usar o banco de dados Northwind ou qualquer outro banco de dados ao qual você possa adicionar uma tabela.

2. No **Designer de Tabela**, adicione as seguintes colunas à tabela:

    |Nome da coluna|Tipo de dados|Permitir nulos|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Tipo**|**int**|**True**|
    |**FirstName**|**nvarchar(200)**|**False**|
    |**LastName**|**nvarchar(200)**|**False**|
    |**Gerente**|**int**|**True**|

3. Defina a coluna de identificação como a chave primária.

4. Salve a tabela e dê a ela o nome de **Pessoa**.

## <a name="add-data-to-the-table"></a>Adicionar dados à tabela
 Para que você possa verificar se a herança está configurada corretamente, a tabela precisa de alguns dados para cada classe na herança de tabela única.

### <a name="to-add-data-to-the-table"></a>Para adicionar dados à tabela

1. Abra a tabela no modo de exibição de dados. (Clique com botão direito do **pessoa** na tabela **Gerenciador de servidores** ou **Database Explorer** e clique em **Mostrar dados da tabela**.)

2. Copie os seguintes dados na tabela. (Você pode copiá-lo e, em seguida, cole-o na tabela selecionando a linha inteira na **resultados** painel.)

    ||||||
    |-|-|-|-|-|
    |**ID**|**Tipo**|**FirstName**|**LastName**|**Gerente**|
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|
    |**3**|**1**|**Yael**|**Peled**|**NULL**|
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|
    |**5**|**2**|**Andreas**|**Hauser**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|
    |**9**|**2**|**Tai**|**Yee**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Mindy**|**Martin**|**3**|
    |**12**|**2**|**Ken**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>Criar um novo projeto
 Agora que você criou a tabela, crie um novo projeto demonstrar a configuração de herança.

### <a name="to-create-the-new-windows-forms-application"></a>Para criar o novo aplicativo de formulários do Windows

1. No Visual Studio, sobre o **arquivo** menu, selecione **New** > **projeto**.

2. Expanda o **Visual c#** ou **Visual Basic** no painel esquerdo, em seguida, selecione **área de trabalho do Windows**.

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.

4. Nomeie o projeto **InheritanceWalkthrough**e, em seguida, escolha **Okey**.

     O projeto **InheritanceWalkthrough** é criado e adicionado ao **Gerenciador de Soluções**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Adicionar um arquivo de classes do LINQ to SQL ao projeto

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Para adicionar um arquivo LINQ to SQL ao projeto

1. No menu **Projeto**, clique em **Adicionar Novo Item**.

2. Clique no modelo **Classes LINQ to SQL** e clique em **Adicionar**.

     O *dbml* arquivo é adicionado ao projeto e o **Relational Designer** é aberta.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Criar a herança usando o Designer Relacional de Objetos
 Configure a herança arrastando um objeto **Herança** da **Caixa de Ferramentas** para a superfície de design.

### <a name="to-create-the-inheritance"></a>Para criar a herança

1. Na **Gerenciador de servidores** ou **Database Explorer**, navegue até o **pessoa** tabela que você criou anteriormente.

2. Arraste o **pessoa** de tabela para o **Relational Designer** superfície de design.

3. Arraste uma segunda **pessoa** de tabela para o **Relational Designer** e altere seu nome para **funcionário**.

4. Exclua a propriedade **Manager** do objeto **Pessoa**.

5. Exclua as propriedades **Type**, **ID**, **FirstName** e **LastName** do objeto **Employee**. (Em outras palavras, exclua todas as propriedades exceto **Gerente**.)

6. Na guia **Object Relational Designer** da **Caixa de Ferramentas**, crie uma **Herança** entre os objetos **Pessoa** e **Funcionário**. Para fazer isso, clique no item **Herança** na **Caixa de Ferramentas** e solte o botão do mouse. Em seguida, clique o **funcionário** objeto e, em seguida, o **pessoa** objeto o **Relational Designer**. A seta na linha de herança, em seguida, aponta para o **pessoa** objeto.

7. Clique na linha **Herança** na superfície de design.

8. Defina a **Propriedade Discriminatória** como **Tipo**.

9. Defina a propriedade **Valor Discriminatório da Classe Derivada** como **2**.

10. Defina a propriedade **Valor Discriminatório da Classe Base** como **1**.

11. Defina a propriedade **Padrão de Herança** como **Pessoa**.

12. Compile o projeto.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Consultar a classe herdada e exibir os dados no formulário
 Agora você pode adicionar algum código ao formulário que consulta uma classe específica no modelo de objeto.

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Para criar uma consulta LINQ e exibir os resultados no formulário

1. Arraste um controle **ListBox** para **Form1**.

2. Clique duas vezes no formulário para criar um manipulador de eventos `Form1_Load`.

3. Adicione o seguinte código ao manipulador de eventos do `Form1_Load`:

    ```vb
    Dim dc As New DataClasses1DataContext
    Dim results = From emp In dc.Persons _
        Where TypeOf emp Is Employee _
        Select emp

    For Each Emp As Employee In results
        ListBox1.Items.Add(Emp.LastName)
    Next
    ```

    ```csharp
    NorthwindDataContext dc = new DataClasses1DataContext();
    var results = from emp in dc.Persons
                  where emp is Employee
                  select emp;

    foreach(Employee Emp in results)
    {
        listBox1.Items.Add(Emp.LastName)
    }
    ```

## <a name="test-the-application"></a>Testar o aplicativo
 Execute o aplicativo e verifique se os registros exibidos na caixa de listagem são todos empregados (os registros que têm um valor de 2 na coluna **Tipo**).

### <a name="to-test-the-application"></a>Para testar o aplicativo

1. Pressione **F5**.

2. Verifique se apenas os registros que têm um valor de 2 na coluna **Tipo** são exibidos.

3. Feche o formulário. (No menu **Depurar**, clique em **Parar Depuração**.)

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Passo a passo: Criando o LINQ para SQL classes (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Como: Gerar o modelo de objeto no Visual Basic ou c#](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)
