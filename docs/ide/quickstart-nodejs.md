---
title: 'Início rápido: usar o Visual Studio para criar seu primeiro aplicativo Node.js'
description: Neste guia de início rápido, você cria um aplicativo Node.js no Visual Studio
ms.date: 06/27/2018
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f716421da3b9f888dbb7656c55db6814de88332b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "78235048"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Início rápido: usar o Visual Studio para criar seu primeiro aplicativo Node.js

Nesta introdução de 5 a 10 minutos do IDE (ambiente de desenvolvimento integrado) do Visual Studio, você criará um aplicativo Web Node.js simples.

## <a name="prerequisites"></a>Pré-requisitos

* Você precisa ter o Visual Studio instalado e a carga de trabalho de desenvolvimento de Node.js.

    ::: moniker range=">=vs-2019"
    Se você ainda não instalou o Visual Studio 2019, acesse a página [de downloads](https://visualstudio.microsoft.com/downloads) do Visual Studio para instalá-lo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se você ainda não instalou o Visual Studio 2017, acesse a página [de downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do Visual Studio para instalá-lo gratuitamente.
    ::: moniker-end

    Se você precisa instalar a carga de trabalho, mas já tem o Visual Studio, vá para **Ferramentas** > **Obter Ferramentas e Recursos...**, que abre o Visual Studio Installer. Escolha a carga de trabalho **Desenvolvimento de Node.js** e, em seguida, selecione **Modificar**.

    ![Carga de trabalho Node.js no instalador do VS](../ide/media/quickstart-nodejs-workload.png)

* Você precisa ter o runtime do Node.js instalado.

    Se você não o tiver instalado, recomendamos que você instale a versão LTS do site [node.js](https://nodejs.org/en/download/) para melhor compatibilidade com frameworks e bibliotecas externas. O Node.js é construído para arquiteturas de 32 bits e 64 bits. As ferramentas Node.js no Visual Studio, incluídas na carga de trabalho do Node.js, suportam ambas as versões. Apenas um é necessário e o instalador Node.js suporta apenas um sendo instalado por vez.
    
    Em geral, o Visual Studio detecta automaticamente o runtime do Node.js instalado. Se ele não detectar um tempo de execução instalado, você poderá configurar seu projeto para referenciar o tempo de execução instalado na página de propriedades (depois de criar um projeto, clique com o botão direito do mouse no nó do projeto, escolha **Propriedades**e defina o **caminho Node.exe**). Você pode usar uma instalação global do Node.js ou pode especificar o caminho para um intérprete local em cada um de seus projetos Node.js. 

## <a name="create-a-project"></a>Criar um projeto

Primeiro, você criará um projeto de aplicativo Web Node.js.

1. Se não tiver o runtime do Node.js instalado, instale a versão LTS do site do [Node.js](https://nodejs.org/en/download/).

    Para obter mais informações, consulte os pré-requisitos.

1. Abra o Visual Studio.

1. Criar um novo projeto.

    ::: moniker range=">=vs-2019"
    Pressione **Esc** para fechar a janela de início. Digite **Ctrl + Q** para abrir a caixa de pesquisa, digite **Node.js** e, em seguida, escolha **Criar novo projeto de Aplicativo Web Node.js em Branco** (JavaScript). Na caixa de diálogo que aparece, escolha **Criar**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na barra de menu superior, escolha **Arquivo** > **Novo** > **Projeto**. No painel esquerdo da caixa de diálogo **Novo Projeto**, expanda **JavaScript** e escolha **Node.js**. No painel central, escolha **Aplicativo Web Node.js em branco** e, em seguida, escolha **OK**.
    ::: moniker-end
    Se não vir o modelo de projeto **Aplicativo Web Node.js em Branco**, instale a carga de trabalho de **desenvolvimento de Node.js**. Confira instruções detalhadas nos [Pré-requisitos](#prerequisites).

    O Visual Studio cria a nova solução e abre o projeto. *server.js* é aberto no editor no painel esquerdo.

## <a name="explore-the-ide"></a>Explorar o IDE

1. Observe o **Gerenciador de Soluções** no painel direito.

   ![Gerenciador de Soluções](../ide/media/quickstart-nodejs-solution-explorer.png)

   - O seu projeto está realçado em negrito, usando o nome que você forneceu na caixa de diálogo **Novo Projeto**. No disco, este projeto é representado por um arquivo *.njsproj* na pasta do projeto.

   - No nível superior está uma solução que, por padrão, tem o mesmo nome que o projeto. Uma solução, representada por um arquivo *.sln* no disco, é um contêiner para um ou mais projetos relacionados.

   - O nó de npm mostra os pacotes npm instalados. Você pode clicar com o botão direito do mouse no nó de npm para pesquisar e instalar pacotes de npm usando uma caixa de diálogo.

1. Se você quiser instalar pacotes npm ou comandos Node.js a partir de um prompt de comando, clique com o botão direito do mouse no nó do projeto e escolha **Abrir comando Prompt aqui**.

   ![Prompt de comando do Node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. No arquivo *server.js* no editor (painel esquerdo), escolha `http.createServer` e pressione **F12** ou escolha **Ir para Definição** no menu de contexto (acessado com o clique do botão direito do mouse). Este comando leva você à `createServer` definição da função em *index.d.ts*.

   ![Menu de contexto de Ir para Definição](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Volte para *server.js*, coloque o cursor no final da cadeia de caracteres nesta linha de código, `res.end('Hello World\n');` e modifique-a para que fique assim:

    `res.end('Hello World\n' + res.connection.`

    Quando você digita `connection.`, o IntelliSense fornece opções para completar automaticamente a entrada de código.

   ![Preenchimento automático do IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Escolha **localPort**e, em seguida, digite `);` para completar a instrução para que ela fique assim:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Executar o aplicativo

1. Pressione **Ctrl**+**F5** (ou **Debug > Start Without Debugging**) para executar o aplicativo. O aplicativo é aberto em um navegador.

1. Na janela do navegador, você verá “Olá, Mundo”, além do número da porta local.

1. Feche o navegador da web.

Parabéns por concluir este Início Rápido! Nele, você se familiarizou com o IDE do Visual Studio e o Node.js. Caso deseje se aprofundar mais nas funcionalidades, continue com um tutorial na seção **Tutoriais** do sumário.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Implantar o aplicativo no Serviço de Aplicativo do Linux](../javascript/publish-nodejs-app-azure.md)

- [Tutorial para o Node.js e o Express](../javascript/tutorial-nodejs.md)
- [Tutorial para o Node.js e o React](../javascript/tutorial-nodejs-with-react-and-jsx.md)