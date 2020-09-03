---
title: Separar conjuntos de linhas e TableAdapters em projetos diferentes | Microsoft Docs
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
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f6ec76e79cc1c4759cbe05d8bdcacc1297b655b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655431"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Conjuntos de dados e TableAdapters separados m diferentes projetos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os conjuntos de linhas tipados foram aprimorados para que as classes [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) e DataSet possam ser geradas em projetos separados. Isso permite que você separe rapidamente as camadas do aplicativo e gere aplicativos de dados de n camadas.

 O procedimento a seguir descreve o processo de usar o Designer de Conjunto de Dados para gerar código de conjunto de conteúdo em um projeto separado do projeto que contém o `TableAdapter` código gerado.

## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets e TableAdapters
 Quando você separa o código do DataSet do `TableAdapter` código, o projeto que contém o código do conjunto de conteúdo deve estar localizado na solução atual. Se esse projeto não estiver localizado na solução atual, ele não estará disponível na lista de **projetos DataSet** na janela **Propriedades** .

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Para separar o DataSet em um projeto diferente

1. Abra uma solução que contenha um conjunto de um (arquivo. xsd).

   > [!NOTE]
   > Se a solução não contiver o projeto no qual você deseja separar o código do conjunto de seus, crie o projeto ou adicione um projeto existente à solução.

2. Clique duas vezes em um arquivo de conjunto de arquivos digitado (um arquivo. xsd) em **Gerenciador de soluções** para abrir o conjunto de **Designer de conjunto de dados**.

3. Selecione uma área vazia da **Designer de conjunto de dados**.

4. Na janela **Propriedades** , localize o nó do **projeto DataSet** .

5. Na lista **projeto DataSet** , selecione o nome do projeto no qual você deseja gerar o código do conjunto de um.

    Depois de selecionar o projeto no qual você deseja gerar o código do conjunto de um, a propriedade do **arquivo DataSet** é populada com um nome de arquivo padrão. Você pode alterar esse nome, se necessário. Além disso, se você quiser gerar o código do conjunto de informações em um diretório específico, poderá definir a propriedade **pasta do projeto** como o nome de uma pasta.

   > [!NOTE]
   > Quando você separa DataSets e TableAdapters (definindo a propriedade de **projeto DataSet** ), as classes parciais DataSet existentes no projeto não serão movidas automaticamente. As classes parciais de DataSet existentes devem ser movidas manualmente para o projeto do conjunto de um.

6. Salve o conjunto de um.

    O código do conjunto de um é gerado no projeto selecionado na propriedade de **projeto DataSet** e o código **TableAdapter** é gerado para o projeto atual.

   Por padrão, depois de separar o DataSet e o `TableAdapter` código, o resultado é um arquivo de classe discreto em cada projeto. O projeto original tem um arquivo chamado DataSetName. designer. vb (ou DatasetName.Designer.cs) que contém o `TableAdapter` código. O projeto designado na Propriedade Project do **conjunto** de conteúdo tem um arquivo chamado DataSetName. DataSet. designer. vb (ou DataSetName.DataSet.designer.cs) que contém o código do conjunto de conteúdo.

> [!NOTE]
> Para exibir o arquivo de classe gerado, selecione o DataSet ou o `TableAdapter` projeto. Em seguida, em  **Gerenciador de soluções**, selecione **Mostrar todos os arquivos** .

## <a name="see-also"></a>Consulte Também
 [Visão geral dos aplicativos de dados de n camadas](../data-tools/n-tier-data-applications-overview.md) – [criando uma](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [atualização hierárquica](../data-tools/hierarchical-update.md) de aplicativo de dados de n camadas [acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [ADO.net](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)
