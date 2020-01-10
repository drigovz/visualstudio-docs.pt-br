---
title: Validar dados em conjuntos de dados
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ed115e851e9c2291dfc9d00f4bb36f670a7f3e00
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586062"
---
# <a name="validate-data-in-datasets"></a>Validar dados em conjuntos de dados
A validação de dados é o processo de confirmar que os valores inseridos em objetos de dados estão em conformidade com as restrições no esquema de um DataSet. O processo de validação também confirma que esses valores estão seguindo as regras que foram estabelecidas para seu aplicativo. É uma boa prática validar os dados antes de enviar atualizações para o banco de dados subjacente. Isso reduz erros, bem como o número potencial de viagens de ida e volta entre um aplicativo e o banco de dados.

Você pode confirmar se os dados que estão sendo gravados em um DataSet são válidos por meio da criação de verificações de validação no conjunto de dados em si. O DataSet pode verificar os dados independentemente de como a atualização está sendo executada — seja diretamente por controles em um formulário, dentro de um componente ou de alguma outra maneira. Como o conjunto de dados faz parte do seu aplicativo (diferentemente do back-end do banco de dados), é um local lógico para criar a validação específica do aplicativo.

O melhor local para adicionar validação ao seu aplicativo é no arquivo de classe parcial do conjunto de um. Em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], abra o **Designer de conjunto de dados** e clique duas vezes na coluna ou tabela para a qual você deseja criar a validação. Essa ação cria automaticamente um manipulador de eventos <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging>.

## <a name="validate-data"></a>Validar os dados
A validação dentro de um conjunto de uma é feita das seguintes maneiras:

- Criando sua própria validação específica do aplicativo que pode verificar valores em uma coluna de dados individual durante as alterações. Para obter mais informações, consulte [como: validar dados durante alterações de coluna](validate-data-in-datasets.md).

- Criando sua própria validação específica do aplicativo que pode verificar os dados em valores enquanto uma linha de dados inteira está sendo alterada. Para obter mais informações, consulte [como: validar dados durante alterações de linha](validate-data-in-datasets.md).

- Criando chaves, restrições exclusivas e assim por diante como parte da definição de esquema real do conjunto de dados.

- Definindo as propriedades do <xref:System.Data.DataColumn> do objeto, como <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>e <xref:System.Data.DataColumn.Unique%2A>.

Vários eventos são gerados pelo objeto <xref:System.Data.DataTable> quando uma alteração está ocorrendo em um registro:

- Os eventos <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> são gerados durante e após cada alteração em uma coluna individual. O evento <xref:System.Data.DataTable.ColumnChanging> é útil quando você deseja validar as alterações em colunas específicas. As informações sobre a alteração proposta são passadas como um argumento com o evento.
- Os eventos <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> são gerados durante e após qualquer alteração em uma linha. O evento <xref:System.Data.DataTable.RowChanging> é mais geral. Isso indica que uma alteração está ocorrendo em algum lugar na linha, mas você não sabe qual coluna foi alterada.

Por padrão, cada alteração em uma coluna, portanto, gera quatro eventos. O primeiro é o <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> eventos para a coluna específica que está sendo alterada. A seguir estão os eventos <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged>. Se várias alterações estiverem sendo feitas na linha, os eventos serão gerados para cada alteração.

> [!NOTE]
> O método <xref:System.Data.DataRow.BeginEdit%2A> da linha de dados desativa os eventos <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> depois que cada coluna individual é alterada. Nesse caso, o evento não é gerado até que o método <xref:System.Data.DataRow.EndEdit%2A> tenha sido chamado, quando os eventos <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> são gerados apenas uma vez. Para obter mais informações, consulte [desativar restrições ao preencher um conjunto de](../data-tools/turn-off-constraints-while-filling-a-dataset.md)dados.

