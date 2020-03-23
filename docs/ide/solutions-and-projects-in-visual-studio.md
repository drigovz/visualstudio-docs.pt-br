---
title: Soluções e projetos
ms.date: 10/05/2017
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
- vs.addnewsolutionitem
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffa561667ea31f215306c7cac4b9820d7b386b5c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303067"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluções e projetos no Visual Studio

Esta página descreve o conceito de um *projeto* e uma *solução* no Visual Studio. Ele também cobre brevemente a janela da ferramenta Solution Explorer e como criar um novo projeto.

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Projetos e soluções no Visual Studio para Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projetos

Quando você cria um aplicativo ou site no Visual Studio, você começa com um *projeto*. Em um sentido lógico, um projeto contém todos os arquivos que são compilados em um executável, biblioteca ou site. Esses arquivos podem incluir código-fonte, ícones, imagens, arquivos de dados e assim por diante. Um projeto também contém as configurações de compilador e outros arquivos de configuração que podem ser necessários para diversos serviços ou componentes com os quais seu programa se comunica.

### <a name="project-file"></a>Arquivo de projeto

O Visual Studio usa [o MSBuild](../msbuild/msbuild.md) para construir cada projeto em uma solução, e cada projeto contém um arquivo de projeto MSBuild. A extensão do arquivo reflete o tipo de projeto, por exemplo, um projeto C# (.csproj), um projeto Visual Basic (.vbproj) ou um projeto de banco de dados (.dbproj). O arquivo do projeto é um documento XML que contém todas as informações e instruções que o MSBuild precisa para construir seu projeto, incluindo o conteúdo, os requisitos da plataforma, as informações de versão, as configurações do servidor web ou do servidor de banco de dados e as tarefas para Executar.

Os arquivos do projeto são baseados no [esquema MSBuild XML](../msbuild/msbuild-project-file-schema-reference.md). Para ver o conteúdo dos arquivos de projeto mais novos e [estilo SDK](../msbuild/how-to-use-project-sdk.md) no Visual Studio, clique com o botão direito do mouse no nó do projeto no **Solution Explorer** e selecione ** \<Editar nome de projeto\>**. Para olhar o conteúdo do .NET Framework e outros projetos desse estilo, primeiro descarregue o projeto (clique com o botão direito do mouse no nó do projeto no **Solution Explorer** e selecione **Unload Project**). Em seguida, clique com o botão direito do mouse no projeto e escolha **Editar \<nome de\>projeto**.

> [!NOTE]
> Você não precisa usar soluções ou projetos no Visual Studio para editar, construir e depurar código. Você pode simplesmente abrir a pasta que contém os arquivos de origem no Visual Studio e começar a editá-los. Para obter mais informações, consulte [Desenvolver código no Visual Studio sem projetos nem soluções](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Soluções

Um projeto está contido dentro de uma *solução*. Apesar do nome, uma solução não é uma "resposta". Ela é apenas um contêiner de um ou mais projetos relacionados, juntamente com informações de build, configurações de janela do Visual Studio e arquivos diversos que não estão associados a nenhum projeto específico. Uma solução é descrita por um arquivo de texto (extensão *.sln*) com seu próprio formato exclusivo; não se destina à edição manual.

O Visual Studio usa dois tipos de arquivos (*.sln* e *.suo*) para armazenar configurações de soluções:

|Extensão|Nome|Descrição|
|---------------|----------|-----------------|
|.sln|Solução do Visual Studio|Organiza projetos, itens de projeto e itens de solução na solução.|
|.suo|Opções do usuário da solução|Armazena configurações e personalizações no nível do usuário, como pontos de interrupção.|

## <a name="create-new-projects"></a>Criar novos projetos

A maneira mais fácil de criar um novo projeto é começar de um modelo de projeto para um tipo específico de aplicativo ou site. Um modelo de projeto consiste em um conjunto básico de arquivos de código, arquivos de configuração, ativos e configurações gerados previamente. Esses modelos estão disponíveis na caixa de diálogo onde você cria um novo projeto **(File** > **New** > **Project).** Para saber mais, confira [Criar um novo projeto no Visual Studio](create-new-project.md) e [Criar soluções e projetos](../ide/creating-solutions-and-projects.md).

Se você geralmente personalizar seus projetos de uma certa maneira, você pode criar um modelo de projeto personalizado que você pode usar para criar novos projetos a partir. Para obter mais informações, confira [Criar modelos de projeto e de item](../ide/creating-project-and-item-templates.md).

Quando você cria um novo projeto, ele é salvo por padrão em *%USERPROFILE%\source\repos*. Você pode alterar esse local na configuração **Locais do projeto** em **Ferramentas** > **Opções** > **Projetos e Soluções** > **Locais**. Para obter mais informações, consulte a [página Projetos e Soluções, caixa de diálogo Opções](../ide/reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Gerenciador de Soluções

Depois de criar um novo projeto, você pode usar o **Gerenciador de Soluções** para exibir e gerenciar o projeto, a solução e seus itens associados. A ilustração a seguir mostra o **Gerenciador de Soluções** com uma solução C# que contém dois projetos:

![Gerenciador de Soluções](../ide/media/vs2015_solution_explorer.png)

Muitos comandos de menu estão disponíveis no menu do botão direito em vários itens no **Gerenciador de Soluções**. Esses comandos incluem criar um projeto, gerenciar pacotes do NuGet, adicionar uma referência, renomear um arquivo e executar testes, apenas para citar alguns. A barra de ferramentas na parte superior do **Gerenciador de Soluções** possui botões para alternar de uma exibição de solução para uma exibição de pasta, mostrar arquivos ocultos, recolher todos os nós e muito mais.

Para projetos ASP.NET Core, você pode personalizar como os arquivos são aninhados no **Gerenciador de Soluções**. Para saber mais, confira [Personalizar o aninhamento de arquivos no Gerenciador de Soluções](file-nesting-solution-explorer.md).

## <a name="see-also"></a>Confira também

- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Projetos e soluções (Visual Studio para Mac)](/visualstudio/mac/projects-and-solutions)
- [Adicionar e remover itens do projeto (Visual Studio para Mac)](/visualstudio/mac/add-and-remove-project-items)
