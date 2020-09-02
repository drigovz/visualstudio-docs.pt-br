---
title: Exibição de processos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8b9c04d1cabd44418c70725ef331c9c4b5ec67e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580487"
---
# <a name="processes-view"></a>Exibição de processos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A exibição processos exibe uma árvore de todos os processos ativos em seu sistema. A ID do processo e o nome do módulo são mostrados. Use a exibição processos se desejar examinar um processo de sistema específico, que geralmente corresponde a um programa em execução. Os processos são identificados por nomes de módulo ou são designados como "processos do sistema".  
  
 O Microsoft Windows dá suporte a vários processos. Cada processo pode ter um ou mais threads, e cada thread pode ter uma ou mais janelas de nível superior associadas. Cada janela de nível superior pode possuir uma série de janelas. Um símbolo + indica que um nível está recolhido. A exibição recolhida consiste em uma linha por processo. Clique no símbolo + para expandir o nível.  
  
 Use a exibição processos se desejar examinar um processo de sistema específico, que geralmente corresponde a um programa em execução. Os processos são identificados por nomes de módulo ou são designados como "processos do sistema". Para localizar um processo, recolha a árvore e pesquise na lista.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-open-the-processes-view"></a>Para abrir o modo de exibição de processos  
  
1. No menu do **Spy** , escolha **processos**.  
  
   ![Exibição de processos do Spy&#43;&#43; ](../debugger/media/spy-processes.png "Spy + + _Processes")  
   Exibição de processos do Spy + +  
  
   A figura acima mostra a exibição de processos com nós de processo e thread expandidos.  
  
### <a name="in-this-section"></a>Nesta seção  
 [Pesquisando um processo na exibição de processos](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Explica como localizar um processo específico no modo de exibição de processos.  
  
 [Exibindo Propriedades do processo](../debugger/how-to-display-process-properties.md)  
 Explica como mostrar mais informações sobre uma mensagem.  
  
### <a name="related-sections"></a>Seções relacionadas  
 [Exibições do Spy++](../debugger/spy-increment-views.md)  
 Explica as exibições de árvore do Spy + + do Windows, mensagens, processos e threads.  
  
 [Usando Spy++](../debugger/using-spy-increment.md)  
 Apresenta a ferramenta Spy + + e explica como ela pode ser usada.  
  
 [Caixa de diálogo Pesquisa de Processo](../debugger/process-search-dialog-box.md)  
 Usado para localizar o nó de um processo específico na exibição de processos.  
  
 [Caixa de diálogo Propriedades do Processo](../debugger/process-properties-dialog-box.md)  
 Exibe as propriedades de um processo selecionado na exibição processos.  
  
 [Referência de Spy++](../debugger/spy-increment-reference.md)  
 Inclui seções que descrevem cada menu e caixa de diálogo do Spy + +.
