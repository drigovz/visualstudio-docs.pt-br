---
title: 'Como: Pesquisar um processo na exibição de processos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e39168e36e9540ec8c5e23a9030d996b81c4097c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838422"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Como procurar um processo na exibição de processos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode pesquisar um processo específico na exibição de processos usando sua ID de processo ou cadeia de caracteres de módulo como critérios de pesquisa. Você também pode especificar a direção inicial da pesquisa. Os campos na caixa de diálogo mostrarão os atributos do processo selecionado na árvore de processo.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Para procurar um processo na exibição de processos  
  
1. Organize suas janelas para que o Spy + + e uma janela de [exibição de processos](../debugger/processes-view.md) ativos fiquem visíveis.  
  
2. No menu **Pesquisar** , escolha **Localizar processo**  
  
    A [caixa de diálogo pesquisa de processo](../debugger/process-search-dialog-box.md) é aberta.  
  
3. Digite a ID do processo ou uma cadeia de caracteres do módulo como critérios de pesquisa.  
  
4. Desmarque os campos para os quais você não deseja especificar valores.  
  
   > [!TIP]
   > Para localizar todos os processos pertencentes a um módulo, desmarque a caixa **processar** e digite o nome do módulo na caixa **módulo** . Em seguida, use **Localizar próximo** para continuar pesquisando processos.  
  
5. Escolha para **cima** ou para **baixo** na direção inicial da pesquisa.  
  
6. Clique em **OK**.  
  
   Se um processo de correspondência for encontrado, ele será realçado na janela de **exibição de processo** .
