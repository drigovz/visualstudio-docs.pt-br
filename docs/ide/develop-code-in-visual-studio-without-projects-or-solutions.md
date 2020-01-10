---
title: Desenvolver o código sem projetos nem soluções
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a9459868d569a7466dccf92e4b548c0500bf80
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596288"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Desenvolver código no Visual Studio sem projetos nem soluções

Abra o código em praticamente todos os tipos de projeto baseado em diretório no Visual Studio sem a necessidade de um arquivo de projeto ou de solução. Isso significa que você pode, por exemplo, clonar um repositório no GitHub, abri-lo diretamente no Visual Studio e começar o desenvolvimento sem precisar criar uma solução ou um projeto. Se for necessário, você pode especificar as tarefas de compilação personalizadas e iniciar os parâmetros por meio de arquivos JSON simples.

Após você abrir os arquivos do código no Visual Studio, o **Gerenciador de Soluções** exibirá todos os arquivos na pasta. Você pode clicar em qualquer arquivo para começar a editá-lo. Em segundo plano, o Visual Studio inicia a indexação dos arquivos para habilitar os recursos de IntelliSense, navegação e refatoração. À medida que você edita, cria, move ou exclui arquivos, o Visual Studio rastreia as alterações automaticamente e atualiza continuamente seu índice do IntelliSense. O código será exibido com a colorização de sintaxe e, em muitos casos, incluirá o preenchimento instrução básico do IntelliSense.

## <a name="open-any-code"></a>Abra qualquer código

Você pode abrir o código no Visual Studio usando uma destas maneiras:

- Na barra de menus do Visual Studio, escolha **Arquivo** > **Abrir** > **Pasta** e, em seguida, navegue até o local do código.

- No menu de contexto (acesso por clique com o botão direito do mouse) de uma pasta que contém o código, escolha o comando **Abrir no Visual Studio**.

::: moniker range="vs-2017"
- Escolha o link **Abrir Pasta** na **Página Inicial** do Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
- Escolha o link **Abrir Pasta** na janela de início.
::: moniker-end

- Se você for usuário de teclado, pressione **Ctrl**+**Shift**+**Alt**+**O** no Visual Studio.

- Abra o código de um repositório GitHub clonado.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Para abrir o código de um repositório GitHub clonado

