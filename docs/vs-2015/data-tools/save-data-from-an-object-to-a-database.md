---
title: Salvar dados de um objeto em um banco de dado | Microsoft Docs
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
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c1470c831177e74e7670d696b44fc2b0119a9a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607451"
---
# <a name="save-data-from-an-object-to-a-database"></a>Salvar dados de um objeto em um banco de dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode salvar dados em objetos em um banco de dado passando os valores do seu objeto para um dos métodos DBDirect do TableAdapter (por exemplo, `TableAdapter.Insert`).

 Para salvar dados de uma coleção de objetos, faça um loop através da coleção de objetos (por exemplo, um loop for-Next) e envie os valores para cada objeto para o banco de dados usando um dos métodos DBDirect do TableAdapter.

 Por padrão, os métodos DBDirect são criados em um TableAdapter que pode ser executado diretamente no banco de dados. Esses métodos podem ser chamados diretamente e não exigem <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> objetos para reconciliar as alterações a fim de enviar atualizações para um banco de dados.

> [!NOTE]
> Quando você estiver configurando um TableAdapter, a consulta principal deverá fornecer informações suficientes para que os métodos DBDirect sejam criados. Por exemplo, se um TableAdapter estiver configurado para consultar dados de uma tabela que não tem uma coluna de chave primária definida, ele não gerará métodos DBDirect.

|Métodos DBDirect TableAdapter|Descrição|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Adiciona novos registros a um banco de dados e permite que você passe valores de coluna individuais como parâmetros de método.|
|`TableAdapter.Update`|Atualiza os registros existentes em um banco de dados. O método `Update` usa valores originais e novos de coluna como parâmetros de método. Os valores originais são usados para localizar o registro original e os novos valores são usados para atualizar esse registro.<br /><br /> O método de `TableAdapter.Update` também é usado para reconciliar as alterações em um conjunto de dados de volta para o Database por meio de um <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> ou uma matriz de <xref:System.Data.DataRow>s como parâmetros de método.|
|`TableAdapter.Delete`|Exclui os registros existentes do banco de dados com base nos valores de coluna originais passados como parâmetros de método.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Para salvar novos registros de um objeto em um banco de dados

- Crie os registros passando os valores para o método `TableAdapter.Insert`.

     O exemplo a seguir cria um novo registro de cliente na tabela `Customers` passando os valores no objeto `currentCustomer` para o método `TableAdapter.Insert`.

     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Para atualizar os registros existentes de um objeto para um banco de dados

- Modifique os registros chamando o método `TableAdapter.Update`, passando os novos valores para atualizar o registro e passando os valores originais para localizar o registro.

    > [!NOTE]
    > Seu objeto precisa manter os valores originais para passá-los para o método `Update`. Este exemplo usa propriedades com um prefixo `orig` para armazenar os valores originais.

     O exemplo a seguir atualiza um registro existente na tabela `Customers` passando os valores novos e originais no objeto `Customer` para o método `TableAdapter.Update`.

     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]

### <a name="to-delete-existing-records-from-a-database"></a>Para excluir registros existentes de um banco de dados

- Exclua os registros chamando o método `TableAdapter.Delete` e passando os valores originais para localizar o registro.

    > [!NOTE]
    > Seu objeto precisa manter os valores originais para passá-los para o método `Delete`. Este exemplo usa propriedades com um prefixo `orig` para armazenar os valores originais.

     O exemplo a seguir exclui um registro da tabela `Customers` passando os valores originais no objeto `Customer` para o método `TableAdapter.Delete`.

     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]

## <a name="net-framework-security"></a>Segurança do .NET Framework
 Você deve ter permissão para executar a inserção, atualização ou exclusão selecionada na tabela no banco de dados.

## <a name="see-also"></a>Consulte também
 [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)
