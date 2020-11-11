---
title: Soluções e Projetos
description: Este documento fornece uma visão geral dos Projetos e Soluções no Visual Studio para Mac.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: c52b8513937505b40d17f7cd9fc05d9cf6a47941
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493394"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Projetos e soluções no Visual Studio para Mac

Este artigo fornece uma visão geral dos conceitos de *projeto* e *solução* no Visual Studio para Mac.

> [!NOTE] 
> Este tópico se aplica ao Visual Studio para Mac. Para o Visual Studio no Windows, confira [Projetos e soluções no Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Projetos

Ao criar um aplicativo, site etc. no Visual Studio para Mac, você começa com um projeto. O projeto contém todos os arquivos (código-fonte, imagens, arquivos de dados etc.) que são necessários para compilar o executável, a biblioteca ou o site.

Um projeto é definido por um arquivo (por exemplo, `.csproj` para projetos C#) que contém um XML que define o arquivo e a hierarquia de pastas, os caminhos para arquivos e configurações específicas do projeto, como configurações de build.

Quando um projeto é carregado pelo Visual Studio para Mac, a janela da solução usa o arquivo de projeto para exibir os arquivos e as pastas em seu projeto. Durante a compilação, o MSBuild lê as configurações do arquivo de projeto para criar o executável.

## <a name="solutions"></a>Soluções

Uma *solução* é um contêiner que agrupa um ou mais projetos relacionados. As soluções são descritas por um arquivo de texto (extensão `.sln`) com seu próprio formato exclusivo; ele não se destina à edição manual.

## <a name="managing-projects-in-the-solution-window"></a>Gerenciando projetos na janela da solução

Depois que um projeto tiver sido criado ou carregado, você poderá usar a janela da solução para exibir e gerenciar o projeto ou a solução e os arquivos contidos no. A ilustração a seguir mostra a janela da solução com uma solução .NET Core que contém dois projetos:

![Solução de exemplo com vários projetos](media/solution-example.png)

Você pode gerenciar as propriedades de projetos e soluções clicando duas vezes no nome do projeto ou da solução ou clicando com o botão direito do mouse e escolhendo **Opções**.

Mais informações sobre essas opções são fornecidas no artigo [Gerenciando propriedades de Projetos e Soluções](managing-solutions-and-project-properties.md).

## <a name="see-also"></a>Confira também

- [Soluções e projetos no Visual Studio (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
