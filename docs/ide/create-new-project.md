---
title: Criar um novo projeto
description: Saiba como criar um novo projeto no Visual Studio.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/17/2020
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd8b6cb4819ae13b526eb5106bc7de3919d1a74f
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97683975"
---
# <a name="create-a-new-project-in-visual-studio"></a>Criar um novo projeto no Visual Studio

Neste artigo, mostraremos como criar rapidamente um novo projeto no Visual Studio.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Abrir a caixa de diálogo Novo Projeto

Há várias maneiras de criar um projeto no Visual Studio 2017. Na página inicial, você pode digitar o nome de um modelo de projeto na caixa **Pesquisar modelos de projeto** ou selecionar o link **criar novo projeto** para abrir a caixa de diálogo **novo projeto** . Além da página inicial, você também pode selecionar **arquivo**  >  **novo**  >  **projeto** na barra de menus ou clicar no botão **novo projeto** na barra de ferramentas.

![Página inicial e Arquivo > Novo > Projeto](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Selecione um tipo de modelo

Na caixa de diálogo **Novo Projeto**, os modelos de projeto disponíveis aparecem em uma lista sob a categoria **Modelos**. Os modelos são organizados por linguagem de programação e tipo de projeto, como Visual C#, JavaScript e Azure Data Lake.

![Caixa de diálogo Novo projeto](./media/vside-newproject-templates-list.png)

> [!NOTE]
> A lista de linguagens e modelos de projeto disponíveis que é exibida depende da versão do Visual Studio que você está executando e das cargas de trabalho que estão instaladas. Para saber mais sobre como instalar cargas de trabalho adicionais, confira [Modificar o Visual Studio adicionando ou removendo cargas de trabalho e componentes](../install/modify-visual-studio.md).

Para mostrar a lista de modelos da linguagem de programação que você deseja usar, clique no triângulo próximo do nome da linguagem e, em seguida, escolha uma categoria de projeto (tal como Área de Trabalho do Windows).

A imagem a seguir mostra os modelos de projeto disponíveis para projetos .NET Core do Visual C#:

![Modelos de projeto](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Configurar seu projeto

Digite um nome para o novo projeto na caixa **Nome**. Você pode salvar o projeto no local padrão em seu computador ou escolher o botão **Procurar** para encontrar outro local. Você também pode selecionar um nome de solução ou adicionar o novo projeto a um repositório git (selecionando **Adicionar ao controle do código-fonte**).

Clique em **OK** para criar a solução e o projeto.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Abrir a página Criar um novo projeto

Há várias maneiras de criar um projeto no Visual Studio 2019. Quando você abre o Visual Studio pela primeira vez, a janela iniciar é exibida e, a partir daí, você pode selecionar **criar um novo projeto**.

![Criar um novo projeto a partir da janela inicial no Visual Studio 2019](media/vs-2019/start-window-create-new-project.png)

Se o ambiente de desenvolvimento do Visual Studio já estiver aberto, você poderá criar um projeto escolhendo **Arquivo** > **Novo** > **Projeto** na barra de menus ou clicando em **Novo Projeto** na barra de ferramentas.

![Botão Novo Projeto no Visual Studio 2019](media/vs-2019/new-project-button.png)

## <a name="select-a-template-type"></a>Selecione um tipo de modelo

Na página **Criar um novo projeto**, uma lista de seus modelos recentemente selecionados aparece à esquerda. Os modelos são classificados por *usados mais recentemente*.

Se não selecionar entre os modelos usados recentemente, você poderá filtrar todos os modelos de projeto disponíveis por **Linguagem de programação** (por exemplo, C# ou C++), **Plataforma** (por exemplo, Windows ou Azure) e **Tipo de projeto** (por exemplo, Desktop ou Web). Você também pode inserir texto de pesquisa na caixa de pesquisa para filtrar ainda mais os modelos, por exemplo, **asp.net**.

![Filtros de modelo de projeto no Visual Studio 2019](media/vs-2019/create-new-project-filters.png)

As marcas que aparecem em cada modelo correspondem aos três filtros de lista suspensa (Tipo de projeto, Plataforma e Linguagem de programação).

> [!TIP]
> Se você não vir o modelo que está procurando, talvez você não tenha uma carga de trabalho para o Visual Studio. Para instalar cargas de trabalho adicionais, por exemplo, **Desenvolvimento do Azure** ou **Desenvolvimento móvel com .NET**, clique no link **Instalar mais ferramentas e recursos** para abrir o Instalador do Visual Studio. A partir daí, selecione as cargas de trabalho que você deseja instalar e, em seguida, selecione **Modificar**. Depois disso, modelos de projeto adicionais serão disponibilizados para sua escolha.
>
> ![Link instalar mais ferramentas e recursos no Visual Studio 2019](media/vs-2019/install-more-tools-features.png)

Selecione um modelo e, em seguida, clique em **Avançar**.

## <a name="configure-your-project"></a>Configurar seu projeto

A página **configurar seu novo projeto** tem opções para nomear seu projeto (e solução), selecionar um local de disco e selecionar uma versão de estrutura (se aplicável ao modelo escolhido).

![Configurar sua nova página de projeto no Visual Studio 2019](media/vs-2019/configure-new-project.png)

> [!NOTE]
> Se você criar um projeto quando já tiver um projeto ou solução aberta no Visual Studio, uma opção de configuração adicional estará disponível. Você pode optar por criar uma solução ou adicionar o novo projeto à solução que já está aberta.
>
> ![Criar nova solução ou adicionar à solução existente no Visual Studio 2019](media/vs-2019/configure-new-project-solution.png)

Clique em **Criar** para criar o projeto.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Adicionar projetos adicionais a uma solução

Se você quiser adicionar um projeto adicional a uma solução, clique com o botão direito do mouse no nó da solução em **Gerenciador de soluções** e selecione **Adicionar**  >  **novo projeto**.

> [!TIP]
> Para obter um exemplo de um projeto e uma solução criados a partir do zero, conclua com instruções passo a passo e código de exemplo, consulte [introdução aos projetos e soluções](../get-started/tutorial-projects-solutions.md).

## <a name="see-also"></a>Confira também

- [Trabalhar com soluções e projetos](creating-solutions-and-projects.md)
