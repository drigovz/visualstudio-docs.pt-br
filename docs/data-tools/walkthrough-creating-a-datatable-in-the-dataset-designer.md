---
title: 'Instruções passo a passo: criando um DataTable no Designer de Conjunto de Dados'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1526a5f4137ece5b76c282255af3da4ab20ac119
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585997"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Walkthrough: criar uma DataTable no Designer de Conjunto de Dados

Este tutorial explica como criar um <xref:System.Data.DataTable> (sem um TableAdapter) usando o **Designer de conjunto de dados**. Para obter informações sobre como criar tabelas de dados que incluem TableAdapters, consulte [criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Criar um novo Aplicativo do Windows Forms

1. No Visual Studio, no menu **Arquivo**, selecione **Novo** > **Projeto**.

2. Expanda **o C# Visual** ou **Visual Basic** no painel esquerdo e, em seguida, selecione **área de trabalho do Windows**.

3. No painel central, selecione o tipo de projeto **Windows Forms aplicativo** .

4. Nomeie o projeto **DataTableWalkthrough**e escolha **OK**.

     O projeto **DataTableWalkthrough** é criado e adicionado ao **Gerenciador de soluções**.

## <a name="add-a-new-dataset-to-the-application"></a>Adicionar um novo conjunto de aplicativos ao aplicativo

1. No menu **Projeto**, selecione **Adicionar Novo Item**.

     A caixa de diálogo **Adicionar Novo Item** é exibida.

2. No painel esquerdo, selecione **dados**e, em seguida, selecione **DataSet** no painel central.

3. Escolha **Adicionar**.

     O Visual Studio adiciona um arquivo chamado **dataSet1. xsd** ao projeto e o abre no **Designer de conjunto de dados**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Adicionar uma nova DataTable ao DataSet

1. Arraste uma **DataTable** da guia **DataSet** da caixa de **ferramentas** para a **Designer de conjunto de dados**.

     Uma tabela chamada **dataTable1** é adicionada ao DataSet.

2. Clique na barra de título de **dataTable1** e renomeie-a `Music`.

## <a name="add-columns-to-the-datatable"></a>Adicionar colunas à DataTable

1. Clique com o botão direito do mouse na tabela **música** . Aponte para **Adicionar**e clique em **coluna**.

2. Nomeie a coluna `SongID`.

3. Na janela **Propriedades** , defina a propriedade <xref:System.Data.DataColumn.DataType%2A> como <xref:System.Int16?displayProperty=fullName>.

4. Repita esse processo e adicione as seguintes colunas:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Definir a chave primária para a tabela

Todas as tabelas de dados devem ter uma chave primária. Uma chave primária identifica exclusivamente um registro específico em uma tabela de dados.

Para definir a chave primária, clique com o botão direito do mouse na coluna **SongID** e clique em **definir chave primária**. Um ícone de chave é exibido ao lado da coluna **SongID** .

## <a name="save-your-project"></a>Salvar o projeto

Para salvar o projeto **DataTableWalkthrough** , no menu **arquivo** , selecione **salvar tudo**.

## <a name="see-also"></a>Veja também

- [Criar e configurar conjuntos de dados no Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validando dados](../data-tools/validate-data-in-datasets.md)
