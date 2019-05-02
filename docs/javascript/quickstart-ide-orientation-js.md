---
title: Tour do IDE do Visual Studio
titleSuffix: ''
ms.date: 02/05/2019
ms.topic: quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d2c20f25b005e738769d1c8663387f0a427e5dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840880"
---
# <a name="first-look-at-the-visual-studio-ide"></a>Introdução ao IDE do Visual Studio

Nesta introdução de 5 a 10 minutos ao IDE (Ambiente de Desenvolvimento Integrado) do Visual Studio, faremos um tour em algumas janelas, menus e em outros recursos de interface do usuário.

::: moniker range="vs-2017"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalá-lo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) para instalá-lo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Janela de início

A primeira coisa que você verá depois de iniciar o Visual Studio é a janela de início. A janela de início foi projetada para ajudar você a "acessar o código" mais rapidamente. Ela tem opções para fechar o código ou fazer check-out dele, abrir um projeto ou uma solução existente, criar um projeto ou simplesmente abrir uma pasta que contenha alguns arquivos de código.

[![](media/vs-2019/start-window.png "A janela de início no Visual Studio 2019")](media/vs-2019/start-window.png)

Se essa for a primeira vez que você estiver usando o Visual Studio, sua lista de projetos recentes estará vazia.

Se você trabalhar com bases de código não baseadas no MSBuild, você usará a opção **Abrir uma pasta local** para abrir o código no Visual Studio. Para obter mais informações, consulte [Desenvolver código no Visual Studio sem projetos nem soluções](develop-javascript-code-without-solutions-projects.md). Caso contrário, você poderá criar um projeto ou clonar um projeto de um provedor de origem como o GitHub ou o Azure DevOps.

A opção **Continuar sem código** apenas abre o ambiente de desenvolvimento do Visual Studio sem nenhum projeto ou código específico carregado. Escolha essa opção para ingressar em uma sessão do [Live Share](/visualstudio/liveshare/) ou anexar a um processo para depuração. Pressione também **Esc** para fechar a janela de início e abrir o IDE.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Start Page

A primeira coisa que você verá depois de iniciar o Visual Studio provavelmente será a **Página Inicial**. A **Página Inicial** foi projetada como um "hub" para ajudá-lo a localizar os comandos e os arquivos de projeto necessários com mais rapidez. A seção **Recentes** exibe projetos e pastas em que você trabalhou recentemente. Em **Novo projeto**, clique em um link para abrir a caixa de diálogo **Novo Projeto** ou, em **Abrir**, abra uma pasta ou um projeto de código existente. À direita está um feed das notícias mais recentes do desenvolvedor.

![Página Inicial no Visual Studio](media/start-page.png)

Se você fechar a **Página Inicial** e desejar vê-la novamente, será possível reabri-la no menu **Arquivo**.

