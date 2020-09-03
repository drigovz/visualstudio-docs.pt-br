---
title: Adicionar novas fontes de dados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85c07ad7995bc614df4b988bb17fa8977452b5d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673062"
---
# <a name="add-new-data-sources"></a>Adicionar novas fontes de dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No contexto do .NET Data Tools no Visual Studio, o termo *fonte de dados* refere-se aos objetos .NET que se conectam a um repositório de dados e expõem os dados a um aplicativo .net. Os designers do Visual Studio podem consumir a saída da fonte de dados para gerar o código clichê que associa os dados a formulários quando você arrasta e solta objetos de banco de **dados da janela Data Sources** . Esse tipo de fonte de dados pode ser:

- Uma classe em um modelo de Entity Framework que está associado a algum tipo de banco de dados.

- Um DataSet associado a algum tipo de banco de dados.

- Uma classe que representa um serviço de rede, como um serviço de dados Windows Communication Foundation (WCF) ou um serviço REST.

- Uma classe que representa um serviço do SharePoint.

- Uma classe ou coleção em sua solução.

> [!NOTE]
> Se você não estiver usando recursos de vinculação de dados, DataSets, Entity Framework, LINQ to SQL, WCF ou SharePoint, o conceito de uma "fonte de dados" não se aplicará. Basta conectar-se diretamente ao banco de dados usando os objetos SQLCommand e se comunicar diretamente com o banco de dados.

 Você cria e edita fontes de dados usando o **Assistente de configuração de fonte de dados** em um aplicativo Windows Forms ou Windows Presentation Foundation. Para Entity Framework, primeiro crie suas classes de entidade e inicie o assistente selecionando **projeto**  >  **Adicionar nova fonte de dados** (descrito em mais detalhes mais adiante neste artigo).

 ![Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png "Assistente para Configuração da Fonte de Dados")

 Depois de criar uma fonte de dados, ela aparecerá na janela de ferramentas de **fontes de dados** (Shift + Alt + D ou **Exibir**  >  **outra**  >  **fonte de dados**do Windows). Você pode arrastar uma fonte de dados da janela **fontes de dados** para um controle ou superfície de design de formulário. Isso faz com que o código clichê seja gerado — o código que exibe os dados originados no armazenamento de dados para o usuário. A ilustração a seguir mostra um conjunto de um DataSet que foi descartado em um formulário do Windows. Se você tiver selecionado F5 no aplicativo, os dados do banco de dado subjacente aparecerão nos controles do formulário.

 ![Operação de arrastar da fonte de dados](../data-tools/media/raddata-data-source-drag-operation.png "operação de arrastar da fonte de dados raddata")

## <a name="data-source-for-a-database-or-a-database-file"></a>Fonte de dados para um banco de dado ou um arquivo de banco

### <a name="dataset"></a>Dataset
 Para criar um DataSet como uma fonte de dados, execute o **Assistente de configuração da fonte de dados** (**projeto**  >  **Adicionar nova** fonte de dados) e escolha o tipo de fonte de dados do **banco** . Siga os prompts para especificar uma conexão de banco de dados nova ou existente ou um arquivo de banco de dados.

