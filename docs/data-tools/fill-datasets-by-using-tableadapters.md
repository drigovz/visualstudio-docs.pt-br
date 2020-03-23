---
title: Preencher conjuntos de dados usando TableAdapters
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a79f7b781944bb93a60794e748eefb9375723384
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302234"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Preencher conjuntos de dados usando TableAdapters

Um componente TableAdapter preenche um conjunto de dados com dados do banco de dados, com base em uma ou mais consultas ou procedimentos armazenados que você especifica. O TableAdapters também pode executar adicionais, atualizações e exclusões no banco de dados para persistir as alterações que você faz no conjunto de dados. Você também pode emitir comandos globais que não estão relacionados a nenhuma tabela específica.

> [!NOTE]
> TableAdapters são gerados por designers do Visual Studio. Se você estiver criando conjuntos de dados de forma programática, use DataAdapter, que é uma classe .NET.

Para obter informações detalhadas sobre as operações do TableAdapter, você pode pular diretamente para um desses tópicos:

|Tópico|Descrição|
|-----------|-----------------|
|[Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Como usar os designers para criar e configurar TableAdapters|
|[Criar consultas TableAdapter parametrizadas](../data-tools/create-parameterized-tableadapter-queries.md)|Como permitir que os usuários forneçam argumentos para procedimentos ou consultas do TableAdapter|
|[Acessar diretamente o banco de dados com um TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Como usar os métodos Dbdirect de TableAdapters|
|[Desligar restrições ao preencher um conjunto de dados](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Como trabalhar com restrições de tecla estrangeira ao atualizar dados|
|[Como estender a funcionalidade de um TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Como adicionar código personalizado aos TableAdapters|
|[Ler dados XML em um conjunto de dados](../data-tools/read-xml-data-into-a-dataset.md)|Como trabalhar com XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Visão geral de TableAdapter

TableAdapters são componentes gerados pelo designer que se conectam a um banco de dados, executam consultas ou procedimentos armazenados e preenchem sua Tabela de Dados com os dados retornados. Os TableAdapters também enviam dados atualizados do seu aplicativo de volta para o banco de dados. Você pode executar quantas consultas quiser em um TableAdapter, desde que retornem dados que estejam em conformidade com o esquema da tabela com a qual o TableAdapter está associado. O diagrama a seguir mostra como o TableAdapters interage com bancos de dados e outros objetos na memória:

![Fluxo de dados em um aplicativo cliente](../data-tools/media/clientdatadiagram.gif)

Embora o TableAdapters seja projetado com o **Dataset Designer,** as classes <xref:System.Data.DataSet>TableAdapter não são geradas como classes aninhadas de . Eles estão localizados em espaços de nomes separados que são específicos para cada conjunto de dados. Por exemplo, se você tiver `NorthwindDataSet`um conjunto de dados <xref:System.Data.DataTable>chamado , `NorthwindDataSet` os TableAdapters que estão associados a s no seria no `NorthwindDataSetTableAdapters` namespace. Para acessar um Adaptador de Mesa específico programáticamente, você deve declarar uma nova instância do TableAdapter. Por exemplo: 

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Esquema da DataTable associada

Ao criar um TableAdapter, você usa a consulta inicial ou o procedimento armazenado para <xref:System.Data.DataTable>definir o esquema do TableAdapter associado . Você executa este procedimento inicial de consulta ou `Fill` armazenado chamando o método do TableAdapter (que preenche o associado <xref:System.Data.DataTable>do TableAdapter). Quaisquer alterações feitas na consulta principal do TableAdapter são refletidas no esquema da tabela de dados associada. Por exemplo, remover uma coluna da consulta principal também remove a coluna da tabela de dados associada. Se quaisquer consultas adicionais no TableAdapter usarem instruções SQL que retornam colunas que não estão na consulta principal, o designer tentará sincronizar as alterações da coluna entre a consulta principal e as consultas adicionais.

## <a name="tableadapter-update-commands"></a>Comandos de atualização do TableAdapter

A funcionalidade de atualização de um TableAdapter depende de quanta informação está disponível na consulta principal no **Assistente TableAdapter**. Por exemplo, os TableAdapters configurados para buscar valores de várias tabelas (usando um `JOIN`), valores escalares, visualizações ou os resultados de funções agregadas não são criados inicialmente com a capacidade de enviar atualizações de volta para o banco de dados subjacente. No entanto, você `INSERT` `UPDATE`pode `DELETE` configurar os comandos e comandos manualmente na janela **Propriedades.**

## <a name="tableadapter-queries"></a>consultas TableAdapter

![Adaptador de tabela com várias consultas](../data-tools/media/tableadapter.gif)

TableAdapters podem conter várias consultas para preencher suas tabelas de dados associadas. Você pode definir quantas consultas for em um TableAdapter conforme seu aplicativo exigir, desde que cada consulta retorne dados que estejam em conformidade com o mesmo esquema que sua tabela de dados associada. Esse recurso permite que um TableAdapter carregue diferentes resultados com base em critérios diferentes.

Por exemplo, se o seu aplicativo contiver uma tabela com nomes de clientes, você pode criar uma consulta que preencha a tabela com cada nome de cliente que começa com uma determinada letra, e outra que preencha a tabela com todos os clientes que estão localizados no mesmo estado. Para preencher `Customers` uma tabela com clientes em `FillByState` um determinado estado, você pode criar uma `SELECT * FROM Customers WHERE State = @State`consulta que leve um parâmetro para o valor do estado da seguinte forma: . Você executa a consulta `FillByState` chamando o método e passando `CustomerTableAdapter.FillByState("WA")`o valor do parâmetro assim: .

Além de adicionar consultas que retornam dados do mesmo esquema que a tabela de dados do TableAdapter, você pode adicionar consultas que retornam valores escalar (único). Por exemplo, uma consulta que retorna`SELECT Count(*) From Customers`uma contagem `CustomersTableAdapter,` de clientes ( ) é válida para um mesmo que os dados devolvidos não estejam de acordo com o esquema da tabela.

## <a name="clearbeforefill-property"></a>Propriedade ClearBeforeFill

Por padrão, toda vez que você executa uma consulta para preencher a tabela de dados de um TableAdapter, os dados existentes são apagados e apenas os resultados da consulta são carregados na tabela. Defina a propriedade `ClearBeforeFill` do `false` TableAdapter para se você quiser adicionar ou mesclar os dados retornados de uma consulta para os dados existentes em uma tabela de dados. Independentemente de você limpar os dados, você precisa enviar explicitamente atualizações de volta para o banco de dados, se você quiser persistiu neles. Portanto, lembre-se de salvar quaisquer alterações nos dados na tabela antes de executar outra consulta que preencha a tabela. Para obter mais informações, consulte [Atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Herança tableAdapter

TableAdapters ampliam a funcionalidade dos adaptadores de <xref:System.Data.Common.DataAdapter> dados padrão encapsulando uma classe configurada. Por padrão, o TableAdapter <xref:System.ComponentModel.Component> herda da classe e <xref:System.Data.Common.DataAdapter> não pode ser lançado para a classe. Lançar um TableAdapter <xref:System.Data.Common.DataAdapter> para a <xref:System.InvalidCastException> classe resulta em um erro. Para alterar a classe base de um TableAdapter, você <xref:System.ComponentModel.Component> pode especificar uma classe derivada da propriedade **Classe base** do TableAdapter no **Dataset Designer**.

## <a name="tableadapter-methods-and-properties"></a>Métodos e propriedades do TableAdapter

A classe TableAdapter não é um tipo .NET. Isso significa que você não pode procurá-lo na documentação ou no **Navegador de Objetos**. Ele é criado na hora do design quando você usa um dos assistentes mencionados anteriormente. O nome atribuído a um TableAdapter quando você o cria é baseado no nome da tabela com a que você está trabalhando. Por exemplo, quando você cria um TableAdapter baseado `Orders`em uma tabela `OrdersTableAdapter`em um banco de dados chamado, o TableAdapter é nomeado . O nome de classe do TableAdapter pode ser alterado usando a propriedade **Nome** no **Dataset Designer**.

A seguir estão os métodos e propriedades comumente utilizados dos TableAdapters:

|Membro|Descrição|
|------------|-----------------|
|`TableAdapter.Fill`|Preenche a tabela de dados associada do TableAdapter com os `SELECT` resultados do comando TableAdapter.|
|`TableAdapter.Update`|Envia alterações de volta ao banco de dados e retorna um inteiro que representa o número de linhas afetadas pela atualização. Para obter mais informações, consulte [Atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Retorna um <xref:System.Data.DataTable> novo que está cheio de dados.|
|`TableAdapter.Insert`|Cria uma nova linha na tabela de dados. Para obter mais informações, consulte [Inserir novos registros em um banco de dados](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Determina se uma tabela de dados é esvaziada antes de chamar um dos `Fill` métodos.|

## <a name="tableadapter-update-method"></a>Método de atualização tableAdapter

Os TableAdapters usam comandos de dados para ler e gravar no banco de dados. Use a consulta `Fill` inicial (principal) do TableAdapter como base para criar o esquema da `InsertCommand`tabela `UpdateCommand`de `DeleteCommand` dados associada, bem `TableAdapter.Update` como os , e comandos associados ao método. Chamar o método de `Update` um TableAdapter executa as instruções criadas quando o TableAdapter foi originalmente configurado, não uma das consultas adicionais que você adicionou com o **TableAdapter Query Configuration Wizard**.

Quando você usa um TableAdapter, ele efetivamente executa as mesmas operações com os comandos que você normalmente executaria. Por exemplo, quando você chama `Fill` o método do adaptador, o `SelectCommand` adaptador executa o comando <xref:System.Data.SqlClient.SqlDataReader>de dados em sua propriedade e usa um leitor de dados (por exemplo) para carregar o resultado definido na tabela de dados. Da mesma forma, quando você `Update` chama o método do adaptador, `InsertCommand`ele `DeleteCommand` executa o comando apropriado (no `UpdateCommand`, e propriedades) para cada registro alterado na tabela de dados.

> [!NOTE]
> Se houver informações suficientes na consulta `InsertCommand` `UpdateCommand`principal, `DeleteCommand` os comandos e comandos serão criados por padrão quando o TableAdapter for gerado. Se a consulta principal do TableAdapter for `SELECT` mais do que uma única declaração de `InsertCommand`tabela, é possível que o designer não seja capaz de gerar `UpdateCommand`, e `DeleteCommand`. Se esses comandos não forem gerados, você `TableAdapter.Update` pode receber um erro ao executar o método.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods

Além `InsertCommand`disso, `UpdateCommand`e `DeleteCommand`, TableAdapters são criados com métodos que você pode executar diretamente contra o banco de dados. Você pode chamar esses`TableAdapter.Insert` `TableAdapter.Update`métodos `TableAdapter.Delete`( , e ) diretamente para manipular dados no banco de dados. Isso significa que você pode chamar esses métodos individuais do seu código em vez de ligar `TableAdapter.Update` para lidar com as inserções, atualizações e exclusões que estão pendentes para a tabela de dados associada.

Se você não quiser criar esses métodos diretos, defina a propriedade **GenerateDbDirectMethods** do TableAdapter para `false` (na janela **Propriedades).** Consultas adicionais adicionadas ao TableAdapter são consultas autônomas — elas não geram esses métodos.

## <a name="tableadapter-support-for-nullable-types"></a>Suporte tableAdapter para tipos anulados

Os TableAdapters suportam tipos `Nullable(Of T)` anulados e `T?`. Para obter mais informações sobre tipos que permitem valor nulo no Visual Basic, consulte [Tipos de valores que permitem valor nulo](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Para obter mais informações sobre tipos anulados em C#, consulte [Usar tipos anulados](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Referência TableAdapterManager

Por padrão, uma classe TableAdapterManager gera quando você cria um conjunto de dados que contém tabelas relacionadas. Para evitar que a classe seja gerada, altere o valor da `Hierarchical Update` propriedade do conjunto de dados para falso. Quando você arrasta uma tabela que tem uma relação na superfície de design de uma página do Formulário windows ou WPF, o Visual Studio declara uma variável membro da classe. Se você não usar a vinculação de dados, você tem que declarar manualmente a variável.

A classe TableAdapterManager não é um tipo .NET. Portanto, você não pode procurá-lo na documentação. Ele é criado na hora do design como parte do processo de criação do conjunto de dados.

A seguir estão os métodos e `TableAdapterManager` propriedades mais utilizados da classe:

|Membro|Descrição|
|------------|-----------------|
|Método `UpdateAll`|Salva todos os dados de todas as tabelas de dados.|
|Propriedade `BackUpDataSetBeforeUpdate`|Determina se criará uma cópia de backup do `TableAdapterManager.UpdateAll` conjunto de dados antes de executar o método. Boolean.|
|*propriedade tableName* `TableAdapter`|Representa um TableAdapter. O TableAdapterManager gerado contém `TableAdapter` uma propriedade para cada um que ele gerencia. Por exemplo, um conjunto de dados com uma tabela Clientes `CustomersTableAdapter` `OrdersTableAdapter` e Pedidos gera com um TableAdapterManager que contém e propriedades.|
|Propriedade `UpdateOrder`|Controla a ordem dos comandos de inserção, atualização e exclusão individual. Defina isso como um `TableAdapterManager.UpdateOrderOption` dos valores da enumeração.<br /><br /> Por padrão, `UpdateOrder` o conjunto é definido como **InsertUpdateDelete**. Isso significa que as inserções, depois as atualizações e, em seguida, as exclusões são realizadas para todas as tabelas no conjunto de dados.|

## <a name="security"></a>Segurança

Quando você usa comandos de dados <xref:System.Data.CommandType.Text>com uma propriedade CommandType definida para, verifique cuidadosamente as informações enviadas de um cliente antes de passá-los para o seu banco de dados. Usuários maliciosos podem tentar enviar (injetar) instruções SQL modificadas ou adicionais para obter acesso não autorizado ou para danificar o banco de dados. Antes de transferir a entrada do usuário para um banco de dados, verifique sempre se as informações são válidas. Uma prática recomendada é sempre usar consultas parametrizadas ou procedimentos armazenados quando possível.

## <a name="see-also"></a>Confira também

- [Ferramentas de conjunto de dados](../data-tools/dataset-tools-in-visual-studio.md)