O evento escolhido depende de quão granular você deseja que a validação seja. Se for importante que você capture um erro imediatamente quando uma coluna for alterada, crie a validação usando o evento <xref:System.Data.DataTable.ColumnChanging>. Caso contrário, use o evento <xref:System.Data.DataTable.RowChanging>, que pode resultar na captura de vários erros ao mesmo tempo. Além disso, se os dados forem estruturados para que o valor de uma coluna seja validado com base no conteúdo de outra coluna, execute sua validação durante o evento de <xref:System.Data.DataTable.RowChanging>.

Quando os registros são atualizados, o objeto <xref:System.Data.DataTable> gera eventos que você pode responder à medida que as alterações estão ocorrendo e depois que as alterações são feitas.

Se seu aplicativo usar um dataset tipado, você poderá criar manipuladores de eventos com rigidez de tipos. Isso adiciona quatro eventos tipados adicionais para os quais você pode criar manipuladores: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`e `dataTableNameRowDeleted`. Esses manipuladores de eventos tipados passam um argumento que inclui os nomes de coluna da tabela que facilitam a gravação e a leitura do código.

## <a name="data-update-events"></a>Eventos de atualização de dados

|Event|Descrição|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|O valor em uma coluna está sendo alterado. O evento passa a linha e a coluna para você, juntamente com o novo valor proposto.|
|<xref:System.Data.DataTable.ColumnChanged>|O valor em uma coluna foi alterado. O evento passa a linha e a coluna para você, juntamente com o valor proposto.|
|<xref:System.Data.DataTable.RowChanging>|As alterações feitas em um objeto <xref:System.Data.DataRow> estão prestes a ser confirmadas de volta no conjunto de informações. Se você não tiver chamado o método <xref:System.Data.DataRow.BeginEdit%2A>, o evento <xref:System.Data.DataTable.RowChanging> será gerado para cada alteração em uma coluna imediatamente após a geração do evento <xref:System.Data.DataTable.ColumnChanging>. Se você chamou <xref:System.Data.DataRow.BeginEdit%2A> antes de fazer alterações, o evento <xref:System.Data.DataTable.RowChanging> será gerado somente quando você chamar o método <xref:System.Data.DataRow.EndEdit%2A>.<br /><br /> O evento passa a linha para você, junto com um valor que indica que tipo de ação (alterar, inserir e assim por diante) está sendo executado.|
|<xref:System.Data.DataTable.RowChanged>|Uma linha foi alterada. O evento passa a linha para você, junto com um valor que indica que tipo de ação (alterar, inserir e assim por diante) está sendo executado.|
|<xref:System.Data.DataTable.RowDeleting>|Uma linha está sendo excluída. O evento passa a linha para você, junto com um valor que indica que tipo de ação (Delete) está sendo executado.|
|<xref:System.Data.DataTable.RowDeleted>|Uma linha foi excluída. O evento passa a linha para você, junto com um valor que indica que tipo de ação (Delete) está sendo executado.|

Os eventos <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>e <xref:System.Data.DataTable.RowDeleting> são gerados durante o processo de atualização. Você pode usar esses eventos para validar dados ou executar outros tipos de processamento. Como a atualização está em andamento durante esses eventos, você pode cancelá-la lançando uma exceção, o que impede a conclusão da atualização.

Os eventos <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> e <xref:System.Data.DataTable.RowDeleted> são eventos de notificação que são gerados quando a atualização é concluída com êxito. Esses eventos são úteis quando você deseja realizar uma ação adicional com base em uma atualização bem-sucedida.

## <a name="validate-data-during-column-changes"></a>Validar dados durante alterações de coluna

> [!NOTE]
> O **Designer de conjunto de dados** cria uma classe parcial na qual a lógica de validação pode ser adicionada a um conjunto de uma. O conjunto de conjuntos gerado pelo designer não exclui nem altera nenhum código na classe parcial.

Você pode validar os dados quando o valor em uma coluna de dados é alterado respondendo ao evento <xref:System.Data.DataTable.ColumnChanging>. Quando gerado, esse evento passa um argumento de evento (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) que contém o valor que está sendo proposto para a coluna atual. Com base no conteúdo de `e.ProposedValue`, você pode:

- Aceite o valor proposto fazendo nada.

- Rejeite o valor proposto definindo o erro de coluna (<xref:System.Data.DataRow.SetColumnError%2A>) de dentro do manipulador de eventos de alteração de coluna.

- Opcionalmente, use um controle <xref:System.Windows.Forms.ErrorProvider> para exibir uma mensagem de erro para o usuário. Para obter mais informações, confira [Componente ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

A validação também pode ser executada durante o evento <xref:System.Data.DataTable.RowChanging>.

## <a name="validate-data-during-row-changes"></a>Validar dados durante as alterações de linha
Você pode escrever código para verificar se cada coluna que você deseja validar contém dados que atendem aos requisitos do seu aplicativo. Faça isso definindo a coluna para indicar que ela contém um erro se um valor proposto for inaceitável. Os exemplos a seguir definem um erro de coluna quando a coluna `Quantity` é 0 ou menor. Os manipuladores de eventos de alteração de linha devem se parecer com os exemplos a seguir.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Para validar dados quando uma linha é alterada (Visual Basic)

1. Abra o conjunto de dados no **Designer de Conjunto de Dados**. Para obter mais informações, consulte [Walkthrough: Criando um conjunto de dados no designer de conjunto de dados](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Clique duas vezes na barra de título da tabela que você deseja validar. Essa ação cria automaticamente o manipulador de eventos <xref:System.Data.DataTable.RowChanging> do <xref:System.Data.DataTable> no arquivo de classe parcial do conjunto de arquivos.

    > [!TIP]
    > Clique duas vezes à esquerda do nome da tabela para criar o manipulador de eventos de alteração de linha. Se você clicar duas vezes no nome da tabela, poderá editá-lo.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>Para validar dados quando uma linha é alteradaC#()

1. Abra o conjunto de dados no **Designer de Conjunto de Dados**. Para obter mais informações, consulte [Walkthrough: Criando um conjunto de dados no designer de conjunto de dados](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Clique duas vezes na barra de título da tabela que você deseja validar. Essa ação cria um arquivo de classe parcial para o <xref:System.Data.DataTable>.

    > [!NOTE]
    > O **Designer de conjunto de dados** não cria automaticamente um manipulador de eventos para o evento <xref:System.Data.DataTable.RowChanging>. Você precisa criar um método para manipular o evento <xref:System.Data.DataTable.RowChanging> e executar o código para vincular o evento no método de inicialização da tabela.

3. Copie o código a seguir para a classe parcial:

    ```csharp
    public override void EndInit()
    {
        base.EndInit();
        Order_DetailsRowChanging += TestRowChangeEvent;
    }

    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)
    {
        if ((short)e.Row.Quantity <= 0)
        {
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
        }
        else
        {
            e.Row.SetColumnError("Quantity", "");
        }
    }
    ```

## <a name="to-retrieve-changed-rows"></a>Para recuperar linhas alteradas
Cada linha em uma tabela de dados tem uma propriedade <xref:System.Data.DataRow.RowState%2A> que controla o estado atual dessa linha usando os valores na enumeração <xref:System.Data.DataRowState>. Você pode retornar linhas alteradas de um conjunto de dados ou tabela de data chamando o método `GetChanges` de um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>. Você pode verificar se existem alterações antes de chamar `GetChanges` chamando o método <xref:System.Data.DataSet.HasChanges%2A> de um conjunto de um DataSet.

> [!NOTE]
> Depois de confirmar as alterações em um conjunto de dados ou em uma tabela Data (chamando o método <xref:System.Data.DataSet.AcceptChanges%2A>), o método `GetChanges` não retorna nenhum dado. Se seu aplicativo precisar processar linhas alteradas, você deverá processar as alterações antes de chamar o método `AcceptChanges`.

Chamar o método <xref:System.Data.DataSet.GetChanges%2A> de um conjunto de dados ou de uma tabela Data retorna um novo DataSet ou tabela de dados que contém somente os registros que foram alterados. Se você quiser obter registros específicos — por exemplo, apenas novos registros ou somente registros modificados — você pode passar um valor da enumeração de <xref:System.Data.DataRowState> como um parâmetro para o método `GetChanges`.

Use a enumeração <xref:System.Data.DataRowVersion> para acessar as diferentes versões de uma linha (por exemplo, os valores originais que estavam em uma linha antes de processá-la).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Para obter todos os registros alterados de um conjunto de uma

- Chame o método <xref:System.Data.DataSet.GetChanges%2A> de um DataSet.

     O exemplo a seguir cria um novo conjunto de recursos chamado `changedRecords` e o popula com todos os registros alterados de outro DataSet chamado `dataSet1`.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>Para obter todos os registros alterados de uma tabela de dados

- Chame o método <xref:System.Data.DataTable.GetChanges%2A> de uma DataTable.

     O exemplo a seguir cria uma nova tabela de dados chamada `changedRecordsTable` e a preenche com todos os registros alterados de outra tabela de dados chamada `dataTable1`.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Para obter todos os registros que têm um estado de linha específico

- Chame o método `GetChanges` de um DataSet ou uma tabela de dados e passe um valor de enumeração <xref:System.Data.DataRowState> como um argumento.

     O exemplo a seguir mostra como criar um novo conjunto de recursos chamado `addedRecords` e preenchê-lo somente com os registros que foram adicionados ao conjunto de `dataSet1`.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     O exemplo a seguir mostra como retornar todos os registros que foram adicionados recentemente à tabela `Customers`:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Acessar a versão original de uma DataRow
Quando são feitas alterações nas linhas de dados, o conjunto de registros retém as versões original (<xref:System.Data.DataRowVersion.Original>) e nova (<xref:System.Data.DataRowVersion.Current>) da linha. Por exemplo, antes de chamar o método `AcceptChanges`, seu aplicativo pode acessar as diferentes versões de um registro (conforme definido na enumeração <xref:System.Data.DataRowVersion>) e processar as alterações de acordo.

> [!NOTE]
> Versões diferentes de uma linha existem somente após serem editadas e antes da chamada do método de `AcceptChanges`. Depois que o método de `AcceptChanges` foi chamado, as versões atual e original são as mesmas.

Passar o valor de <xref:System.Data.DataRowVersion> junto com o índice de coluna (ou nome de coluna como uma cadeia de caracteres) retorna o valor da versão de linha específica dessa coluna. A coluna alterada é identificada durante os eventos de <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged>. Esse é um bom momento para inspecionar as diferentes versões de linha para fins de validação. No entanto, se você suspendeu temporariamente as restrições, esses eventos não serão gerados e será necessário identificar de forma programática quais colunas foram alteradas. Você pode fazer isso Iterando pela coleção de <xref:System.Data.DataTable.Columns%2A> e comparando os diferentes valores de <xref:System.Data.DataRowVersion>.

### <a name="to-get-the-original-version-of-a-record"></a>Para obter a versão original de um registro

- Acesse o valor de uma coluna passando o <xref:System.Data.DataRowVersion> da linha que você deseja retornar.

     O exemplo a seguir mostra como usar um valor <xref:System.Data.DataRowVersion> para obter o valor original de um campo `CompanyName` em um <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Acessar a versão atual de uma DataRow

### <a name="to-get-the-current-version-of-a-record"></a>Para obter a versão atual de um registro

- Acesse o valor de uma coluna e, em seguida, adicione um parâmetro ao índice que indica qual versão de uma linha você deseja retornar.

     O exemplo a seguir mostra como usar um valor de <xref:System.Data.DataRowVersion> para obter o valor atual de um campo de `CompanyName` em um <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Veja também

- [Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Como validar dados no controle DataGridView do Windows Forms](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Como exibir ícones de erro para validação de formulário com o componente ErrorProvider do Windows Forms](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)
