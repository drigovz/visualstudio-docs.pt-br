---
title: Pesquisar uma janela no modo de exibição do Windows | Microsoft Docs
description: Procure uma janela específica na exibição do Windows da ferramenta Spy + + usando seu identificador, legenda, classe ou uma combinação de sua legenda e classe no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0051a17d3a2360776f48cee2bd7f1d2f11a2492
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920096"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Como procurar uma janela na exibição de janelas
Você pode pesquisar uma janela específica no modo de exibição do Windows usando seu identificador, legenda, classe ou uma combinação de sua legenda e classe como critérios de pesquisa. Você também pode especificar a direção inicial da pesquisa. Os campos na caixa de diálogo mostrarão os atributos da janela selecionada na árvore de janelas.

 Comece com a árvore expandida para o segundo nível (todas as janelas que são filhos da área de trabalho), para que você possa identificar as janelas de nível de desktop pelo nome e título da classe. Depois de escolher uma janela de nível de desktop, você pode expandir esse nível para localizar uma janela filho específica.

### <a name="to-search-for-a-window-in-windows-view"></a>Para procurar uma janela no modo de exibição do Windows

1. Organize suas janelas para que o Spy + +, a janela [exibição do Windows](../debugger/windows-view.md) e a janela de destino fiquem visíveis.

2. No menu **Pesquisar** , escolha **localizar janela**.

    A [caixa de diálogo pesquisa de janela](../debugger/window-search-dialog-box.md) é aberta.

   > [!TIP]
   > Para reduzir a desordem na tela, selecione a opção **ocultar Spy** . Essa opção oculta a janela principal do Spy + + e deixa apenas a caixa de diálogo **pesquisa de janela** visível sobre seus outros aplicativos. A janela principal Spy + + é restaurada quando você clica em **OK** ou em **Cancelar**, ou quando você desmarca a opção **ocultar Spy + +** .

3. Arraste a **ferramenta localizador** sobre a janela de destino. À medida que você arrasta a ferramenta, a caixa de diálogo **pesquisa de janela** exibe detalhes na janela selecionada.

   - ou –

     Se você souber o identificador da janela que deseja (por exemplo, do depurador), poderá digitá-lo na caixa **identificador** .

   - ou –

     Se você souber a legenda e/ou a classe da janela desejada, poderá digitá-las nas caixas de texto **legenda** e **classe** e desmarcar a caixa de texto **identificador** .

4. Escolha para **cima** ou para **baixo** na direção inicial da pesquisa.

5. Clique em **OK**.

    Se uma janela correspondente for encontrada, ela será realçada na janela [exibição do Windows](../debugger/windows-view.md) .