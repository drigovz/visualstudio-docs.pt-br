---
title: Gerenciar pacotes npm
description: O Visual Studio ajuda você a gerenciar pacotes usando o npm (gerenciador de pacotes do Node.js)
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 31eab6c10451bb6be9e53870bf2724c188d650f4
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649503"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Gerenciar pacotes de npm no Visual Studio

O npm permite que você instale e gerencie pacotes a serem usados em seus aplicativos Node.js. O Visual Studio facilita a interação com o npm e emite comandos do npm diretamente ou por meio da interface do usuário. Se você não conhece o npm e quer saber mais, acesse a [documentação do npm](https://docs.npmjs.com/).

A integração do Visual Studio com o NPM é diferente dependendo do seu tipo de projeto.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Pasta aberta (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm espera que a pasta *node_modules* e *package.json* na raiz do projeto. Se a estrutura de pastas do seu aplicativo for diferente, você deve modificar sua estrutura de pastas se quiser gerenciar pacotes npm usando o Visual Studio.

## <a name="nodejs-projects"></a>Projetos node.js

Para projetos Node.js, você pode executar as seguintes tarefas:
* [Instalar os pacotes usando o Gerenciador de Soluções](#npmInstallWindow)
* [Gerenciar pacotes instalados usando o Gerenciador de Soluções](#solutionExplorer)
* [Usar o comando `.npm` na janela interativa do Node.js](#interactive)

Esses recursos funcionam juntos e são sincronizados com o sistema de projeto e o arquivo *package.json* no projeto.

### <a name="prerequisites"></a>Pré-requisitos

Você precisa da carga de trabalho **de desenvolvimento node.js** e do tempo de execução do Node.js instalado para adicionar suporte npm ao seu projeto. Para obter etapas detalhadas, consulte [Criar um projeto Node.js](/visualstudio/ide/quickstart-nodejs?toc=/visualstudio/javascript/toc.json).

> [!NOTE]
> Para projetos node.js existentes, use o modelo de solução **de código Node.js existente** ou o tipo de projeto ['Node.js'](../javascript/develop-javascript-code-without-solutions-projects.md) para habilitar o npm em seu projeto.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>Instalar pacotes do Solution Explorer (Node.js)

Para projetos Node.js, a maneira mais fácil de instalar pacotes npm é através da janela de instalação do pacote npm. Para acessar essa janela, clique com o botão direito do mouse no nó do **npm** no projeto e selecione **Instalar Novos Pacotes do npm**.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Instalar o novo pacote do npm usando o Gerenciador de Soluções" border="true":::

Nessa janela, você pode procurar por um pacote, especificar as opções e instalar.

![Pesquisar pacote do npm](../javascript/media/search-package.png)

* **Tipo de dependência** – escolha entre os pacotes **Padrão**, **Desenvolvimento** e **Opcional**. Padrão especifica que o pacote é uma dependência de runtime, enquanto Desenvolvimento especifica que o pacote só é necessário durante o desenvolvimento.
* **Adicionar ao package.json** - Recomendado. Esta opção configurável é depreciada.
* **Versão selecionada** – selecione a versão do pacote que você deseja instalar.
* **Outros argumentos do npm** – especifique outros argumentos padrão do npm. Por exemplo, você pode inserir um valor de versão como `@~0.8` para instalar uma versão específica que não está disponível na lista de versões.

Você pode ver o progresso da instalação na saída **npm** na janela **Saída.** Isso pode levar algum tempo.

![saída npm](../javascript/media/npm-output.png)

> [!TIP]
> É possível pesquisar pacotes com escopo acrescentando a consulta de pesquisa com o escopo desejado, por exemplo, digite `@types/mocha` para procurar por arquivos de definição de TypeScript para moca. Além disso, ao instalar definições de tipo para TypeScript, você pode `@ts2.6` especificar a versão TypeScript que você está mirando adicionando no campo de argumento npm.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Gerenciar pacotes instalados no Solution Explorer (Node.js)

Os pacotes do npm são mostrados no Gerenciador de Soluções. As entradas no nó **npm** imitam as dependências do arquivo *package.json*.

![Pesquisar pacote do npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Status do pacote

* ![Pacote instalado](../javascript/media/installed-npm.png) – Instalado e listado no package.json
* ![Pacote desconhecido](../javascript/media/extraneous-npm.png) – instalado, mas não listado explicitamente no package.json
* ![Pacote ausente](../javascript/media/missing-npm.png) – Não instalado, mas listado no package.json

::: moniker range=">=vs-2019"
Clique com o botão direito do mouse no nó **npm** para tomar uma das seguintes ações:

* **Instale novos pacotes npm** Abre a ui para instalar novos pacotes
* **Instale pacotes npm** Executa o comando npm install para instalar todos os pacotes listados em *package.json*. (Corre `npm install`.)
* **Atualizar pacotes npm** Atualiza um pacote para a versão especificada no *package.json*. (Corre `npm update --save`.)

Clique com o botão direito do mouse em um nó de pacote para tomar uma das seguintes ações:

* **Instale npm Package(s)** Executa o comando npm install para instalar a versão do pacote listada em *package.json*. (Corre `npm install`.)
* **Atualizar npm Pacotes** Atualiza um pacote para a versão especificada no *package.json*. (Corra `npm update --save`.)
* **Desinstale npm Package(s)** Desinstale o pacote e remova-o `npm uninstall --save`do *package.json* (Executa .)
::: moniker-end
::: moniker range="vs-2017"
Clique com o botão direito do mouse em um nó de pacote ou no nó do **npm** para executar uma das seguintes ações:
* **Instalar pacotes ausentes** listados em *package.json*
* **Atualizar pacotes npm** para a versão mais recente
* **Desinstalar um pacote** e remover do *package.json*
::: moniker-end

>[!NOTE]
> Para ajudar a resolver problemas com pacotes npm, consulte [Solução de problemas](#troubleshooting-npm-packages).

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Use o comando .npm na Janela Interativa no dedo.js (Node.js)

Você também pode usar o comando `.npm` na janela interativa do Node.js para executar comandos do npm. Para abrir a janela, clique com o botão direito do mouse no projeto no Gerenciador de Soluções e escolha **Abrir Janela Interativa do Node.js**.

Na janela, você pode usar comandos como o seguinte para instalar um pacote:

`.npm install azure@4.2.3`

 > [!Tip]
 > Por padrão, o npm será executado no diretório inicial do projeto. Se houver vários projetos na solução, especifique o nome ou o caminho do projeto entre colchetes.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Se seu projeto não contiver um arquivo package.json, use `.npm init -y` para criar um novo arquivo package.json com as entradas padrão.

 ## <a name="aspnet-core-projects"></a>ASP.NET projetos do Núcleo

Para projetos como ASP.NET Projetos Core, você pode integrar o suporte npm em seu projeto e usar npm para instalar pacotes.
* [Adicionar suporte npm a um projeto](#npmAdd)
* [Instale pacotes usando package.json](#npmInstallPackage)

>[!NOTE]
> Para ASP.NET projetos Core, você também pode usar [o Library Manager](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) ou o fio em vez de npm para instalar arquivos JavaScript e CSS do lado do cliente.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Adicionar suporte npm a um projeto (ASP.NET Core)

Se o seu projeto ainda não incluir um arquivo *package.json,* você pode adicionar um para habilitar o suporte ao npm adicionando um arquivo *package.json* ao projeto.

1. Se você não tiver o Node.js instalado, recomendamos que você instale a versão LTS do site [node.js](https://nodejs.org/en/download/) para melhor compatibilidade com frameworks e bibliotecas externas.

   npm requer Node.js.

1. Para adicionar o arquivo *package.json,* clique com o botão direito do mouse no projeto no Solution Explorer e escolha **Adicionar** > **novo item**. Escolha o **arquivo de configuração npm,** use o nome padrão e clique **em Adicionar**.

   ![Adicione package.json ao seu projeto](../javascript/media/npm-add-package-json.png)

   Se você não ver o arquivo de configuração npm listado, as ferramentas de desenvolvimento node.js não serão instaladas. Você pode usar o Visual Studio Installer para adicionar a carga de trabalho de **desenvolvimento node.js.** Em seguida, repita o passo anterior.

1. Inclua um ou mais pacotes `dependencies` `devDependencies` npm na seção ou na seção *do package.json*. Por exemplo, você pode adicionar o seguinte ao arquivo:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Quando você salva o arquivo, o Visual Studio adiciona o pacote sob o nó **Dependências / npm** no Solution Explorer. Se você não ver o nó, clique com o botão direito do **mouse em package.json** e escolha **Restaurar pacotes**.

>[!NOTE]
> Em alguns cenários, o Solution Explorer pode não mostrar o status correto para pacotes npm instalados. Para saber mais, consulte a [Solução de problemas](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Instale pacotes usando package.json (ASP.NET Core)

Para projetos com npm incluído, você pode `package.json`configurar pacotes npm usando . Clique com o botão direito do mouse no nó npm no Solution Explorer e escolha **Open package.json**.

![Pesquisar pacote do npm](../javascript/media/npm-add-package.png)

O IntelliSense no *package.json* ajuda você a selecionar uma versão específica de um pacote npm.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Selecione a versão do pacote npm" border="true":::

Quando você salva o arquivo, o Visual Studio adiciona o pacote sob o nó **Dependências / npm** no Solution Explorer. Se você não ver o nó, clique com o botão direito do **mouse em package.json** e escolha **Restaurar pacotes**.

Pode levar vários minutos para instalar um pacote. Verifique o progresso na instalação do pacote, mudando para saída **npm** na janela **Saída.**

![saída npm](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Solução de problemas de pacotes npm

* npm requer Node.js Se você não tiver o Node.js instalado, recomendamos que você instale a versão LTS do site [node.js](https://nodejs.org/en/download/) para melhor compatibilidade com frameworks e bibliotecas externas.

* Para projetos Node.js, você deve ter a carga de trabalho de **desenvolvimento node.js** instalada para suporte npm.

* Em alguns cenários, o Solution Explorer pode não mostrar o status correto para pacotes npm instalados devido a um problema conhecido descrito [aqui](https://github.com/aspnet/Tooling/issues/479). Por exemplo, o pacote pode aparecer como não instalado quando está instalado. Na maioria dos casos, você pode atualizar o Solution Explorer excluindo *o package.json*, reiniciando o Visual Studio e adicionando o arquivo *package.json* como descrito anteriormente neste artigo. Ou, ao instalar pacotes, você pode usar a janela npm Saída para verificar o status da instalação.

* Se você vir algum erro ao construir seu aplicativo ou transpilar o código TypeScript, verifique se há incompatibilidades no pacote npm como uma fonte potencial de erros. Para ajudar a identificar erros, verifique a janela de saída npm ao instalar os pacotes, conforme descrito anteriormente neste artigo. Por exemplo, se uma ou mais versões do pacote npm foram depreciadas e resultarem em um erro, talvez seja necessário instalar uma versão mais recente para corrigir erros. Para obter informações sobre como usar *package.json* para controlar as versões do pacote de npm, confira [Configuração de package.json](../javascript/configure-packages-with-package-json.md).

