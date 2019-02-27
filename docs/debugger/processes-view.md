---
title: Exibição de processos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ba60021410f1965e05f7c5479231013d53cb71
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697618"
---
# <a name="processes-view"></a>Exibição de processos
A tela processos exibe uma árvore de todos os processos ativos no sistema. O nome do módulo e a ID de processo são mostrados. Se você quiser examinar um processo de determinado sistema, que normalmente corresponde a um programa em execução, use o modo de exibição de processos. Processos são identificados por nomes de módulo, ou eles são designados "processos do sistema".

 Microsoft Windows dá suporte a vários processos. Cada processo pode ter um ou mais threads e cada thread pode ter um ou mais associadas janelas de nível superior. Cada janela de nível superior pode possuir uma série de janelas. Um + símbolo indica que um nível é recolhido. Modo de exibição recolhido consiste em uma linha por processo. Clique o símbolo para expandir o nível +.

 Se você quiser examinar um processo de determinado sistema, que normalmente corresponde a um programa em execução, use o modo de exibição de processos. Processos são identificados por nomes de módulo, ou eles são designados "processos do sistema". Para localizar um processo, recolher a árvore e a lista de pesquisa.

## <a name="procedures"></a>Procedimentos

#### <a name="to-open-the-processes-view"></a>Para abrir a exibição de processos

1. Dos **Spy** menu, escolha **processos**.

   ![Spy&#43; &#43; exibição de processos](../debugger/media/spy--_processes.png "Spy + + _Processes") exibição de processos do Spy + +

   A figura acima mostra a exibição de processos conosco de processo e thread expandidos.

### <a name="in-this-section"></a>Nesta seção
 [Procurando por um processo na exibição de processos](../debugger/how-to-search-for-a-process-in-processes-view.md) explica como localizar um processo específico na exibição de processos.

 [Exibindo propriedades do processo](../debugger/how-to-display-process-properties.md) explica como mostrar mais informações sobre uma mensagem.

### <a name="related-sections"></a>Seções relacionadas
 [Exibições do Spy + +](../debugger/spy-increment-views.md) explica as exibições de árvore do Spy + + do windows, as mensagens, processos e threads.

 [Usando Spy + +](../debugger/using-spy-increment.md) apresenta a ferramenta Spy + + e explica como ele pode ser usado.

 [Processar caixa de diálogo Pesquisar](../debugger/process-search-dialog-box.md) usado para localizar o nó para um determinado processo na exibição de processos.

 [Caixa de diálogo Propriedades de processar](../debugger/process-properties-dialog-box.md) exibe as propriedades de um processo selecionado na exibição de processos.

 [Referência de Spy + +](../debugger/spy-increment-reference.md) inclui as seções que descrevem cada Spy + + menu e caixa de diálogo caixa.