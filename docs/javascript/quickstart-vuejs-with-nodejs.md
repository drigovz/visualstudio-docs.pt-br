---
title: 'Início Rápido: Criar seu primeiro aplicativo Vue.js'
description: Neste início rápido, você criará um aplicativo Vue.js no Visual Studio usando as Ferramentas Node.js para Visual Studio
ms.custom: seodec18
ms.date: 09/24/2018
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
ms.openlocfilehash: 28e86068b2255d1796363405c0231c1fb6bdd480
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226507"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Início Rápido: Usar o Visual Studio para criar seu primeiro aplicativo Vue.js

Nesta introdução de 5 a 10 minutos do IDE (ambiente de desenvolvimento integrado) do Visual Studio, você criará e executará um aplicativo Web Vue.js simples.

> [!IMPORTANT]
> Este artigo requer o modelo Vue.js, disponível no Visual Studio 2017 versão 15.8 e posteriores.

## <a name="prerequisites"></a>Pré-requisitos

* Você precisa ter o Visual Studio instalado e a carga de trabalho de desenvolvimento de Node.js.

    ::: moniker range=">=vs-2019"
    Se você ainda não instalou o Visual Studio 2019, acesse a página  [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalá-lo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se você ainda não instalou o Visual Studio 2017, acesse a página  [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalá-lo gratuitamente.
    ::: moniker-end

    Caso precise instalar a carga de trabalho, mas já tiver o Visual Studio, acesse **Ferramentas** > **Obter Ferramentas e Funcionalidades...** , que abre o Instalador do Visual Studio. Escolha a carga de trabalho **Desenvolvimento de Node.js** e, em seguida, selecione **Modificar**.

    ![Carga de trabalho Node.js no instalador do VS](../ide/media/quickstart-nodejs-workload.png)

* Você precisa ter o tempo de execução do Node.js instalado.

    Se não o tiver instalado, instale a versão LTS do site do [Node.js](https://nodejs.org/en/download/). Em geral, o Visual Studio detecta automaticamente o tempo de execução do Node.js instalado. Se ele não detectar um tempo de execução instalado, você poderá configurar seu projeto para fazer referência ao tempo de execução instalado na página de propriedades (depois de criar um projeto, clique com botão direito do mouse no nó do projeto e escolha **Propriedades**).

## <a name="create-a-project"></a>Criar um projeto

Primeiro, você criará um projeto de aplicativo Web Vue.js.

1. Se não tiver o tempo de execução do Node.js instalado, instale a versão LTS do site do [Node.js](https://nodejs.org/en/download/).

    Em geral, o Visual Studio detecta automaticamente o tempo de execução do Node.js instalado. Se ele não detectar um tempo de execução instalado, você poderá configurar o projeto para referenciar o tempo de execução instalado na página de propriedades (depois de criar um projeto, clique com o botão direito do mouse no nó do projeto e escolha **Propriedades**).

1. Abra o Visual Studio.

1. Crie um novo projeto.

    ::: moniker range=">=vs-2019"
    Pressione **Esc** para fechar a janela de início. Digite **Ctrl + Q** para abrir a caixa de pesquisa, digite **Basic Vue.js** e, em seguida, escolha **Aplicativo Web básico do Vue.js** (JavaScript ou TypeScript). Na caixa de diálogo que aparece, digite o nome **basic-vuejs** e, em seguida, escolha **Criar**.

    ![Modelo do Vue.js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na barra de menus superior, escolha **Arquivo** > **Novo** > **Projeto**. No painel esquerdo da caixa de diálogo **Novo Projeto**, expanda **JavaScript** ou **TypeScript** e escolha **Node.js**. No painel central, escolha **aplicativo Web Basic Vue.js**, digite o nome **basic-vuejs** e, em seguida, escolha **OK**.

    ![Modelo do Vue.js](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Se não vir o modelo de projeto **Aplicativo Web Vue.js básico**, você deverá instalar a carga de trabalho de **desenvolvimento de Node.js**. Confira instruções detalhadas nos [Pré-requisitos](#prerequisites).

    O Visual Studio cria o projeto. O novo projeto é aberto no Gerenciador de Soluções (painel direito).

1. Verifique a janela de Saída (painel inferior) para ver o progresso da instalação dos pacotes npm necessários para o aplicativo.

1. No Gerenciador de Soluções, abra o nó **npm** e verifique se todos os pacotes npm listados estão instalados.

    Se um pacote estiver ausente (ícone de ponto de exclamação), clique com o botão direito do mouse no nó **npm** e escolha **Instalar Pacotes npm Ausentes**.

## <a name="explore-the-ide"></a>Explorar o IDE

1. Observe o **Gerenciador de Soluções** no painel direito.

     ![Solução do Vue.js](../javascript/media/vuejs-solution.png)

   - O seu projeto está realçado em negrito, usando o nome que você forneceu na caixa de diálogo **Novo Projeto**. No disco, esse projeto é representado por um arquivo *.njsproj* na pasta do projeto.

   - No nível superior está uma solução que, por padrão, tem o mesmo nome que o projeto. Uma solução, representada por um arquivo *.sln* no disco, é um contêiner para um ou mais projetos relacionados.

   - O nó **npm** mostra os pacotes npm instalados. Você pode clicar com o botão direito do mouse no nó de npm para pesquisar e instalar pacotes de npm usando uma caixa de diálogo.

2. Caso deseje instalar pacotes npm ou executar comandos do Node.js em um prompt de comando, clique com o botão direito do mouse no nó do projeto e escolha **Abrir Prompt de Comando Aqui**.

## <a name="add-a-vue-file-to-the-project"></a>Adicionar um arquivo .vue ao projeto

1. No Gerenciador de Soluções, clique com o botão direito do mouse em qualquer pasta, como a pasta *src/components* e, em seguida, escolha **Adicionar** > **Novo Item**.

1. Selecione **Componente de Arquivo Único JavaScript Vue** ou **Componente de Arquivo Único TypeScript Vue** e, em seguida, clique em **Adicionar**.

    O Visual Studio adiciona o novo arquivo ao projeto.

## <a name="build-the-project"></a>Compilar o projeto

1. (Somente projeto TypeScript) No Visual Studio, escolha **Compilar** > **Limpar Solução**.

1. Em seguida, escolha **Compilar** > **Compilar Solução** para criar o projeto. Verifique a janela de **Saída** para ver os resultados do build e escolha **Build** na lista **Mostrar saída de**.

    O modelo de projeto Vue.js usa o script npm `build`, configurando um evento pós-build. Caso deseje modificar essa configuração, abra o arquivo de projeto ( *\<projectname\>.njsproj*) no Windows Explorer e localize esta linha de código:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Executar o aplicativo

1. Pressione **Ctrl**+**F5** (ou **Depurar > Iniciar sem Depuração**) para executar o aplicativo.

   No console, você verá a mensagem *Iniciando Development Server*.

   Em seguida, o aplicativo será aberto em um navegador.

   ![Aplicativo Vue.js em execução no navegador](../javascript/media/vuejs-running-app.png)

1. Feche o navegador da Web.

Parabéns por concluir este Guia de Início Rápido! Esperamos que você tenha aprendido um pouco sobre como usar o IDE do Visual Studio e com o Vue.js. Caso deseje se aprofundar mais nas funcionalidades, continue com um tutorial na seção **Tutoriais** do sumário.

## <a name="next-steps"></a>Próximas etapas

- Veja o [Tutorial para Node.js e Express](../nodejs/tutorial-nodejs.md)
- Veja o [Tutorial para Node.js e React](/visualstudio/javascript/tutorial-nodejs-with-react-and-jsx)
- [Implantar o aplicativo no Serviço de Aplicativo do Linux](../javascript/publish-nodejs-app-azure.md)