---
title: Atualizar dados usando um TableAdapter | Microsoft Docs
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
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 312bf75100d2b9b270b45776c5f7ded21ab6ac52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72602330"
---
# <a name="update-data-by-using-a-tableadapter"></a>Atualizar dados usando um TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Depois que os dados em seu DataSet forem modificados e validados, você poderá enviar os dados atualizados de volta para um databaseby chamando o `Update` método de um TableAdapter. O `Update` método atualiza uma única tabela de dados e executa o comando correto (INSERT, Update ou Delete) com base em <xref:System.Data.DataRow.RowState%2A> cada linha de dados na tabela. Quando um conjunto de um DataSet tem tabelas relacionadas, o Visual Studio gera uma classe TableAdaptermanager que você usa para fazer as atualizações. A classe TableAdaptermanager garante que as atualizações sejam feitas na ordem correta com base nas restrições de chave estrangeira definidas no banco de dados. Quando você usa controles vinculados a dados, a arquitetura DataBinding cria uma variável de membro da classe TableAdaptermanager chamada tableAdaptermanager. Para obter mais informações, consulte [visão geral da atualização hierárquica](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).

> [!NOTE]
> Quando você tenta atualizar uma fonte de dados com o conteúdo de um conjunto, você pode obter erros. Para evitar erros, recomendamos que thatyou Coloque o código que chama o método do adaptador `Update` dentro de um `try` / `catch` bloco.

 O procedimento exato para atualizar uma fonte de dados pode variar dependendo das necessidades dos negócios, mas inclui as seguintes etapas:

1. Chame o método do adaptador `Update` em um `try` / `catch` bloco.

2. Se uma exceção for detectada, localize a linha de dados que causou o erro. Para obter mais informações, consulte [como localizar linhas com erros](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).

3. Reconcilie o problema na linha de dados (programaticamente se você puder, ou apresentando a linha inválida para o usuário para modificação) e tente a atualização novamente ( <xref:System.Data.DataRow.HasErrors%2A> , <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="savedata-to-a-database"></a>SaveData a um banco de dados
 Chame o `Update` método de um TableAdapter. Passe o nome da tabela de dados que contém os valores a serem gravados no banco de dado.

#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Para atualizar um banco de dados usando um TableAdapter

- Coloque o método do TableAdapter `Update` em um `try` / `catch` bloco. O exemplo a seguir mostra como atualizar o conteúdo da `Customers` tabela no `NorthwindDataSet` de dentro de um `try` / `catch` bloco.

     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]

## <a name="see-also"></a>Consulte Também
 [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)
