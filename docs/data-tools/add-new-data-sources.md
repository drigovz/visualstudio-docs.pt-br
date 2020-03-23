---
title: Adicionar novas fontes de dados
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 555d32eb295e944060d2efe0b843e9d157b7c675
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302248"
---
# <a name="add-new-data-sources"></a>Adicionar novas fontes de dados

No contexto das ferramentas de dados .NET no Visual Studio, o termo fonte de *dados* refere-se a objetos .NET que se conectam a um armazenamento de dados e disponibilizam os dados para um aplicativo .NET. Os designers do Visual Studio podem consumir a saída da fonte de dados para gerar o código da caldeira que liga os dados aos formulários quando você arrasta e solta objetos de banco de dados da janela Fontes de **dados.** Esse tipo de fonte de dados pode ser:

- Uma classe em um modelo de Framework de entidade que está associada a algum tipo de banco de dados.

- Um conjunto de dados que está associado a algum tipo de banco de dados.

- Uma classe que representa um serviço de rede, como um serviço de dados da Windows Communication Foundation (WCF) ou um serviço REST.

- Uma classe que representa um serviço SharePoint.

- Uma classe ou coleção em sua solução.

> [!NOTE]
> Se você não estiver usando recursos de vinculação de dados, conjuntos de dados, Entity Framework, LINQ para SQL, WCF ou SharePoint, o conceito de "fonte de dados" não se aplica. Basta conectar-se diretamente ao banco de dados usando os objetos SQLCommand e comunicar-se diretamente com o banco de dados.

Você cria e edita fontes de dados usando o **Assistente de Configuração de Fonte de Dados** em um aplicativo do Windows Forms ou do Windows Presentation Foundation. Para O Framework da entidade, primeiro crie suas classes de entidade e, em seguida, inicie o assistente selecionando **Project** > **Add New Data Source** (descrito com mais detalhes mais tarde neste artigo).

![Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>janela Fontes de Dados

Depois de criar uma fonte de dados, ele aparece na janela da ferramenta **Fontes de dados.**

> [!TIP]
> Para abrir a janela **Fontes de dados,** certifique-se de que seu projeto está aberto e pressione **Shift**+**Alt**+**D** ou escolha **Exibir** > **outras** > fontes de**dados do**Windows .

Você pode arrastar uma fonte de dados da janela Fontes de **dados** para uma superfície ou controle de design de formulário. Isso faz com que o código da caldeira seja gerado que exibe os dados do armazenamento de dados.

A ilustração a seguir mostra um conjunto de dados que foi lançado em um formulário do Windows. Se você selecionar **F5** no aplicativo, os dados do banco de dados subjacente aparecerão nos controles do formulário.

![Operação de arrasto de origem de dados](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Fonte de dados para um banco de dados ou um arquivo de banco de dados

Você pode criar um conjunto de dados ou um modelo de Framework de entidade para usar como fonte de dados para um banco de dados ou arquivo de banco de dados.

### <a name="dataset"></a>Dataset

Para criar um conjunto de dados como fonte de dados, execute o **Assistente de Configuração de Origem de Dados** selecionando **Project** > **Add New Data Source**. Escolha o tipo de origem de dados do banco de **dados** e siga as instruções para especificar uma conexão de banco de dados nova ou existente ou um arquivo de banco de dados.

### <a name="entity-classes"></a>Classes de entidades

Para criar um modelo framework de entidade como fonte de dados:

1. Execute o **Assistente de Modelo de Dados da Entidade** para criar as classes da entidade. Selecione **Projeto** > **Adicionar novo item** > ADO.NET modelo de dados da**entidade**.

   ![Novo item do projeto do modelo do Framework da entidade](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Escolha o método que deseja gerar o modelo.

   ![Assistente de modelo de dados da entidade](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Adicione o modelo como fonte de dados. As classes geradas aparecem no **Assistente de configuração de origem de dados** quando você escolhe a categoria **Objetos.**

   ![Assistente de configuração de origem de dados com classes de entidade](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Fonte de dados para um serviço

Para criar uma fonte de dados a partir de um serviço, execute o Assistente de **Configuração de Origem de Dados** e escolha o tipo de fonte de dados do **Serviço.** Este é apenas um atalho para a caixa de diálogo Adicionar referência de **serviço,** que você também pode acessar clicando com o botão direito do mouse no projeto no **Solution Explorer** e selecionando **Adicionar referência de serviço**.

Quando você cria uma fonte de dados de um serviço, o Visual Studio adiciona uma referência de serviço ao seu projeto. O Visual Studio também cria objetos proxy que correspondem aos objetos que o serviço retorna. Por exemplo, um serviço que retorna um conjunto de dados é representado em seu projeto como um conjunto de dados; um serviço que retorna um tipo específico é representado em seu projeto à medida que o tipo retornado.

Você pode criar uma fonte de dados a partir dos seguintes tipos de serviços:

- [Serviços de dados WCF](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Serviços wcf](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- SERVIÇOS WEB

    > [!NOTE]
    > Os itens que aparecem na janela **Fontes de dados** dependem dos dados que o serviço retorna. Alguns serviços podem não fornecer informações suficientes para o **Assistente de Configuração de Fonte de Dados** criar objetos associáveis. Por exemplo, se o serviço retornar um conjunto de dados não digitado, nenhum item aparecerá na janela **Fontes de dados** quando você concluir o assistente. Isso porque conjuntos de dados não digitados não fornecem um esquema e, portanto, o assistente não tem informações suficientes para criar a fonte de dados.

## <a name="data-source-for-an-object"></a>Fonte de dados de um objeto

Você pode criar uma fonte de dados a partir de qualquer objeto que exponha uma ou mais propriedades públicas executando o **Assistente de Configuração de Origem de Dados** e, em seguida, selecionando o tipo de origem de dados do **Objeto.** Todas as propriedades públicas de um objeto são exibidas na janela **Fontes de dados.** Se você estiver usando o Entity Framework e tiver gerado um modelo, é aqui que você encontra as classes de entidade que são as fontes de dados para o seu aplicativo.

Na **página Selecionar objetos de dados,** expanda os nós na exibição da árvore para localizar os objetos aos que você deseja vincular. A visão da árvore contém nós para o seu projeto e para montagens e outros projetos que são referenciados pelo seu projeto.

Se você quiser vincular a um objeto em um conjunto ou projeto que não apareça na exibição da árvore, clique em **Adicionar referência** e use a Caixa de diálogo **Adicionar referência** para adicionar uma referência ao conjunto ou projeto. Depois de adicionar a referência, a montagem ou projeto é adicionado à visualização da árvore.

> [!NOTE]
> Você pode precisar construir o projeto que contém seus objetos antes que os objetos apareçam na exibição da árvore.

> [!NOTE]
> Para suportar a vinculação de dados de <xref:System.ComponentModel.ITypedList> <xref:System.ComponentModel.IListSource> arrastar e soltar, os objetos que implementam a interface devem ter um construtor padrão. Caso contrário, o Visual Studio não pode instanciar o objeto de origem de dados e exibe um erro ao arrastar o item para a superfície do design.

## <a name="data-source-for-a-sharepoint-list"></a>Fonte de dados para uma lista sharePoint

Você pode criar uma fonte de dados a partir de uma lista do SharePoint executando o **Assistente de Configuração de Origem de Dados** e selecionando o tipo de origem de dados do **SharePoint.** O SharePoint expõe dados através do WCF Data Services, portanto, criar uma fonte de dados do SharePoint é o mesmo que criar uma fonte de dados a partir de um serviço. Selecionar o item **SharePoint** na **Assistente de Configuração de Origem de Dados** abre a caixa de diálogo Adicionar referência de **serviço,** onde você se conecta ao serviço de dados SharePoint apontando para o servidor SharePoint. Isso requer o SharePoint SDK.

## <a name="see-also"></a>Confira também

- [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
