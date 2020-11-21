---
title: Alterar a experiência de inicialização
description: Saiba como personalizar sua experiência de inicialização para que o Visual estúdios seja aberto com as ferramentas que são mais úteis para você.
ms.custom: SEO-VS-2020
ms.date: 02/01/2017
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 827ac67840f272e17cec6a7882a02b58dddbf925
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006257"
---
# <a name="customize-startup"></a>Personalizar a inicialização

Você pode personalizar a experiência de inicialização do Visual Studio de várias maneiras diferentes, como abrir a solução mais recente ou apenas um ambiente de desenvolvimento vazio.

::: moniker range="vs-2017"

Também é possível mostrar uma página inicial personalizada, que é uma página XAML do Windows Presentation Foundation (WPF) executada em uma janela de ferramenta e pode executar comandos que são internos do Visual Studio.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Para alterar o item de inicialização

1. Na barra de menus, escolha **ferramentas**  >  **Opções**.

2. Expanda **Ambiente** e escolha **Inicialização**.

::: moniker range="vs-2017"

3. Na lista **Na inicialização**, escolha o item a ser exibido depois que o Visual Studio inicia.

::: moniker-end

::: moniker range=">=vs-2019"

3. Na lista **Na inicialização, abrir**, escolha o que deve acontecer depois que o Visual Studio é iniciado. Escolha entre **janela Iniciar** (que permite abrir um projeto novo ou existente), **Solução mais recente** ou **Ambiente vazio**.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Para mostrar uma página inicial personalizada

Você pode [criar sua própria página inicial personalizada](../extensibility/creating-a-custom-start-page.md) usando o SDK do Visual Studio ou usar uma que alguém criou. Por exemplo, você pode encontrar as páginas iniciais personalizadas no [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Para instalar uma página inicial personalizada, abra um arquivo *.vsix* ou copie e cole os arquivos de página inicial na pasta *%USERPROFILE% \Documents\Visual Studio 2017\StartPages* do computador.

### <a name="to-select-which-custom-start-page-to-display"></a>Para selecionar qual página inicial personalizada exibir

1. Na barra de menus, escolha **Ferramentas** > **Opções**.

1. Expanda **Ambiente** e escolha **Inicialização**.

1. Na lista **Personalizar Página Inicial**, escolha a página desejada.

> [!TIP]
> Se um erro em uma página inicial personalizada causar pane no Visual Studio, você poderá abrir o Visual Studio no modo de segurança e defini-lo para usar a página inicial padrão. Consulte [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Confira também

- [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end