### <a name="entity-classes"></a>Classes de entidade
 Para criar um modelo de Entity Framework como uma fonte de dados, primeiro execute o **Assistente de modelo de dados de entidade** para criar as classes de entidade (**projeto**  >  **Adicionar novo item**  >  **ADO.NET modelo de dados de entidade**).

 ![Novo item de projeto de modelo de Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata novo item de projeto de modelo de Entity Framework")

 Escolha o método pelo qual você deseja gerar o modelo.

 ![Assistente de Modelo de Dados de Entidade](../data-tools/media/raddata-entity-data-model-wizard.png "Assistente de Modelo de Dados de Entidade de raddata")

 Adicione o modelo como uma fonte de dados. As classes que foram geradas aparecem no **Assistente de configuração da fonte de dados** quando você escolhe a categoria **objetos** .

 ![Assistente de configuração de fonte de dados com classes de entidade](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "Assistente de configuração da fonte de dados do raddata com classes de entidade")

## <a name="data-source-for-a-service"></a>Fonte de dados para um serviço
 Para criar uma fonte de dados de um serviço, execute o **Assistente de configuração de fonte de dados** e escolha o tipo de fonte de dados de **serviço** . Isso é, na verdade, apenas um atalho para a caixa de diálogo **Adicionar referência de serviço** , que você também pode acessar clicando com o botão direito do mouse no projeto em **Gerenciador de soluções** e selecionando **Adicionar referência de serviço**.

 Quando você cria uma fonte de dados de um serviço, o Visual Studio adiciona uma referência de serviço ao seu projeto. O Visual Studio também cria objetos proxy que correspondem aos objetos que o serviço retorna. Por exemplo, um serviço que retorna um conjunto de um DataSet é representado em seu projeto como um conjunto de um. um serviço que retorna um tipo específico é representado em seu projeto como o tipo retornado.

 Você pode criar uma fonte de dados dos seguintes tipos de serviços:

- WCF Data Services. Para obter mais informações, consulte [visão geral](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).

- WCF Data Services. Para obter mais informações, consulte [Windows Communication Foundation Services e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).

- Serviços Web.

    > [!NOTE]
    > Os itens que aparecem na janela **Data Sources** são dependentes dos dados que o serviço retorna. Alguns serviços podem não fornecer informações suficientes para o **Assistente de Configuração de Fonte de Dados** criar objetos associáveis. Por exemplo, se o serviço retornar um conjunto de dados não tipado, nenhum item será exibido na janela **fontes de dados** quando você concluir o assistente. Isso ocorre porque os conjuntos de dados não tipados não fornecem um esquema e, portanto, o assistente não tem informações suficientes para criar a fonte de dados.

## <a name="data-source-for-an-object"></a>Fonte de dados para um objeto
 Você pode criar uma fonte de dados de qualquer objeto que expõe uma ou mais propriedades públicas executando o **Assistente de configuração da fonte de dados** e selecionando o tipo de fonte de dados do **objeto** . Todas as propriedades públicas de um objeto são exibidas na janela **fontes de dados** .   Se você estiver usando Entity Framework e tiver gerado um modelo, é aqui que você encontrará as classes de entidade que serão as fontes de dados para seu aplicativo.

 Na página **selecionar os objetos de dados** , expanda os nós na exibição de árvore para localizar os objetos que você deseja associar. O modo de exibição de árvore contém nós para seu projeto e para assemblies e outros projetos que são referenciados por seu projeto.

 Se você quiser associar a um objeto em um assembly ou projeto que não é exibido no modo de exibição de árvore, clique em **Adicionar referência** e use a **caixa de diálogo Adicionar referência** para adicionar uma referência ao assembly ou ao projeto. Depois de adicionar a referência, o assembly ou projeto é adicionado ao modo de exibição de árvore.

> [!NOTE]
> Talvez seja necessário compilar o projeto que contém os objetos antes que os objetos apareçam no modo de exibição de árvore.

> [!NOTE]
> Para dar suporte à vinculação de dados do tipo "arrastar e soltar", os objetos que implementam a <xref:System.ComponentModel.ITypedList> <xref:System.ComponentModel.IListSource> interface ou devem ter um construtor padrão. Caso contrário, o Visual Studio não poderá instanciar o objeto de fonte de dados e exibirá um erro quando você arrastar o item para a superfície de design.

## <a name="data-source-for-a-sharepoint-list"></a>Fonte de dados para uma lista do SharePoint
 Você pode criar uma fonte de dados de uma lista do SharePoint executando o **Assistente de configuração da fonte de dados** e selecionando o tipo de fonte de dados do **SharePoint** . O SharePoint expõe dados por meio [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] do, portanto, criar uma fonte de dados do SharePoint é o mesmo que criar uma fonte de dados de um serviço. A seleção do item do **SharePoint** no **Assistente de configuração da fonte de dados** abre a caixa de diálogo **Adicionar referência de serviço** , em que você se conecta ao serviço de dados do SharePoint apontando para o servidor do SharePoint.  Isso requer o SDK do SharePoint.

## <a name="see-also"></a>Consulte Também
 [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