![Menu Arquivo no Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

## <a name="create-a-project"></a>Criar um projeto

Para continuar explorando os recursos do Visual Studio, vamos criar um projeto.

::: moniker range=">=vs-2019"

1. Na janela de início, selecione **Criar um projeto** e, em seguida, na caixa de pesquisa, digite **javascript** para filtrar da lista de tipos de projeto para aqueles que contenham "javascript" no nome ou no tipo de linguagem.

   O Visual Studio fornece vários tipos de modelos de projeto que ajudam você a começar a codificar rapidamente. (Como alternativa, se você for um desenvolvedor do TypeScript, fique à vontade criar um projeto nessa linguagem. A interface do usuário que veremos é semelhante em todas as linguagens de programação.)

   ![Pesquisar modelos de projeto na janela de início do Visual Studio](media/vs-2019/create-new-project.png)

1. Escolha um modelo de projeto **Aplicativo Web do Node.js em Branco** e clique em **Avançar**.

1. Na caixa de diálogo **Configurar o novo projeto** exibida, aceite o nome de projeto padrão e escolha **Criar**.

::: moniker-end

::: moniker range="vs-2017"

1. Na **Página Inicial**, na caixa de pesquisa de **Novo projeto**, digite **javascript** para filtrar da lista de tipos de projeto aqueles que contêm "javascript" no nome ou tipo de linguagem.

   ![Pesquisar modelos de projeto na Página Inicial do Visual Studio](media/start-page-search-templates.png)

   O Visual Studio fornece vários tipos de modelos de projeto que ajudam você a começar a codificar rapidamente. Escolha um modelo de projeto de **Aplicativo Web do Node.js em branco**. (Como alternativa, se você for um desenvolvedor do TypeScript, fique à vontade criar um projeto nessa linguagem. A interface do usuário que veremos é semelhante em todas as linguagens de programação.)

1. Na caixa de diálogo **Novo Projeto** exibida, aceite o nome de projeto padrão e escolha **OK**.
::: moniker-end

   O projeto é criado e um arquivo chamado *server.cs* é aberto na janela **Editor**. O **Editor** mostra o conteúdo dos arquivos e é onde você fará a maior parte do trabalho de codificação no Visual Studio.

   ![Editor no Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Gerenciador de Soluções

O **Gerenciador de Soluções**, que, normalmente, está do lado direito do Visual Studio, mostra uma representação gráfica da hierarquia de arquivos e pastas no projeto, na solução ou na pasta de código. Você pode procurar na hierarquia e navegar até algum arquivo no **Gerenciador de Soluções**.

![Gerenciador de Soluções no Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menus

A barra de menus na parte superior do Visual Studio agrupa os comandos em categorias. Por exemplo, o menu **Projeto** contém comandos relacionados ao projeto em que você está trabalhando. No menu **Ferramentas**, personalize o comportamento do Visual Studio selecionando **Opções** ou adicione recursos à instalação selecionando **Obter Ferramentas e Recursos**.

![Barra de menus no Visual Studio](media/quickstart-IDE-menu-bar.png)

Vamos abrir a janela **Lista de Erros** escolhendo o menu **Exibir** e, em seguida, **Lista de Erros**.

## <a name="error-list"></a>Lista de Erros

A **Lista de Erros** mostra erros, avisos e mensagens sobre o estado atual do código. Se houver erros (como uma chave ou um ponto e vírgula ausente) no arquivo ou em qualquer lugar do projeto, eles serão listados aqui.

![Lista de Erros no Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>janela Saída

A janela de **Saída** mostra as mensagens de saída do build do projeto e do provedor de controle do código-fonte.

Vamos criar o projeto para ver uma saída de build. No menu **Compilação**, escolha **Compilar Solução**. A janela **Saída** obtém o foco automaticamente e exibe uma mensagem de build bem-sucedido.

![Janela de Saída no Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Caixa de pesquisa

A caixa pesquisa é uma maneira rápida e fácil de fazer praticamente tudo no Visual Studio. Você pode inserir um texto relacionado ao que você deseja fazer e ele mostrará uma lista de opções que pertencem ao texto. Por exemplo, imagine que você deseje aumentar o detalhamento da saída de build para que ela exiba mais detalhes sobre o que o build está fazendo exatamente. Veja como você pode fazer isso:

1. Digite **detalhamento** na caixa de pesquisa. Nos resultados exibidos, escolha **Projetos e Soluções -> Compilar e Executar** na categoria **Opções**.

   ![Caixa de pesquisa no Visual Studio](media/quickstart-IDE-quick-launch.png)

   A caixa de diálogo **Opções**é aberta na página de opções **Compilar e Executar**.

1. Em **Detalhes da saída de build do projeto do MSBuild**, escolha **Normal** e clique em **OK**.

1. Compile o projeto novamente clicando com o botão direito do mouse no projeto **NodejsWebApp1** no **Gerenciador de Soluções** e escolhendo **Recompilar** no menu de contexto.

   Desta vez, a janela **Saída** mostra o log detalhado do processo de build, incluindo quais arquivos foram copiados e onde.

   ![Saída de build detalhada no Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menu Enviar Comentários

Caso encontre problemas enquanto estiver usando o Visual Studio ou se tiver sugestões de como melhorar o produto, use o menu **Enviar Comentários** na parte superior da janela do Visual Studio.

![Menu Enviar Comentários no Visual Studio](../ide/media/quickstart-ide-send-feedback.png)

## <a name="next-steps"></a>Próximas etapas

Examinamos apenas alguns dos recursos do Visual Studio para nos familiarizarmos com a interface do usuário. Para explorar mais:

> [!div class="nextstepaction"]
> [Saiba mais sobre o editor de códigos](write-and-edit-code.md)

> [!div class="nextstepaction"]
> [Saiba mais sobre projetos e soluções](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Consulte também

- [Visão geral do IDE do Visual Studio](../get-started/visual-studio-ide.md)
- [Mais recursos do Visual Studio 2017](../ide/advanced-feature-overview.md)
- [Alterar as cores do tema e da fonte](../ide/quickstart-personalize-the-ide.md)
