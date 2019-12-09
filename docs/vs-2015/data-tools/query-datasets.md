---
title: Consultar conjuntos de os | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ccd5deffb0127769e2cd9dff3bf2accf75617eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607446"
---
# <a name="query-datasets"></a>Consultar conjuntos de dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para pesquisar registros específicos em um conjunto de informações, use o método FindBy na DataTable, escreva seu próprio loop foreach sobre a coleção Rows da tabela ou use [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17). LINQ to DataSet.

## <a name="dataset-case-sensitivity"></a>Diferenciação de maiúsculas e minúsculas
 Em um conjunto de dados, os nomes de tabela e coluna não diferenciam maiúsculas de minúsculas por padrão — ou seja, uma tabela em um conjunto de dados chamada "Customers" também pode ser referida como "Customers". Isso corresponde às convenções de nomenclatura em vários bancos de dados, incluindo o SQL Server.In SQL Server, o comportamento padrão é que os nomes dos elementos de dados não podem ser diferenciados somente por maiúsculas e minúsculas.

> [!NOTE]
> Ao contrário dos conjuntos de dados, os documentos XML diferenciam maiúsculas de minúsculas e, portanto, os nomes dos elementos de dado definidos em esquemas diferenciam maiúsculas de minúsculas. Por exemplo, o protocolo de esquema permite que o esquema defina uma tabela chamada "Customers" e uma tabela diferente chamada "Customers". Isso pode resultar em colisões de nome quando um esquema que contém elementos que diferem somente por maiúsculas e minúsculas é usado para gerar uma classe de conjunto de resultados.

 No entanto, a diferenciação de maiúsculas e minúsculas pode ser um fator em como os dados são interpretados no DataSet. Por exemplo, se você filtrar dados em uma tabela de DataSet, os critérios de pesquisa poderão retornar resultados diferentes, dependendo se a comparação diferencia maiúsculas de minúsculas. Você pode controlar a diferenciação de maiúsculas e minúsculas de filtragem, pesquisa e classificação definindo a propriedade de <xref:System.Data.DataSet.CaseSensitive%2A> do conjunto de propriedades. Todas as tabelas no conjunto de um DataSet herdam o valor dessa propriedade por padrão. (Você pode substituir essa propriedade para cada tabela individual definindo a propriedade de <xref:System.Data.DataTable.CaseSensitive%2A> da tabela.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Localizar uma linha específica em uma tabela de dados

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Para localizar uma linha em um dataset tipado com um valor de chave primária

- Para localizar uma linha, chame o método de `FindBy` fortemente tipado que usa a chave primária da tabela.

     No exemplo a seguir, a coluna `CustomerID` é a chave primária da tabela `Customers`. Isso significa que o método `FindBy` gerado é `FindByCustomerID`. O exemplo mostra como atribuir um <xref:System.Data.DataRow> específico a uma variável usando o método `FindBy` gerado.

     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Para localizar uma linha em um conjunto de um DataSet não tipado com um valor de chave primária

- Chame o método <xref:System.Data.DataRowCollection.Find%2A> de uma coleção de <xref:System.Data.DataRowCollection>, passando a chave primária como um parâmetro.

     O exemplo a seguir mostra como declarar uma nova linha chamada `foundRow` e atribuir a ela o valor de retorno do método <xref:System.Data.DataRowCollection.Find%2A>. Se a chave primária for encontrada, o conteúdo do índice de coluna 1 será exibido em uma caixa de mensagem.

     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]

## <a name="findrows-by-column-values"></a>FindRows por valores de coluna

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Para localizar linhas com base nos valores de qualquer coluna

- As tabelas de dados são criadas com o método <xref:System.Data.DataTable.Select%2A>, que retorna uma matriz de <xref:System.Data.DataRow>s com base na expressão passada para o método <xref:System.Data.DataTable.Select%2A>. Para obter mais informações sobre como criar expressões válidas, consulte a seção "sintaxe de expressão" da página sobre a propriedade <xref:System.Data.DataColumn.Expression%2A>.

     O exemplo a seguir mostra como usar o método <xref:System.Data.DataTable.Select%2A> da <xref:System.Data.DataTable> para localizar linhas específicas.

     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]

## <a name="access-related-records"></a>Acessar registros relacionados
 Quando as tabelas em um conjunto de registros estão relacionadas, um objeto <xref:System.Data.DataRelation> pode tornar os registros relacionados disponíveis em outra tabela. Por exemplo, um conjunto de um DataSet contendo `Customers` e `Orders` tabelas podem ser disponibilizados.

 Você pode usar um objeto <xref:System.Data.DataRelation> para localizar registros relacionados chamando o método <xref:System.Data.DataRow.GetChildRows%2A> de um <xref:System.Data.DataRow> na tabela pai. Esse método retorna uma matriz de registros filho relacionados. Ou você pode chamar o método <xref:System.Data.DataRow.GetParentRow%2A> de um <xref:System.Data.DataRow> na tabela filho. Esse método retorna uma única <xref:System.Data.DataRow> da tabela pai.

 Esta página fornece exemplos usando datasets tipados. Para obter informações sobre como navegar em relações em conjuntos de dados não tipados, consulte [navegando em DataRelations](https://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).

> [!NOTE]
> Se você estiver trabalhando em um aplicativo Windows Forms e usando os recursos de vinculação de dados para exibir dados, o formulário gerado pelo designer poderá fornecer funcionalidade suficiente para seu aplicativo. Para obter mais informações, confira [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

 Os exemplos de código a seguir demonstram como navegar pelas relações para cima e para baixo em conjuntos de valores tipados. Os exemplos de código usam <xref:System.Data.DataRow>s tipados (`NorthwindDataSet.OrdersRow`) e os métodos de `FindBy`*PrimaryKey* (`FindByCustomerID`) gerados para localizar uma linha desejada e retornar os registros relacionados. Os exemplos são compilados e executados corretamente somente se você tiver:

- Uma instância de um conjunto de uma chamada `NorthwindDataSet` com uma tabela `Customers`.

- Uma tabela `Orders`.

- Uma relação chamada `FK_Orders_Customers`relating as duas tabelas disponíveis para o escopo do seu código

Além disso, ambas as tabelas precisam ser preenchidas com dados para que todos os registros sejam retornados.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Para retornar os registros filho de um registro pai selecionado

- Chame o método <xref:System.Data.DataRow.GetChildRows%2A> de uma linha de dados de `Customers` específica e retorne uma matriz de linhas da tabela `Orders`:

     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Para retornar o registro pai de um registro filho selecionado

- Chame o método <xref:System.Data.DataRow.GetParentRow%2A> de uma linha de dados de `Orders` específica e retorne uma única linha da tabela `Customers`:

     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]
