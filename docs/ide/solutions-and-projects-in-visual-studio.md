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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42a8dbc2fd9a6fc89b0be62271b048f8275a82b2
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432205"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluções e projetos no Visual Studio

Este artigo descreve o conceito de um *projeto* e de uma *solução* no Visual Studio. Ele também aborda rapidamente a janela de ferramentas **Gerenciador de Soluções** e como criar um projeto.

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Projetos e soluções no Visual Studio para Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projetos

Ao criar um aplicativo, um site, um plug-in, etc. no Visual Studio, você inicia um *projeto*. Logicamente, um projeto contém todos os arquivos de código-fonte, ícones, imagens, arquivos de dados, etc. que são compilados em um executável, biblioteca ou site. Um projeto também contém as configurações de compilador e outros arquivos de configuração que podem ser necessários para diversos serviços ou componentes com os quais seu programa se comunica.

> [!NOTE]
> Você não precisa usar soluções ou projetos no Visual Studio para editar, compilar e depurar o código. Você pode simplesmente abrir a pasta que contém os arquivos de origem no Visual Studio e começar a editá-los. Para obter mais informações, consulte [Desenvolver código no Visual Studio sem projetos nem soluções](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

Um projeto é definido em um arquivo XML com uma extensão, como *.vbproj*, *.csproj* ou *.vcxproj*. Este arquivo contém uma hierarquia de pasta virtual e os caminhos para todos os itens no projeto. Ele também contém as configurações de build.

> [!TIP]
> Para examinar o conteúdo de um arquivo de projeto no Visual Studio, primeiro descarregue o projeto selecionando o nome do projeto no **Gerenciador de Soluções** e escolhendo **Descarregar Projeto** no menu de contexto ou de clique com o botão direito do mouse. Em seguida, abra o menu de contexto novamente e escolha **Editar \<projectname\>** .

No Visual Studio, o arquivo de projeto é usado pelo **Gerenciador de Soluções** para exibir as configurações e o conteúdo do projeto. Quando você compila seu projeto, o mecanismo do MSBuild consome o arquivo de projeto para criar o executável. Você também pode personalizar os projetos para produzir outros tipos de saída.

## <a name="solutions"></a>Soluções

Um projeto está contido dentro de uma *solução*. Apesar do nome, uma solução não é uma "resposta". Ela é apenas um contêiner de um ou mais projetos relacionados, juntamente com informações de build, configurações de janela do Visual Studio e arquivos diversos que não estão associados a nenhum projeto específico. Uma solução é descrita por um arquivo de texto (extensão *.sln*) com seu próprio formato exclusivo; não se destina à edição manual.

O Visual Studio usa dois tipos de arquivos ( *.sln* e *.suo*) para armazenar configurações de soluções:

|Extensão|Nome|Descrição|
|---------------|----------|-----------------|
|.sln|Solução do Visual Studio|Organiza projetos, itens de projeto e itens de solução na solução.|
|.suo|Opções do usuário da solução|Armazena configurações e personalizações no nível do usuário, como pontos de interrupção.|

## <a name="create-new-projects"></a>Criar novos projetos

A maneira mais fácil de criar um novo projeto é começar de um modelo de projeto para um tipo específico de aplicativo ou site. Um modelo de projeto consiste em um conjunto básico de arquivos de código, arquivos de configuração, ativos e configurações gerados previamente. Esses modelos estão disponíveis na caixa de diálogo em que você cria um projeto (**Arquivo** > **Novo** > **Projeto**). Para saber mais, confira [Criar um novo projeto no Visual Studio](create-new-project.md) e [Criar soluções e projetos](../ide/creating-solutions-and-projects.md).

Se você costuma personalizar seus projetos de uma determinada maneira, é possível criar um modelo de projeto personalizado que possa ser usado para criar novos projetos. Para obter mais informações, confira [Criar modelos de projeto e de item](../ide/creating-project-and-item-templates.md).

Quando você cria um novo projeto, ele é salvo por padrão em *%USERPROFILE%\source\repos*. Você pode alterar esse local na configuração **Locais do projeto** em **Ferramentas** > **Opções** > **Projetos e Soluções** > **Locais**. Para obter mais informações, consulte a [página Projetos e Soluções, caixa de diálogo Opções](../ide/reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Gerenciador de Soluções

Depois de criar um novo projeto, você pode usar o **Gerenciador de Soluções** para exibir e gerenciar o projeto, a solução e seus itens associados. A ilustração a seguir mostra o **Gerenciador de Soluções** com uma solução C# que contém dois projetos:

![Gerenciador de Soluções](../ide/media/vs2015_solution_explorer.png)

Muitos comandos de menu estão disponíveis no menu do botão direito em vários itens no **Gerenciador de Soluções**. Esses comandos incluem criar um projeto, gerenciar pacotes do NuGet, adicionar uma referência, renomear um arquivo e executar testes, apenas para citar alguns. A barra de ferramentas na parte superior do **Gerenciador de Soluções** possui botões para alternar de uma exibição de solução para uma exibição de pasta, mostrar arquivos ocultos, recolher todos os nós e muito mais.

Para projetos ASP.NET Core, você pode personalizar como os arquivos são aninhados no **Gerenciador de Soluções**. Para saber mais, confira [Personalizar o aninhamento de arquivos no Gerenciador de Soluções](file-nesting-solution-explorer.md).

## <a name="see-also"></a>Consulte também

- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Projetos e soluções (Visual Studio para Mac)](/visualstudio/mac/projects-and-solutions)
- [Adicionar e remover itens do projeto (Visual Studio para Mac)](/visualstudio/mac/add-and-remove-project-items)
