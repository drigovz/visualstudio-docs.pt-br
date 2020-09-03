---
title: Adicionar código a TableAdapters em aplicativos de n camadas | Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 942850e776cdd493afaad56b782b417db2040625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673099"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Adicionar código a TableAdapters em aplicativos de n camadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode estender a funcionalidade de um `TableAdapter` criando um arquivo de classe parcial para o `TableAdapter` e adicionando código a ele (em vez de adicionar código ao *DataSetName*. Arquivo DataSet. Designer). As classes parciais permitem que o código de uma classe específica seja dividido entre vários arquivos físicos. Para obter mais informações, consulte [parcial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) ou [parcial (tipo)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

 O código que define um `TableAdapter` é gerado toda vez que as alterações são feitas no `TableAdapter` . Esse código também é gerado quando são feitas alterações durante a execução de qualquer assistente que modifica a configuração do `TableAdapter` . Para impedir que seu código seja excluído durante a regeneração de um `TableAdapter` , adicione o código ao arquivo de classe parcial do `TableAdapter` .

 Por padrão, depois de separar o DataSet e o `TableAdapter` código, o resultado é um arquivo de classe discreto em cada projeto. O projeto original tem um arquivo chamado *DataSetName*. Designer. vb (ou *DataSetName*. Designer.cs) que contém o `TableAdapter` código. O projeto designado na Propriedade Project de **DataSet** tem um arquivo chamado *DataSetName*. DataSet. designer. vb (ou *DataSetName*. DataSet.Designer.cs) que contém o código do conjunto de conteúdo.

> [!NOTE]
> Quando você separa DataSets e `TableAdapter` s (definindo a propriedade de **projeto DataSet** ), as classes parciais DataSet existentes no projeto não serão movidas automaticamente. As classes parciais de DataSet existentes devem ser movidas manualmente para o projeto do conjunto de um.

> [!NOTE]
> O DataSet Designer fornece a funcionalidade de geração <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> manipuladores de eventos quando a validação é necessária. Para obter mais informações, consulte [Adicionar validação a um conjunto](../data-tools/add-validation-to-an-n-tier-dataset.md)de dados de n camadas.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Para adicionar código de usuário a um TableAdapter em um aplicativo de n camadas

1. Localize o projeto que contém o arquivo. xsd (o DataSet).

2. Clique duas vezes no arquivo **. xsd** para abrir o conjunto de um.

3. Clique com o botão direito do mouse no `TableAdapter` que você deseja adicionar código e, em seguida, selecione**Exibir código**.

     Uma classe parcial é criada e aberta no editor de código.

4. Adicione o código dentro da declaração de classe parcial.

5. O exemplo a seguir mostra onde adicionar código ao `CustomersTableAdapter` no `NorthwindDataSet` :

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Consulte Também
 [Visão geral de aplicativos de dados de n camadas](../data-tools/n-tier-data-applications-overview.md) [: adicionar código a conjuntos de dados em aplicativos de n camadas](../data-tools/add-code-to-datasets-in-n-tier-applications.md) [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) [TableAdapterManager visão](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650) geral de [atualização hierárquica](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)