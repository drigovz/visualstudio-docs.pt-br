---
title: Como executar um programa (C#)
description: Guia de iniciantes sobre como executar um programa C# no Visual Studio.
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
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649646"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Como: Executar um programa C# no Visual Studio

O que você precisa fazer para executar um programa depende do que você está começando, que tipo de programa, aplicativo ou serviço é, e se você quer executá-lo sob o depurador ou não. No caso mais simples, quando você tiver um projeto aberto no Visual Studio, construa e execute-o pressionando **Ctrl**+**F5** **(Iniciar sem depuração)** ou **F5** **(Comece com a depuração),** ou pressione o arqueiro verde **(Botão de Partida)** na barra de ferramentas principal do Visual Studio.

![Captura de tela mostrando botão de partida](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>A partir de um projeto

Se você tem um projeto C# (arquivo *.csproj),* então você pode executá-lo, se for um programa executável. Se um projeto contiver um `Main` arquivo C# com um método, e sua saída for um EXE executável, então provavelmente ele será executado se for construído com sucesso.

Se você já tem o código para o seu programa em um projeto no Visual Studio, abra o projeto. Para abrir o projeto, clique duas vezes ou toque no *.csproj* do Windows File Explorer ou no Visual Studio, escolha **Abrir um projeto,** procurar encontrar o arquivo project *(.csproj)* e escolher o arquivo do projeto.

Após as cargas dos projetos no Visual Studio, pressione **Ctrl**+**F5** **(Iniciar sem depuração)** ou use o botão verde **Iniciar** na barra de ferramentas do Visual Studio para executar o programa.  Se houver vários projetos, aquele `Main` com o método deve ser definido como o projeto de inicialização. Para definir o projeto de inicialização, clique com o botão direito do mouse em um nó de projeto e escolha **Definir como projeto de inicialização**.

![Definir projeto de inicialização](media/set-as-startup-project.png)

O Visual Studio tenta construir e executar seu projeto.  Se houver erros de compilação, você verá a saída de compilação na janela **Saída** e os erros na janela **Lista de erros.**

Se a compilação for bem sucedida, o aplicativo será executado de uma forma apropriada para o tipo de projeto. Aplicativos de console são executados em uma janela de terminal, aplicativos de desktop do Windows começam em uma nova janela, os aplicativos da Web começam no navegador (hospedado pelo IIS Express), e assim por diante.

## <a name="starting-from-code"></a>A partir do código

Se você está começando a partir de uma listagem de código, arquivo de código ou um pequeno número de arquivos, primeiro certifique-se de que o código que você deseja executar é de uma fonte confiável e é um programa executável. Se ele `Main` tiver um método, provavelmente é destinado como um programa executável que você pode usar o modelo console App para criar um projeto para trabalhar com ele no Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Listagem de código para um único arquivo

Inicie o Visual Studio, abra um projeto de console C# vazio, selecione todo o código no arquivo .cs que já está no projeto e exclua-o. Em seguida, cole o conteúdo do seu código no arquivo .cs. Quando você colar o código, sobrepor ou excluir o código que estava lá antes. Renomeie o arquivo para corresponder ao código original.

### <a name="code-listings-for-a-few-files"></a>Listas de código para alguns arquivos

Inicie o Visual Studio, abra um projeto de console C# vazio, selecione todo o código no arquivo .cs que já está no projeto e exclua-o. Em seguida, cole o conteúdo do primeiro arquivo de código no arquivo .cs. Renomeie o arquivo para corresponder ao código original. 

Para um segundo arquivo, clique com o botão direito do mouse no nó do projeto no **Solution Explorer** para abrir o menu de atalho para o projeto e escolha Adicionar **> Item Existente** (ou use a combinação de teclas **Shift**+**Alt**+**A),** e selecione os arquivos de código.

### <a name="multiple-files-on-disk"></a>Vários arquivos em disco

1. Crie um novo projeto do tipo apropriado (use C# **Console App,** se você não tiver certeza).

2. Clique com o botão direito do mouse no nó do projeto, se **Adicionar** > **item existente** para selecionar os arquivos e importá-los para o seu projeto.  

### <a name="starting-from-a-folder"></a>A partir de uma pasta

Quando você estiver trabalhando com uma pasta de muitos arquivos, primeiro veja se há um projeto ou solução.  Se o programa foi criado com o Visual Studio, você deve encontrar um arquivo de projeto ou um arquivo de solução. Procure arquivos com a extensão *.csproj* ou extensão .sln e no Windows File Explorer, clique duas vezes em um deles para abri-los no Visual Studio. Consulte [A partir de uma solução ou projeto do Visual Studio.](#starting-from-a-project)

Se você não tiver um arquivo de projeto, como se o código foi desenvolvido em outro ambiente de desenvolvimento, então abra a pasta de nível superior usando o método **de pasta Aberta** no Visual Studio. Consulte [Desenvolver código sem projetos ou soluções](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>A partir de um repo GitHub ou Azure DevOps

Se o código que você deseja executar estiver no GitHub ou em um repo Azure DevOps, você pode usar o Visual Studio para abrir o projeto diretamente do repo. Consulte [Abrir um projeto a partir de um repo](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Execute o programa

Para iniciar o programa, pressione o arqueiro verde (botão**Iniciar)** na barra de ferramentas principal do Visual Studio ou pressione **F5** ou **Ctrl**+**F5** para executar o programa. Quando você usa o botão **Iniciar,** ele é executado sob o depurador.  O Visual Studio tenta construir o código em seu projeto e executá-lo.  Se isso for bem sucedido, ótimo! Mas se não, continue lendo algumas ideias sobre como fazê-lo construir com sucesso.

## <a name="troubleshooting"></a>Solução de problemas

Seu código pode ter erros, mas se o código estiver correto, mas depender apenas de alguns outros conjuntos ou pacotes NuGet, ou foi escrito para segmentar uma versão diferente do .NET, você pode ser capaz de corrigi-lo facilmente.

### <a name="add-references"></a>Adicionar referências

Para construir corretamente, o código deve estar correto e ter as referências certas configuradas para bibliotecas ou outras dependências. Você pode olhar para as linhas vermelhas e na **Lista de erros** para ver se o programa tem algum erro, mesmo antes de compilar e executá-lo. Se você está vendo erros relacionados a nomes não resolvidos, você provavelmente precisa adicionar uma referência ou uma diretiva de uso, ou ambos. Se o código fizer referência a quaisquer conjuntos ou pacotes NuGet, você precisará adicionar essas referências no projeto.

O Visual Studio tenta ajudá-lo a identificar referências perdidas. Quando um nome não é resolvido, um ícone de lâmpada aparece no editor. Se você clicar na lâmpada, você pode ver algumas sugestões sobre como corrigir o problema. Correções podem ser:

- adicionar uma diretiva de uso
- adicionar uma referência a uma assembléia, ou
- instalar um pacote NuGet.

#### <a name="missing-using-directive"></a>Faltando usando diretiva

Por exemplo, na tela a seguir, `using System;` você pode optar por adicionar ao `Console`início do arquivo de código para resolver o nome não resolvido:

![Captura de tela de lâmpada para adicionar uma diretiva de uso](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Referência de montagem ausente

As referências .NET podem ser na forma de conjuntos ou pacotes NuGet. Normalmente, se você encontrar código fonte, o editor ou autor explicará quais conjuntos são necessários e quais pacotes o código depende. Para adicionar uma referência a um projeto manualmente, clique com o botão direito do mouse no nó **Referências** no **Explorador de soluções,** escolha **Adicionar referência**e localize o conjunto necessário.

![Captura de tela do menu Adicionar referência](media/add-reference.png)

Você pode encontrar conjuntos e adicionar referências seguindo as instruções em [Adicionar ou remover referências usando o gerenciador de referências](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

#### <a name="missing-nuget-package"></a>Pacote NuGet ausente

Se o Visual Studio detectar um pacote NuGet ausente, uma lâmpada aparecerá e lhe der a opção de instalá-lo:

![Captura de tela de lâmpada para instalar pacote](media/lightbulb-add-package.png)

Se isso não resolver o problema e o Visual Studio não conseguir localizar o pacote, tente procurá-lo online. Consulte [Instalar e usar um pacote NuGet no Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Use a versão certa do .NET

Como diferentes versões do .NET Framework têm algum grau de compatibilidade retrógrada, uma nova estrutura pode executar código sumido para uma estrutura mais antiga sem quaisquer modificações. Mas, às vezes, você precisa mirar em uma estrutura específica. Você pode precisar instalar uma versão específica do .NET Framework ou .NET Core, se ele ainda não estiver instalado. Consulte [Modify Visual Studio](../../install/modify-visual-studio.md).

Para alterar o quadro de destino, consulte [Alterar o quadro de destino](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Para obter mais informações, consulte [Erros de segmentação do Framework .NET](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Próximas etapas

Explore o ambiente de desenvolvimento do Visual Studio lendo [Welcome to the Visual Studio IDE](../visual-studio-ide.md).

## <a name="see-also"></a>Confira também

[Crie seu primeiro aplicativo C#](tutorial-console.md)
