---
title: Usar a Pesquisa do Visual Studio
description: Aprenda a usar o Visual Studio Search para localizar configurações, menus e código.
ms.date: 10/08/2020
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.QuickLaunch
- IDE navigator
ms.assetid: 3870a8fd-4afa-4f1e-a811-9fdf41a9e82d
monikerRange: vs-2019
author: profexorgeek
ms.author: jusjohns
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 101875b3a600a71c832498d05073187d2cf0b774
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873899"
---
# <a name="use-visual-studio-search"></a>Usar a pesquisa do Visual Studio

O IDE (ambiente de desenvolvimento integrado) do Visual Studio tem muitos menus, opções e recursos, que podem ser difíceis de lembrar. O recurso de pesquisa do Visual Studio é uma caixa de pesquisa única que ajuda os desenvolvedores a localizar menus e opções do IDE, enquanto também pesquisa seu código. Se você é novo no Visual Studio ou em um desenvolvedor experiente, esse recurso oferece uma maneira rápida de Pesquisar entre os recursos do IDE e seu código.

Use o atalho de teclado **Ctrl** + **Q** para acessar a caixa de pesquisa ou clique na caixa de entrada de pesquisa do Visual Studio, localizada ao lado da barra de menus por padrão:

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Caixa de pesquisa do Visual Studio" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> O comando executado pela pesquisa do Visual Studio é `Window.QuickLaunch` e você pode ver esse recurso conhecido como pesquisa rápida ou início rápido.

Ao contrário de outros recursos de pesquisa, como localizar em arquivos ou Pesquisar Gerenciador de Soluções, a pesquisa nos resultados do Visual Studio inclui recursos de IDE, opções de menu, nomes de arquivos e muito mais. As seções a seguir discutem os diferentes tipos de resultados que o Visual Studio Search pode encontrar.

## <a name="search-menus-options-and-windows"></a>Pesquisar menus, opções e janelas

Você pode usar a caixa de pesquisa do Visual Studio para localizar configurações, opções e itens de configuração semelhantes. Por exemplo, pesquise por *alterar tema* para localizar e abrir rapidamente a caixa de diálogo que permite alterar o tema de cores do Visual Studio, conforme mostrado na seguinte captura de tela:

:::image type="content" source="media/visual-studio-search-options.png" alt-text="Pesquisar configurações e opções do Visual Studio":::

> [!TIP]
> Na maioria dos casos, a pesquisa do Visual Studio também o lembrará do menu, das teclas de atalho e do local de cada item nos resultados.

Você pode usar a caixa de pesquisa do Visual Studio para localizar itens de menu e comandos. Por exemplo, pesquise *sol limpo* para localizar e executar rapidamente o comando limpar solução. Os resultados da pesquisa também oferecem um lembrete de onde encontrar esse comando nos menus, conforme mostrado na seguinte captura de tela:

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Pesquisar itens de menu e comandos do Visual Studio":::

Por fim, você pode procurar janelas ou painéis que você pode ter fechado acidentalmente. Por exemplo, pesquise por *teste* para localizar e abrir a janela Gerenciador de testes:

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Pesquisar janelas e painéis do Visual Studio":::

## <a name="search-files-and-code"></a>Pesquisar arquivos e código

A pesquisa do Visual Studio também pesquisa seus itens de solução para nome de arquivo, código, método e outras correspondências. Na captura de tela a seguir, uma pesquisa por *redução* encontrou o arquivo MarkdownMetaExtractor.cs, a `MarkdownMetaExtractor` classe e dois métodos dentro da solução:

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Pesquisar arquivos com a pesquisa do Visual Studio":::

Você também pode fazer uma pesquisa "camel case". Na captura de tela a seguir **, uma pesquisa** por *FSS* encontrou um arquivo, classe e **método imensionar****s** mais antigos:

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="Pesquisa do Camel dobra com o Visual Studio Search":::

## <a name="see-also"></a>Confira também

- [Comandos do Visual Studio](reference/visual-studio-commands.md)