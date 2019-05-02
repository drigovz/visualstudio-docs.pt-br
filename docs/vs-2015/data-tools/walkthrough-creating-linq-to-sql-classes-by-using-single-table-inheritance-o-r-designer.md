---
title: 'Passo a passo: Criando Classes LINQ to SQL, usando a herança de tabela única (Object Relational Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2dac656f9a765875fc552739b814538582200cc8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424694"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Passo a passo: Criando Classes LINQ to SQL, usando a herança de tabela única (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O [ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) dá suporte a herança de tabela única como geralmente é implementado em sistemas relacionais. Este passo a passo expande até as etapas genéricas fornecidas a [como: Configurar a herança usando o Designer relacional de objetos](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) tópico e fornece alguns dados reais para demonstrar o uso de herança no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
 Durante essa explicação passo a passo, você executará as seguintes tarefas:  
  
- Criar uma tabela de banco de dados e adicione dados a ela.  
  
- Criar um aplicativo do Windows Forms.  
  
- Adicionar um arquivo do [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] a um projeto.  
  
- Criar novas classes de entidade.  
  
- Configurar as classes de entidade para usar herança.  
  
- Consultar a classe herdada.  
  
- Exibir os dados em um Windows Form.  
  
## <a name="create-a-table-to-inherit-from"></a>Criar uma tabela da qual herdar  
 Para ver como a herança funciona, você criará uma pequena tabela Person, usará como uma classe base e, em seguida, criará um objeto Employee que herda dela.  
  
#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Para criar uma tabela base para demonstrar a herança  
  
1. No **Gerenciador de servidores**/**Gerenciador de banco de dados**, clique com botão direito do **tabelas** nó e clique em **adicionar nova tabela**.  
  
    > [!NOTE]
    > Você pode usar o banco de dados Northwind ou qualquer outro banco de dados ao qual você possa adicionar uma tabela.  
  
2. No Designer de Tabela, adicione as seguintes colunas à tabela:  
  
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
  
#### <a name="to-add-data-to-the-table"></a>Para adicionar dados à tabela  
  
1. Abra a tabela no modo de exibição de dados. (Clique com botão direito do **pessoa** na tabela **Gerenciador de servidores**/**Database Explorer** e clique em **Mostrar dados da tabela**.)  
  
2. Copie os seguintes dados na tabela. (Você pode copiá-lo e, em seguida, cole-o na tabela selecionando a linha inteira no painel de resultados.)  
  
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
  
#### <a name="to-create-the-new-windows-application"></a>Para criar o novo aplicativo do Windows  
  
1. Dos **arquivo** menu, crie um novo projeto.  
  
2. Nomeie o projeto **InheritanceWalkthrough**.  
  
    > [!NOTE]
    > O [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tem suporte em projetos do Visual Basic e C#. Crie o novo projeto em uma dessas linguagens.  
  
3. Clique o **aplicativo do Windows Forms** modelo e clique **Okey**. Para obter mais informações, consulte [aplicativos cliente](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
4. O projeto InheritanceWalkthrough é criado e adicionado ao **Gerenciador de soluções**.  
  
## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Adicionar um arquivo de classes do LINQ to SQL ao projeto  
  
#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Para adicionar um arquivo LINQ to SQL ao projeto  
  
1. No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
2. Clique no modelo **Classes LINQ to SQL** e clique em **Adicionar**.  
  
     O arquivo .dbml é adicionado ao projeto e o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] é aberto.  
  
## <a name="create-the-inheritance-by-using-the-or-designer"></a>Criar a herança usando o Designer Relacional de Objetos  
 Configure a herança arrastando um objeto **Herança** da **Caixa de Ferramentas** para a superfície de design.  
  
#### <a name="to-create-the-inheritance"></a>Para criar a herança  
  
1. Na **Gerenciador de servidores**/**Database Explorer**, navegue até a **pessoa** tabela que você criou anteriormente.  
  
2. Arraste o **pessoa** de tabela para o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] superfície de design.  
  
3. Arraste uma segunda **pessoa** de tabela para o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] e altere seu nome para **funcionário**.  
  
4. Exclua a propriedade **Manager** do objeto **Pessoa**.  
  
5. Exclua as propriedades **Type**, **ID**, **FirstName** e **LastName** do objeto **Employee**. (Em outras palavras, exclua todas as propriedades exceto **Gerente**.)  
  
6. Na guia **Object Relational Designer** da **Caixa de Ferramentas**, crie uma **Herança** entre os objetos **Pessoa** e **Funcionário**. Para fazer isso, clique no item **Herança** na **Caixa de Ferramentas** e solte o botão do mouse. Em seguida, clique o **funcionário** objeto e, em seguida, o **pessoa** objeto o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. A seta na linha de herança irá apontar para o **pessoa** objeto.  
  
7. Clique na linha **Herança** na superfície de design.  
  
8. Defina a **Propriedade Discriminatória** como **Tipo**.  
  
9. Defina a propriedade **Valor Discriminatório da Classe Derivada** como **2**.  
  
10. Defina a propriedade **Valor Discriminatório da Classe Base** como **1**.  
  
11. Defina a propriedade **Padrão de Herança** como **Pessoa**.  
  
12. Compile o projeto.  
  
## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Consultar a classe herdada e exibir os dados no formulário  
 Agora você adicionará um código ao formulário que consulta uma classe específica no modelo de objeto.  
  
#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Para criar uma consulta LINQ e exibir os resultados no formulário  
  
1. Arraste uma **ListBox** para Form1.  
  
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
 Execute o aplicativo e verifique se os registros exibidos na caixa de listagem são todos empregados (os registros que têm um valor de 2 na coluna Tipo).  
  
#### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1. Pressione F5.  
  
2. Verifique se apenas os registros que têm um valor de 2 na coluna Tipo são exibidos.  
  
3. Feche o formulário. (No menu **Depurar**, clique em **Parar Depuração**.)  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Como: Adicionar o LINQ to SQL Classes a um projeto (Object Relational Designer)](http://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6)   
 [Passo a passo: Criando Classes LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer relacional de objetos)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Como: gerar o modelo de objeto em Visual Basic ou em C#](http://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)
