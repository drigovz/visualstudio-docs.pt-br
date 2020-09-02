---
title: Como executar um programa (C#)
description: Guia para iniciantes sobre como executar um programa em C# no Visual Studio.
ms.custom: get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ee28bde6de10006ccfdc5175cca629ad9d1590d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649646"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Como executar um programa em C# no Visual Studio

O que você precisa fazer para executar um programa depende do que você está iniciando, que tipo de programa, aplicativo ou serviço é, e se você deseja executá-lo no depurador ou não. No caso mais simples, quando você tem um projeto aberto no Visual Studio, crie-o e execute-o pressionando **Ctrl** + **F5** (**Iniciar sem depuração**) ou **F5** (**comece com a depuração**) ou pressione a seta verde (**botão iniciar**) na barra de ferramentas principal do Visual Studio.

![Captura de tela mostrando o botão iniciar](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Iniciando com base em um projeto

Se você tiver um projeto C# (arquivo *. csproj* ), poderá executá-lo, se for um programa executável. Se um projeto contiver um arquivo C# com um `Main` método e sua saída for um executável (exe), provavelmente ele será executado se ele for compilado com êxito.

Se você já tiver o código para seu programa em um projeto no Visual Studio, abra o projeto. Para abrir o projeto, clique duas vezes ou toque em *. csproj* no explorador de arquivos do Windows ou no Visual Studio, escolha **abrir um projeto**, navegue para localizar o arquivo de projeto (*. csproj*) e escolha o arquivo de projeto.

Depois que os projetos forem carregados no Visual Studio, pressione **Ctrl** + **F5** (**Iniciar sem depuração**) ou use o botão verde **Iniciar** na barra de ferramentas do Visual Studio para executar o programa.  Se houver vários projetos, aquele com o `Main` método deverá ser definido como o projeto de inicialização. Para definir o projeto de inicialização, clique com o botão direito do mouse em um nó do projeto e escolha **definir como projeto de inicialização**.

![Definir projeto de inicialização](media/set-as-startup-project.png)

O Visual Studio tenta compilar e executar o projeto.  Se houver erros de compilação, você verá a saída da compilação na janela **saída** e os erros na janela **lista de erros** .

Se a compilação for realizada com sucesso, o aplicativo será executado de forma adequada para o tipo de projeto. Os aplicativos de console são executados em uma janela de terminal, os aplicativos da área de trabalho do Windows começam em uma nova janela, os aplicativos Web iniciam no navegador (hospedado por IIS Express) e assim por diante.

## <a name="starting-from-code"></a>A partir do código

Se você estiver iniciando em uma listagem de código, arquivo de código ou um pequeno número de arquivos, primeiro verifique se o código que você deseja executar é de uma fonte confiável e é um programa executável. Se ele tiver um `Main` método, provavelmente se destina a um programa executável que você pode usar o modelo de aplicativo de console para criar um projeto para trabalhar com ele no Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Listagem de código para um único arquivo

Inicie o Visual Studio, abra um projeto de console em C# vazio, selecione todo o código no arquivo. cs que já está no projeto e exclua-o. Em seguida, Cole o conteúdo do código no arquivo. cs. Ao colar o código, substitua ou exclua o código que estava lá antes. Renomeie o arquivo para corresponder ao código original.

### <a name="code-listings-for-a-few-files"></a>Listagens de código para alguns arquivos

Inicie o Visual Studio, abra um projeto de console em C# vazio, selecione todo o código no arquivo. cs que já está no projeto e exclua-o. Em seguida, Cole o conteúdo do primeiro arquivo de código no arquivo. cs. Renomeie o arquivo para corresponder ao código original. 

Para um segundo arquivo, clique com o botão direito do mouse no nó do projeto em **Gerenciador de soluções** para abrir o menu de atalho para o projeto e escolha **Adicionar > item existente** (ou use a combinação de teclas **Shift** + **Alt** + **a Alt a**) e selecione os arquivos de código.

### <a name="multiple-files-on-disk"></a>Vários arquivos em disco

1. Crie um novo projeto do tipo apropriado (use o **aplicativo de console** em C# se você não tiver certeza).

2. Clique com o botão direito do mouse no nó do projeto, se **Adicionar**  >  **Item existente** para selecionar os arquivos e importá-los para seu projeto.  

### <a name="starting-from-a-folder"></a>Iniciando com base em uma pasta

Quando você estiver trabalhando com uma pasta de muitos arquivos, primeiro veja se há um projeto ou solução.  Se o programa foi criado com o Visual Studio, você deve encontrar um arquivo de projeto ou um arquivo de solução. Procure arquivos com a extensão *. csproj* ou a extensão. sln e, no explorador de arquivos do Windows, clique duas vezes em um deles para abri-los no Visual Studio. Consulte [Iniciando em uma solução ou projeto do Visual Studio](#starting-from-a-project).

Se você não tiver um arquivo de projeto, como se o código foi desenvolvido em outro ambiente de desenvolvimento, abra a pasta de nível superior usando o método **abrir pasta** no Visual Studio. Consulte [desenvolver código sem projetos ou soluções](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>Iniciando em um repositório do GitHub ou DevOps do Azure

Se o código que você deseja executar estiver no GitHub ou em um repositório DevOps do Azure, você poderá usar o Visual Studio para abrir o projeto diretamente do repositório. Consulte [abrir um projeto de um repositório](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Executar o programa

Para iniciar o programa, pressione a seta verde (botão**Iniciar** ) na barra de ferramentas principal do Visual Studio ou pressione **F5** ou **Ctrl** + **F5** para executar o programa. Quando você usa o botão **Iniciar** , ele é executado no depurador.  O Visual Studio tenta criar o código em seu projeto e executá-lo.  Se isso for bem sucedido, ótimo! Mas, se não estiver, continue lendo algumas ideias sobre como fazê-lo compilar com êxito.

## <a name="troubleshooting"></a>Solução de problemas

Seu código pode ter erros, mas se o código estiver correto, mas apenas depende de alguns outros assemblies ou pacotes NuGet, ou foi escrito para direcionar a uma versão diferente do .NET, você poderá corrigi-lo facilmente.

### <a name="add-references"></a>Adicionar referências

Para compilar corretamente, o código deve estar correto e ter as referências corretas configuradas para bibliotecas ou outras dependências. Você pode examinar as linhas onduladas vermelhas e, na **lista de erros** para ver se o programa tem algum erro, mesmo antes de compilá-lo e executá-lo. Se você estiver vendo erros relacionados a nomes não resolvidos, provavelmente precisará adicionar uma referência ou uma diretiva de uso, ou ambos. Se o código fizer referência a qualquer assembly ou pacotes NuGet, você precisará adicionar essas referências no projeto.

O Visual Studio tenta ajudá-lo a identificar referências ausentes. Quando um nome não é resolvido, um ícone de lâmpada aparece no editor. Se você clicar na lâmpada, poderá ver algumas sugestões sobre como corrigir o problema. As correções podem ser:

- Adicionar uma diretiva using
- Adicionar uma referência a um assembly ou
- instalar um pacote NuGet.

#### <a name="missing-using-directive"></a>Diretiva de uso ausente

Por exemplo, na tela a seguir, você pode optar por adicionar `using System;` ao início do arquivo de código para resolver o nome não resolvido `Console` :

![Captura de tela de lâmpada para adicionar uma diretiva de uso](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Referência de assembly ausente

As referências do .NET podem estar na forma de assemblies ou pacotes NuGet. Normalmente, se você encontrar o código-fonte, o editor ou autor explicará quais assemblies são necessários e em quais pacotes o código depende. Para adicionar uma referência a um projeto manualmente, clique com o botão direito do mouse no nó **referências** na **Gerenciador de soluções**, escolha **Adicionar referência**e localize o assembly necessário.

![Captura de tela do menu Adicionar referência](media/add-reference.png)

Você pode encontrar assemblies e adicionar referências seguindo as instruções em [Adicionar ou remover referências usando o Gerenciador de referências](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

#### <a name="missing-nuget-package"></a>Pacote NuGet ausente

Se o Visual Studio detectar um pacote NuGet ausente, uma lâmpada será exibida e lhe dará a opção de instalá-lo:

![Captura de tela de lâmpada para instalar o pacote](media/lightbulb-add-package.png)

Se isso não resolver o problema e o Visual Studio não conseguir localizar o pacote, tente procurá-lo online. Consulte [instalar e usar um pacote NuGet no Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Usar a versão correta do .NET

Como versões diferentes do .NET Framework têm algum grau de compatibilidade com versões anteriores, uma estrutura mais nova pode executar código escrito para uma estrutura mais antiga sem nenhuma modificação. Mas, às vezes, você precisa ter como alvo uma estrutura específica. Talvez seja necessário instalar uma versão específica do .NET Framework ou do .NET Core, se ele ainda não estiver instalado. Consulte [Modificar o Visual Studio](../../install/modify-visual-studio.md).

Para alterar a estrutura de destino, consulte [alterar a estrutura de destino](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Para obter mais informações, consulte [Solucionando problemas de .NET Framework direcionando erros](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Próximas etapas

Explore o ambiente de desenvolvimento do Visual Studio lendo [Bem-vindo ao IDE do Visual Studio](../visual-studio-ide.md).

## <a name="see-also"></a>Confira também

[Criar seu primeiro aplicativo em C#](tutorial-console.md)
