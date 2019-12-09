---
title: Adicionar código a conjuntos de itens em aplicativos de n camadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aed37ee9cdd8c221fcfb114db426a6286ee8ad6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673112"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Adicionar código a conjuntos de dados em aplicativos de n camadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode estender a funcionalidade de um conjunto de um DataSet criando um arquivo de classe parcial para o conjunto de recursos e adicionando código a ele (em vez de adicionar código ao *DataSetName*. Arquivo DataSet. Designer). As classes parciais permitem que o código de uma classe específica seja dividido entre vários arquivos físicos. Para obter mais informações, consulte [classes e métodos](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1) [parciais](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) ou parciais.

O código que define um conjunto de um DataSet é gerado toda vez que são feitas alterações na definição do conjunto de conjuntos. Esse código também é gerado quando você faz alterações durante a execução de qualquer assistente que modifica a configuração de um conjunto de uma. Para impedir que seu código seja excluído durante a regeneração de um conjunto de um DataSet, adicione o código ao arquivo de classe parcial do conjunto de um.

Por padrão, depois de separar o conjunto de resultados e `TableAdapter` código, o resultado é um arquivo de classe discreto em cada projeto. O projeto original tem um *DataSetName*de nome de um. Designer. vb (ou *DataSetName*. Designer.cs) que contém o código `TableAdapter`. O projeto designado na Propriedade Project de **DataSet** tem um arquivo chamado *DataSetName*. DataSet. designer. vb (ou *DataSetName*. DataSet.Designer.cs). Esse arquivo contém o código do conjunto de conteúdo.

> [!NOTE]
> Quando você separa conjuntos de valores e `TableAdapter`s (definindo a propriedade de **projeto DataSet** ), as classes parciais DataSet existentes no projeto não serão movidas automaticamente. As classes parciais de DataSet existentes devem ser movidas manualmente para o projeto do conjunto de um.

> [!NOTE]
> Quando o código de validação precisa ser adicionado, o DataSet Designer fornece a funcionalidade para gerar <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> manipuladores de eventos. Para obter mais informações, consulte [Adicionar validação a um conjunto](../data-tools/add-validation-to-an-n-tier-dataset.md)de dados de n camadas.

## <a name="add-code-to-datasets-in-n-tier-applications"></a>Adicionar código a conjuntos de dados em aplicativos de n camadas

1. Localize o projeto que contém o arquivo. xsd (o DataSet).

2. Selecione o arquivo **. xsd** para abrir o conjunto de um.

3. Clique com o botão direito do mouse na tabela de dados à qual você deseja adicionar o código (o nome da tabela na barra de título) e, em seguida, selecione **Exibir código**.

     Uma classe parcial é criada e aberta no editor de código.

4. Adicione o código dentro da declaração de classe parcial.

     O exemplo a seguir mostra onde adicionar código ao CustomersDataTable no NorthwindDataSet:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Consulte também

- [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md)
- [Adicionar código a TableAdapters em aplicativos de N camadas](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [Visão geral do TableAdaptermanager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [Visão geral da atualização hierárquica](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)