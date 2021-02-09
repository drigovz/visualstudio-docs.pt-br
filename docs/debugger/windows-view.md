---
title: Exibição do Windows | Microsoft Docs
description: A exibição do Windows mostra uma árvore de todas as janelas e controles. Use-o como ponto de partida para obter informações sobre o Windows de interesse.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.windowsview
helpviewer_keywords:
- Windows view
ms.assetid: 154786ce-c803-4bfb-8198-f7962a900363
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 34a66e9c2728798330b52f87afe8ecdea8733508
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906332"
---
# <a name="windows-view"></a>Exibição de janelas
Quando você abre o Spy + + pela primeira vez, a exibição do Windows exibe uma árvore de todas as janelas e controles no sistema. O identificador da janela e o nome da classe são mostrados. A janela da área de trabalho atual está na parte superior da árvore. Todas as outras janelas são filhas da área de trabalho e são listadas de acordo com a hierarquia de janela padrão. As janelas irmãos aparecem em listas de expansible recuadas abaixo de seus pais.

 A figura a seguir mostra uma exibição típica do Windows Spy + + com o nó superior expandido.

 ![Exibição do Spy&#43;&#43; Windows](../debugger/media/spy--_windowsview.png "Spy + + _WindowsView") Exibição do Spy + + Windows

 A janela da área de trabalho atual está na parte superior da árvore. Todas as outras janelas são filhas da área de trabalho e são listadas de acordo com a hierarquia de janela padrão, com janelas irmãos ordenadas por ordem Z. Você pode expandir ou recolher qualquer nó pai da árvore clicando no símbolo + ou-ao lado do nó.

 Quando a exibição do Windows tiver o foco, você poderá usar a ferramenta Finder na [caixa de diálogo pesquisa de janela](../debugger/window-search-dialog-box.md) para exibir informações de qualquer janela aberta no sistema.

## <a name="in-this-section"></a>Nesta seção
 [Como: usar a ferramenta Finder](../debugger/how-to-use-the-finder-tool.md) Mostra como essa ferramenta verifica o Windows em busca de propriedades ou mensagens.

 [Como: procurar uma janela no modo de exibição do Windows](../debugger/how-to-search-for-a-window-in-windows-view.md) Explica como localizar uma janela específica no modo de exibição do Windows.

 [Como: exibir as propriedades da janela](../debugger/how-to-display-window-properties.md) m procedimentos para abrir a caixa de diálogo Propriedades da janela.

## <a name="related-sections"></a>Seções relacionadas
 [Modos de exibição do Spy + +](../debugger/spy-increment-views.md) Explica as exibições de árvore do Spy + + do Windows, mensagens, processos e threads.

 [Usando o Spy + +](../debugger/using-spy-increment.md) Apresenta a ferramenta Spy + + e explica como ela pode ser usada.

 [Caixa de diálogo localizar janela](../debugger/find-window-dialog-box.md) Usado para exibir as propriedades ou mensagens de uma janela específica.

 [Caixa de diálogo pesquisa de janela](../debugger/window-search-dialog-box.md) Usado para localizar o nó de uma janela específica no modo de exibição do Windows.

 [Caixa de diálogo Propriedades da janela](../debugger/window-properties-dialog-box.md) Usado para exibir as propriedades de uma janela selecionada no modo de exibição do Windows.

 [Referência do Spy + +](../debugger/spy-increment-reference.md) Inclui seções que descrevem cada menu e caixa de diálogo do Spy + +.