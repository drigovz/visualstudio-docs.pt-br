---
title: Editar dados em DataSets | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 699ee9b6e7a68c6a79f7f7dac526127206e8aa42
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672397"
---
# <a name="edit-data-in-datasets"></a>Editar dados em conjuntos de dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você edita dados em tabelas de dados da mesma forma que edita os dados em uma tabela em qualquer banco de dado. O processo pode incluir inserção, atualização e exclusão de registros na tabela. Em um formulário vinculado a dados, você pode especificar quais campos são editáveis pelo usuário. Nesses casos, a infraestrutura de ligação de dados lida com todo o controle de alterações para que as alterações possam ser enviadas de volta para o banco mais tarde. Se você fizer edições programaticamente nos dados e pretende enviar essas alterações de volta ao banco de dado, deverá usar os objetos e métodos que fazem o controle de alterações para você.

 Além de alterar os dados reais, você também pode consultar um <xref:System.Data.DataTable> para retornar linhas específicas de dados. Por exemplo, você pode consultar linhas individuais, versões específicas de linhas (originais e propostas), linhas que foram alteradas ou linhas com erros.

## <a name="to-edit-rows-in-a-dataset"></a>Para editar linhas em um conjunto de registros
 Para editar uma linha existente em um <xref:System.Data.DataTable> , você precisa localizar o <xref:System.Data.DataRow> que deseja editar e, em seguida, atribuir os valores atualizados às colunas desejadas.

 Se você não souber o índice da linha que deseja editar, use o `FindBy` método para pesquisar pela chave primária:

 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]

 Se você souber o índice de linha, poderá acessar e editar as linhas da seguinte maneira:

 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Para inserir novas linhas em um conjunto de registros
 Os aplicativos que usam controles vinculados a dados normalmente adicionam novos registros por meio do botão **Adicionar novo** em um [controle BindingNavigator](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

 Para adicionar manualmente novos registros a um DataSet, crie uma nova linha de dados chamando o método na DataTable. Em seguida, adicione a linha à <xref:System.Data.DataRow> coleção ( <xref:System.Data.DataTable.Rows%2A> ) do <xref:System.Data.DataTable> :

 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]

 Para manter as informações que o conjunto de dados precisa para enviar atualizações para a fonte, use o <xref:System.Data.DataRow.Delete%2A> método para remover linhas em uma tabela de dados. Por exemplo, se seu aplicativo usa um TableAdapter (ou <xref:System.Data.Common.DataAdapter> ), o método do TableAdapter `Update` exclui linhas no banco de dados que têm um <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState> .

 Se seu aplicativo não precisar enviar atualizações de volta para uma fonte de dados, será possível remover os registros acessando diretamente a coleção de linhas de dados ( <xref:System.Data.DataRowCollection.Remove%2A> ).

#### <a name="to-delete-records-from-a-data-table"></a>Para excluir registros de uma tabela de dados

- Chame o <xref:System.Data.DataRow.Delete%2A> método de a <xref:System.Data.DataRow> .

     Esse método não remove fisicamente o registro. Em vez disso, ele marca o registro para exclusão.

    > [!NOTE]
    > Se você obtiver a propriedade Count de um <xref:System.Data.DataRowCollection> , a contagem resultante incluirá os registros que foram marcados para exclusão. Para obter uma contagem precisa de registros que não estão marcados para exclusão, você pode executar um loop na coleção examinando a <xref:System.Data.DataRow.RowState%2A> propriedade de cada registro. (Os registros marcados para exclusão têm um <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState> .) Como alternativa, você pode criar um modo de exibição de dados de um DataSet que filtra com base no estado de linha e obter a propriedade Count a partir daí.

     O exemplo a seguir mostra como chamar o <xref:System.Data.DataRow.Delete%2A> método para marcar a primeira linha na `Customers` tabela como excluída:

     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]

## <a name="determine-if-there-are-changed-rows"></a>Determinar se há linhas alteradas
 Quando são feitas alterações nos registros em um conjunto de dados, as informações sobre essas alterações são armazenadas até você confirmá-las. As alterações são confirmadas quando você chama o `AcceptChanges` método de um conjunto de dados ou de uma tabela data, ou quando você chama o `Update` método de um TableAdapter ou adaptador de dados.

 As alterações são controladas de duas maneiras em cada linha de dados:

- Cada linha de dados contém informações relacionadas a ele <xref:System.Data.DataRow.RowState%2A> (por exemplo,,, <xref:System.Data.DataRowState> <xref:System.Data.DataRowState> <xref:System.Data.DataRowState> ou <xref:System.Data.DataRowState> ).

- Cada linha de dados alterada contém várias versões dessa linha ( <xref:System.Data.DataRowVersion> ), a versão original (antes das alterações) e a versão atual (após as alterações). Durante o período em que uma alteração está pendente (a hora em que você pode responder ao <xref:System.Data.DataTable.RowChanging> evento), uma terceira versão — a versão proposta — também está disponível.

  O <xref:System.Data.DataSet.HasChanges%2A> método de um conjunto de um DataSet retorna `true` se foram feitas alterações no DataSet. Depois de determinar que as linhas alteradas existem, você pode chamar o `GetChanges` método de um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> retornar um conjunto de linhas alteradas. Para obter mais informações, consulte [como: recuperar linhas alteradas](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Para determinar se foram feitas alterações em qualquer linha

- Chame o <xref:System.Data.DataSet.HasChanges%2A> método de um conjunto de registros para verificar se há linhas alteradas.

     O exemplo a seguir mostra como verificar o valor de retorno do <xref:System.Data.DataSet.HasChanges%2A> método para detectar se há linhas alteradas em um conjunto de registros chamado `NorthwindDataset1` :

     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]

## <a name="determine-the-type-of-changes"></a>Determinar o tipo de alterações
 Você também pode verificar para ver quais tipos de alterações foram feitas em um conjunto de um DataSet, passando um valor da <xref:System.Data.DataRowState> enumeração para o <xref:System.Data.DataSet.HasChanges%2A> método.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Para determinar que tipo de alterações foram feitas em uma linha

- Passe um <xref:System.Data.DataRowState> valor para o <xref:System.Data.DataSet.HasChanges%2A> método.

     O exemplo a seguir mostra como verificar um conjunto de `NorthwindDataset1` registros chamado para determinar se alguma nova linha foi adicionada a ele:

     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]

## <a name="to-locate-rows-that-have-errors"></a>Para localizar linhas com erros
 Ao trabalhar com colunas individuais e linhas de dados, você pode encontrar erros. Você pode verificar a `HasErrors` propriedade para determinar se há erros em um <xref:System.Data.DataSet> , <xref:System.Data.DataTable> ou <xref:System.Data.DataRow> .

1. Verifique a `HasErrors` propriedade para ver se há erros no conjunto de os.

2. Se a `HasErrors` propriedade for `true` , itere pelas coleções de tabelas e, em seguida, as pelas linhas, para localizar a linha com o erro.

     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