O exemplo a seguir mostra como clonar um repositório GitHub e, em seguida, abrir seu código no Visual Studio. Para seguir este procedimento, você deve ter uma conta do GitHub e o Git para Windows instalado no sistema. Consulte [Inscrevendo em uma nova conta do GitHub](https://help.github.com/articles/signing-up-for-a-new-github-account/) e o [Git para Windows](https://git-for-windows.github.io/) para obter mais informações.

1. Acesse o repositório que deseja clonar no GitHub.

1. Escolha o botão **Clonar ou Baixar** e, em seguida, selecione o botão **Copiar para Área de Transferência** no menu suspenso para copiar a URL segura do repositório do GitHub.

   ![Botão de clone do GitHub](./media/VSIDE_Code_Clone.png)

1. No Visual Studio, escolha a guia **Team Explorer** para abrir o **Team Explorer**. Se você não vir a guia, abra-a em **Exibir** > **Team Explorer**.

1. No Team Explorer, na seção **Repositórios Git Locais**, escolha o comando **Clonar** e, em seguida, cole a URL da página do GitHub na caixa de texto.

   ![Clonar o projeto](./media/VSIDE_Code_Clone2.png)

1. Escolha o botão **Clonar** para clonar os arquivos do projeto para um repositório Git local. Dependendo do tamanho do repositório, esse processo poderá levar vários minutos.

1. Depois que o repositório for clonado para o sistema, no **Team Explorer**, escolha o comando **Abrir** no menu de contexto (acesso com clique com o botão direito do mouse) do repositório recém-clonado.

   ![Repositório clonado](./media/VSIDE_Code_Clone3.png)

1. Escolha o comando **Mostrar Modo de Exibição da Pasta** para exibir os arquivos no **Gerenciador de Soluções**.

   ![Mostrar exibição de pasta](./media/VSIDE_Code_Clone3_show.png)

   Agora é possível procurar pastas e arquivos no repositório clonado, além de exibir e pesquisar o código no editor de códigos do Visual Studio, completo com colorização de sintaxe e outros recursos.

## <a name="run-and-debug-your-code"></a>Executar e depurar seu código

É possível depurar o código no Visual Studio sem um projeto ou uma solução! Para depurar algumas linguagens, talvez seja necessário especificar um *arquivo de inicialização* válido na base de código, como um script, executável ou projeto. A caixa de listagem suspensa ao lado do botão **Iniciar** na barra de ferramentas lista todos os itens de inicialização detectados pelo Visual Studio, bem como os itens indicados especificamente por você. O Visual Studio executa esse código primeiro ao depurar o código.

A configuração de seu código para execução no Visual Studio difere dependendo do tipo de código e das ferramentas de compilação.

### <a name="codebases-that-use-msbuild"></a>Bases de código que usam MSBuild

Bases de código com base em MSBuild podem ter várias configurações de build que aparecem na lista suspensa do botão **Iniciar**. Selecione o arquivo que você quer usar como o item de inicialização e, depois, escolha o botão **Iniciar** para começar a depuração.

> [!NOTE]
> Para as bases de código de C# e Visual Basic, você deve ter a carga de trabalho **Desenvolvimento para desktop com o .NET**. Para as bases de código de C++, você deve ter a carga de trabalho **Desenvolvimento para desktop com o C++** instalada.

### <a name="codebases-that-use-custom-build-tools"></a>As bases de código que usam ferramentas de compilação personalizadas

Se a base de código usar ferramentas de compilação personalizadas, você deverá instruir o Visual Studio como compilar seu código usando *tarefas de build* definidas em um arquivo *.json*. Para saber mais, confira [Personalizar tarefas de compilação e depuração](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Bases de código que contém código Python ou JavaScript

Se a sua base de código contiver código Python ou JavaScript, não será necessário configurar arquivos *.json*, mas você precisa instalar a carga de trabalho correspondente. Você também precisa configurar o script de inicialização:

1. Instale a carga de trabalho [Desenvolvimento em Node.js](https://visualstudio.microsoft.com/vs/node-js/) ou [Desenvolvimento em Python](https://visualstudio.microsoft.com/vs/python/) escolhendo **Ferramentas** > **Obter Ferramentas e Recursos** ou fechando o Visual Studio e executando o Instalador do Visual Studio.

   ![Cargas de trabalho de desenvolvimento do Node.js e Python](media/python_nodejs_workloads.png)

1. No **Gerenciador de Soluções**, no menu de contexto ou de atalho de um arquivo JavaScript, escolha o comando **Definir como Item de Inicialização**.

1. Escolha o botão **Iniciar** para começar a depuração.

### <a name="codebases-that-contain-c-code"></a>As bases de código que contêm o código C++

Para saber mais sobre como abrir o código C++ sem soluções ou projetos no Visual Studio, confira [Projetos de pasta aberta para C++](/cpp/build/open-folder-projects-cpp).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Bases de código que contém um projeto do Visual Studio

Se sua pasta de códigos contiver um projeto do Visual Studio, você poderá designar o projeto como o item de inicialização.

![Definir projeto como item de inicialização](media/customize-set-project-as-startup-item.png)

O texto do botão **Iniciar** muda para refletir que o projeto é o item de inicialização.

![Botão Projeto na Inicialização](media/customize-start-button-project.png)

## <a name="see-also"></a>Veja também

- [Personalizar as tarefas de depuração e build](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [Projetos de pasta aberta para C++](/cpp/build/open-folder-projects-cpp)
- [Projetos CMake em C++](/cpp/build/cmake-projects-in-visual-studio)
- [Escrevendo código no editor de código e texto](../ide/writing-code-in-the-code-and-text-editor.md)
