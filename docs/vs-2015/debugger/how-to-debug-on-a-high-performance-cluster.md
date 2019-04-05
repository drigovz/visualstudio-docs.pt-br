---
title: 'Como: Depurar em um Cluster de alto desempenho | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a283cfd34d0990a59bc5d8ce1109f2c0ae6b38bc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58929483"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Como: Depurar em um cluster de alto desempenho
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A depuração de um programa com vários processamentos em um cluster de alto desempenho é semelhante à depuração de um programa comum em um computador remoto. No entanto, há algumas considerações adicionais. Para requisitos gerais de configuração remota, consulte [depuração remota](../debugger/remote-debugging.md).  
  
 Ao depurar em um cluster de alto desempenho, você pode usar todas as janelas e técnicas de depuração do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que estiverem disponíveis para a depuração remota. Como você está depurando remotamente, no entanto, a janela do console externo não está disponível.  
  
 A janela **Threads** e a janela **Processos** são úteis especificamente para depurar aplicativos paralelos. Para obter dicas sobre como usar essas janelas, consulte [como: Use a janela de processos](http://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) e [como: Usar a janela Threads](../debugger/how-to-use-the-threads-window.md).  
  
 Os procedimentos a seguir mostram algumas técnicas que são muito úteis para depurar em um conjunto de alto desempenho.  
  
 Ao depurar um aplicativo paralelo, convém definir um ponto de interrupção em um segmento, processo, ou em um computador específico. Você pode fazer isso criando um ponto de interrupção normal, e depois adicionando um filtro de ponto de interrupção.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Para abrir a caixa de diálogo Filtro de Ponto de Interrupção  
  
1.  Clique com o botão direito do mouse em um glifo de ponto de interrupção em uma janela de origem, na janela de **Desmontagem**, na janela de **Pilha de Chamadas** ou na janela de **Pontos de Interrupção**.  
  
2.  No menu de atalho, clique em **Filtrar**. Essa opção pode aparecer no nível superior ou no submenu em **Pontos de Interrupção**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Para definir um ponto de interrupção em um computador específico  
  
1.  Obter o nome do computador na janela **Processos**.  
  
2.  Selecione um ponto de interrupção e abra a caixa de diálogo **Filtro de Ponto de Interrupção** como descrito no procedimento anterior.  
  
3.  Na caixa de diálogo **Filtro de Ponto de Interrupção**, digite:  
  
     MachineName =*nomedoseucomputador*  
  
     Para criar um filtro mais complexo, você pode combinar cláusulas usando `&`, o operador AND, `||`, o operador OR, `!`, o operador NOT, e parênteses.  
  
4.  Clique em **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Para definir um ponto de interrupção em um processo específico  
  
1.  Obter o nome do processo ou o número da ID do processo na janela **Processos**.  
  
2.  Selecione um ponto de interrupção e abra a caixa de diálogo **Filtro de Ponto de Interrupção** como no primeiro procedimento.  
  
3.  Na caixa de diálogo **Filtro de Ponto de Interrupção**, digite:  
  
     `ProcessName =` *nomedoseuprocesso*  
  
     —ou—  
  
     `ProcessID =` *númerodaIDdoseuprocesso*  
  
     Para criar um filtro mais complexo, você pode combinar cláusulas usando `&`, o operador AND, `||`, o operador OR, `!`, o operador NOT, e parênteses.  
  
4.  Clique em **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Para definir um ponto de interrupção em um segmento específico  
  
1.  Obter o nome do thread ou o número da ID do thread na janela **Threads**.  
  
2.  Selecione um ponto de interrupção e abra a caixa de diálogo **Filtro de Ponto de Interrupção** como descrito no primeiro procedimento.  
  
3.  Na caixa de diálogo **Filtro de Ponto de Interrupção**, digite:  
  
     `ThreadName =` *nomedothread*  
  
     —ou—  
  
     `ThreadID =` *númerodaIDdothread*  
  
     Para criar um filtro mais complexo, você pode combinar cláusulas usando `&`, o operador AND, `||`, o operador OR, `!`, o operador NOT, e parênteses.  
  
4.  Clique em **OK**.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar um filtro para um ponto de interrupção em um computador chamado `marvin` e um thread chamado `fourier1`.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multi-threaded](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depuração remota](../debugger/remote-debugging.md)   
 [Como: Use a janela processos](http://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Como: Usar a janela Threads](../debugger/how-to-use-the-threads-window.md)   
 [Threads e processos](http://msdn.microsoft.com/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Usando pontos de interrupção](../debugger/using-breakpoints.md)
