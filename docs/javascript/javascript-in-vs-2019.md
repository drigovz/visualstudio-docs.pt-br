---
title: JavaScript e TypeScript no Visual Studio 2019
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 199a27dbfef2b7297563e87d973137e2acd9c745
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544283"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript e TypeScript no Visual Studio 2019

## <a name="overview"></a>Visão geral

O Visual Studio 2019 oferece suporte avançado para desenvolvimento de JavaScript, usando JavaScript diretamente ou a [linguagem de programação TypeScript](http://www.typescriptlang.org/), desenvolvida para proporcionar uma experiência de desenvolvimento de JavaScript mais produtiva e agradável, especialmente ao desenvolver projetos em escala. É possível escrever código JavaScript ou TypeScript no Visual Studio para muitos tipos de aplicativos e serviços.

## <a name="javascript-language-service"></a>Serviço de linguagem JavaScript

A experiência de JavaScript no Visual Studio de 2019 é alimentada pelo mesmo mecanismo que oferece suporte a TypeScript. Isso oferece um melhor suporte a recursos, sofisticação e integração prontos para uso.

A opção de restaurar o serviço de linguagem JavaScript herdado não está mais disponível. Os usuários agora têm o novo serviço de linguagem JavaScript pronto para uso. O novo serviço de linguagem baseia-se exclusivamente no serviço de linguagem TypeScript, que é alimentado por análise estática. Isso permite fornecer a você melhores ferramentas, para que seu código JavaScript possa se beneficiar de um IntelliSense mais sofisticado com base nas definições de tipo. O novo serviço é leve e consome menos memória do que o serviço herdado, fornecendo a você um melhor desempenho conforme o escalonamento do seu código. Também melhoramos o desempenho do serviço de linguagem para lidar com projetos maiores.

## <a name="typescript-support"></a>Suporte a TypeScript

O Visual Studio 2019 fornece várias opções para a integração de compilação de TypeScript ao seu projeto:

* [O pacote NuGet do TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Quando o pacote do NuGet para o TypeScript 3.2 ou posterior está instalado em seu projeto, a versão correspondente do serviço de linguagem TypeScript é carregada no editor.
* [O pacote npm do TypeScript](https://www.npmjs.com/package/typescript). Quando o pacote npm para o TypeScript 2.1 ou posterior está instalado em seu projeto, a versão correspondente do serviço de linguagem TypeScript é carregada no editor.
* O TypeScript SDK, disponível por padrão no instalador do Visual Studio, bem como um download de SDK autônomo do [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017).

> [!TIP]
> Para projetos desenvolvidos no Visual Studio 2019, encorajamos você a usar o TypeScript NuGet ou o pacote TypeScript npm para maior portabilidade em diferentes plataformas e ambientes.

Um uso comum para o pacote NuGet é compilar TypeScript usando o .NET Core CLI. A menos que você edite manualmente seu arquivo de projeto para importar alvos de compilação a partir de uma instalação do `dotnet build` `dotnet publish`TypeScript SDK, o pacote NuGet é a única maneira de ativar a compilação TypeScript usando comandos .NET Core CLI, tais como e .

## <a name="remove-default-imports-aspnet-core-projects"></a>Remover importações padrão (ASP.NET projetos core)

Em projetos mais antigos que usam o [formato não-SDK,](https://docs.microsoft.com/nuget/resources/check-project-format)você pode precisar remover alguns elementos de arquivo do projeto.

Se você estiver usando o pacote NuGet para suporte ao MSBuild para um projeto, o arquivo do projeto não deve importar `Microsoft.TypeScript.Default.props` ou `Microsoft.TypeScript.targets`. Os arquivos são importados pelo pacote NuGet, então incluí-los separadamente pode causar comportamento não intencional.

1. Clique com o botão direito do mouse no projeto e escolha **Descarregar Projeto**.

1. Clique com o botão direito do mouse no projeto e escolha **Editar \< *o nome*\>do arquivo do projeto**.

   O arquivo do projeto é aberto.

1. Remova referências `Microsoft.TypeScript.Default.props` `Microsoft.TypeScript.targets`e .

   As importações para remover são semelhantes às seguintes:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```

## <a name="projects"></a>Projetos

Aplicativos JavaScript da UWP não são mais compatíveis com o Visual Studio 2019. Não é possível criar ou abrir projetos da UWP em JavaScript (arquivos com extensão *.jsproj*). Você pode saber mais na documentação sobre como [criar PWAs (Aplicativos Web Progressivos)](/microsoft-edge/progressive-web-apps/get-started) que são executados perfeitamente no Windows.
