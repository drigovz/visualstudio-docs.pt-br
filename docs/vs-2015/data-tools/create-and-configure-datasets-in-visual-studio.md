---
title: Criar e configurar conjuntos de dados
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
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c84105387c708fa16e0b1d5c3294ef909466524
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72631201"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Criar e configurar conjuntos de dados no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um *DataSet* é um conjunto de objetos que armazenam dados de um Database na memória e dão suporte ao controle de alterações para permitir operações de criação, leitura, atualização e exclusão (CRUD) nesses dados sem a necessidade de sempre estar conectado ao banco de dado. Os conjuntos de dados foram projetados para *formulários simples em* aplicativos de negócios de data. Para novos aplicativos, considere o uso de Entity Framework para armazenar e modelar dados na memória. Para trabalhar com conjuntos de dados, você deve ter um conhecimento básico dos conceitos de banco de dados.

 Você cria uma classe tipada <xref:System.Data.DataSet> no Visual Studio em tempo de design usando o **Assistente de configuração de fonte de dados**. Para obter informações sobre como criar conjuntos de dados programaticamente, consulte [criando um conjunto de](https://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc)dados.

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Criar um novo conjunto de dados usando o assistente de configuração de fonte de dados

1. No menu **projeto** , clique em **Adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.

2. Escolha o tipo de fonte de dados ao qual você estará se conectando.

     ![Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png "Assistente para Configuração da Fonte de Dados")

3. Para bancos de dados, escolha o banco de dados ou os bancos de dados que serão a fonte de dado para o seu DataSet.

     ![Fonte de dados escolha uma conexão](../data-tools/media/data-source-choose-a-connection.png "Fonte de dados escolha uma conexão")

4. Escolha as tabelas (ou colunas individuais), procedimentos armazenados, funções e exibições do banco de dados que você deseja que sejam representadas no DataSet.

     ![Escolher objetos de banco de dados](../data-tools/media/raddata-chose-objects.png "raddata escolheu objetos")

5. Clique em **Concluir**.

6. O conjunto de um é exibido como um nó no **Gerenciador de soluções**:

     ![Conjunto de Gerenciador de Soluções](../data-tools/media/dataset-in-solution-explorer.png "Conjunto de Gerenciador de Soluções")

     Clique nesse nó e o DataSet aparecerá no **DataSet Designer**. Observe que cada tabela no conjunto de resultados tem um objeto TableAdapter associado, que é representado na parte inferior. O adaptador de tabela é usado para popular o conjunto de dados e, opcionalmente, para enviar comandos para o Database.

     ![Designer de Conjunto de Dados](../data-tools/media/dataset-designer.png "Designer de Conjunto de Dados")

7. As linhas de relação que conectam as tabelas representam relações de tabela, conforme definido no banco de dados. Por padrão, as restrições Foreign-Key em um banco de dados são representadas somente como uma relação, com as regras Update e Delete definidas como None. Normalmente, isso é o que você deseja. No entanto, você pode clicar nas linhas para abrir a caixa de diálogo de **relação** , na qual você pode alterar o comportamento de atualizações hierárquicas. Para obter mais informações, consulte [relações em conjuntos de](../data-tools/relationships-in-datasets.md) dados e [atualização hierárquica](../data-tools/hierarchical-update.md).

     ![Caixa de diálogo relação entre conjuntos de conjunto](../data-tools/media/raddata-relation-dialog.png "caixa de diálogo raddata relation")

8. Clique em uma tabela, um adaptador de tabela ou um nome de coluna em uma tabela para ver suas propriedades na janela **Propriedades** . Você pode modificar alguns dos valores aqui. Apenas lembre-se de que você está modificando o conjunto de dados, não o banco de dados de origem.

     ![Propriedades da coluna DataSet](../data-tools/media/dataset-column-properties.png "Propriedades da coluna DataSet")

9. Você pode adicionar novas tabelas ou adaptadores de tabela ao conjunto de recursos ou adicionar novas consultas para adaptadores de tabela existentes ou especificar novas relações entre tabelas arrastando esses itens da guia **caixa de ferramentas** . Essa guia aparece quando o **Designer de conjunto** de os está em foco.

     ![Caixa de ferramentas de DataSet](../data-tools/media/raddata-dataset-toolbox.png "Caixa de ferramentas do conjunto de raddata")

10. Em seguida, você provavelmente desejará especificar como popular o conjunto de dados. Para isso, você usa o **Assistente de configuração do TableAdapter**. Para obter mais informações, consulte [preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Adicionar uma tabela de banco de dados ou outro objeto a um conjunto de dados existente
 Este procedimento mostra como adicionar uma tabela do mesmo banco de dados que você usou para primeiro criar o conjunto.

1. Clique no nó DataSet em **Gerenciador de soluções** para colocar o designer de conjunto de DataSet em foco.

2. Clique na guia **fontes de dados** na margem esquerda do Visual Studio ou digite `Data Sources` na **inicialização rápida**.

3. Clique com o botão direito do mouse no nó do conjunto de dados e selecione **Configure Data Source com o assistente** .

     ![Menu de contexto da fonte de dados](../data-tools/media/data-source-context-menu.png "Menu de contexto da fonte de dados")

4. Use o assistente para especificar quais tabelas adicionais, ou procedimentos armazenados ou outro objeto de banco de dados, adicionar ao DataSet.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Adicionar uma tabela de dados autônoma a um DataSet

1. Abra o conjunto de dados no **Designer de Conjunto de Dados**.

2. Arraste uma <xref:System.Data.DataTable> classe da guia **DataSet** da caixa de **ferramentas** para a **Designer de conjunto de dados**.

3. Adicione colunas para definir a tabela de dados. Para obter mais informações, consulte [como: adicionar colunas a uma DataTable](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4. Tabelas autônomas precisam implementar a `Fill` lógica em tabelas autônomas para que você possa preenchê-las com dados. Para obter informações sobre como preencher tabelas de dados autônomas, consulte [Populando um DataSet de um DataAdapter](https://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
