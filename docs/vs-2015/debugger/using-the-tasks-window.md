---
title: Usando a janela tarefas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 267a04e0d717bde311423aae7f35fba07ca6f39b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684032"
---
# <a name="using-the-tasks-window"></a>Usando a janela Tarefas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A janela **Tarefas** é semelhante à janela **Threads**, exceto que mostra informações sobre os objetos <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) ou [WinJS.Promise](https://msdn.microsoft.com/library/windows/apps/br211867.aspx) em vez de cada thread. Como threads, as tarefas representam as operações assíncronas que podem ser executadas simultaneamente; no entanto, várias tarefas podem ser executadas no mesmo thread. Consulte [programação assíncrona em JavaScript (aplicativos da Windows Store)](https://msdn.microsoft.com/library/windows/apps/hh700330.aspx) para obter mais informações.  
  
 No código gerenciado, você pode usar a janela **Tarefas** quando trabalha com objetos <xref:System.Threading.Tasks.Task?displayProperty=fullName> ou com as palavras-chave **await** e **async** (**Await** e **Async** no Visual Basic). Para obter mais informações sobre tarefas em código gerenciado, consulte  [programação paralela](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d).  
  
 No código nativo, você pode usar a janela **Tarefas** quando trabalha com [grupos de tarefas](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [algoritmos paralelos](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [agentes assíncronas](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a) e [tarefas leves](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90). Para obter mais informações sobre tarefas em código nativo, consulte [tempo de execução de simultaneidade](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c).  
  
 No JavaScript, você pode usar a janela Tarefas quando estiver trabalhando com a tarefa e, em seguida, codificar.  
  
 Você pode usar a janela **Tarefas** sempre que quebrar no depurador. Você poderá acessá-la clicando no menu **Depurar**, **Janelas** e **Tarefas**. A ilustração a seguir mostra a janela **Tarefas** no modo padrão.  
  
 ![Janela tarefas paralelas](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
> No código gerenciado, um <xref:System.Threading.Tasks.Task> que tem um status de <xref:System.Threading.Tasks.TaskStatus>, <xref:System.Threading.Tasks.TaskStatus> ou <xref:System.Threading.Tasks.TaskStatus> podem não ser exibidos na janela das tarefas quando os threads gerenciados estão em um estado de suspensão ou junção.  
  
## <a name="tasks-column-information"></a>Informações da coluna de tarefas  
 As colunas na janela **Tarefas** mostram as informações a seguir.  
  
|Nome da coluna|Descrição|  
|-----------------|-----------------|  
|**Sinalizadores**|Mostra quais tarefas estão sinalizadas e permite sinalizar ou remover a sinalização de uma tarefa.|  
|**Ícones**|Uma seta amarela indica a tarefa atual. A tarefa atual é a tarefa mais alta no thread atual.<br /><br /> Uma seta branca indica a tarefa de quebra, isto é, a que era atual quando o depurador foi chamado.<br /><br /> O ícone de pausa indica uma tarefa que foi congelada pelo usuário. Você pode congelar e descongelar uma tarefa clicando com o botão direito na lista.|  
|**ID**|Um número fornecido pelo sistema para a tarefa. No código nativo, esse é o endereço da tarefa.|  
|**Status**|O estado atual (agendado, ativo, com deadlock, aguardando ou concluído) da tarefa. Uma tarefa agendada é aquela que ainda não foi executada e, portanto, ainda não tem uma pilha de chamadas, um thread alocado ou as informações relacionadas.<br /><br /> Uma tarefa ativa é aquela que estava executando o código antes de quebrar no depurador.<br /><br /> Uma tarefa de espera é bloqueada porque está esperando um evento ser sinalizado, um bloqueio ser liberado ou outra tarefa ser concluída.<br /><br /> Uma tarefa com deadlock é uma tarefa de espera cujo thread está bloqueado com outro thread.<br /><br /> Passe o mouse sobre a célula de **status** de uma tarefa de deadlock ou de espera para ver mais informações sobre o bloco. **AVISO:**  A janela **tarefas** relata o deadlock somente para uma tarefa bloqueada que usa um primitivo de sincronização que é suportado pela WCT (Wait Chain Traversal). Por exemplo, para um objeto Deadlocked <xref:System.Threading.Tasks.Task> , que usa a WCT, o depurador relata **aguardando o deadlock**. Para uma tarefa com deadlock que é gerenciada pelo Runtime de Simultaneidade, que não usa WCT, o depurador informa **Aguardando**. Para saber mais sobre o WCT, consulte [Passagem de cadeia de espera](https://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Start Time**|A hora em que a tarefa se tornou ativa.|  
|**Duration**|O número de segundos que a tarefa esteve ativa.|  
|**Tempo de Conclusão**|A hora e conclusão da tarefa.|  
|**Localidade**|O local atual da pilha de chamadas da tarefa. Passe o mouse sobre esta célula para ver a pilha de chamada inteira para a tarefa. As tarefas agendadas não têm um valor nessa coluna.|  
|**Tarefa**|O método inicial e quaisquer argumentos que são passados para a tarefa quando ela foi criada.|  
|**Pai**|A ID da tarefa que criou essa tarefa. Se estiver em branco, a tarefa não terá pai. Isso é aplicável somente para programas gerenciados.|  
|**Atribuição de thread**|O nome e a ID do thread no qual a tarefa está em execução.|  
|**Status de retorno**|O status da tarefa quando foi concluída. Os valores de status de retorno são **Success**, **Canceled**e **Error**.|  
|**Descarregar**|Para código gerenciado, o domínio de aplicativo no qual a tarefa está em execução.|  
|**task_group**|Para o código nativo, o endereço do objeto [task_group](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) que agendou a tarefa. Para agentes assíncronos e tarefas leves, essa coluna é definida como 0.|  
|Processo|A ID do processo no qual a tarefa está em execução.|  
|Estado assíncrono|Para código gerenciado, o status da tarefa. Por padrão, essa coluna está ocultada. Para exibir esta coluna, abra o menu de contexto para um dos cabeçalhos de coluna. Escolha **Colunas**, **AsyncState**.|  
  
 Você pode adicionar colunas à exibição clicando com o botão direito em um cabeçalho de coluna e selecionando as colunas desejadas. (Remova as colunas desmarcando as seleções.) Você também pode reordenar colunas arrastando-as para a esquerda ou direita. O menu de atalho da coluna é mostrado na ilustração a seguir.  
  
 ![Menu de exibição de atalho na janela tarefas paralelas](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Tarefas de classificação  
 Para classificar as tarefas por critérios da coluna, clique no cabeçalho da coluna. Por exemplo, ao clicar no cabeçalho da coluna **ID** , você pode classificar as tarefas por ID da tarefa: 1, 2, 3, 4, 5 e assim por diante. Para inverter a ordem de classificação, clique no cabeçalho da coluna novamente. A coluna e a ordem de classificação atuais estão indicadas por uma seta na coluna.  
  
## <a name="grouping-tasks"></a>Agrupando tarefas  
 Você pode agrupar tarefas com base em qualquer coluna na exibição de lista. Por exemplo, clicando com o botão direito do mouse no cabeçalho da coluna **status** e clicando em **Agrupar por status**, você pode agrupar todas as tarefas que têm o mesmo status. Por exemplo, você pode visualizar rapidamente as tarefas em espera para que poder se concentrar em por que estão bloqueadas. Você também pode recolher um grupo que não é de interesse durante a sessão de depuração. Da mesma forma, você pode agrupar por outras colunas. Um grupo pode ser sinalizado ou ter a sinalização removida apenas clicando no botão ao lado do cabeçalho do grupo. A ilustração a seguir mostra a janela **Tarefas** no modo agrupado.  
  
 ![Modo agrupado na janela tarefas paralelas](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Exibição de pai-filho  
 (Essa exibição está disponível somente para código gerenciado.) Ao clicar com o botão direito do mouse em um título de coluna e clicar em **exibição pai filho**, você pode alterar a lista de tarefas para uma exibição hierárquica, na qual cada tarefa filho é um subnó que pode ser exibido ou oculto sob seu pai. A ilustração a seguir mostra as tarefas na exibição de pai-filho.  
  
 ![Exibição filho de&#45;pai na janela tarefas paralelas](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>Tarefas de sinalização  
 Você pode sinalizar o thread na tarefa em que uma tarefa está sendo executada selecionando o item da lista de tarefas e escolhendo **sinalizador** no menu de contexto ou clicando no ícone de sinalizador na primeira coluna. Se você sinalizar várias tarefas, poderá classificar na coluna do sinalizador para levar todas as tarefas sinalizadas para o alto para que você possa se concentrar apenas nelas. Você também pode usar a janela **Pilhas Paralelas** para exibir apenas tarefas sinalizadas. Isso permite filtrar tarefas nas quais você não está interessado para depuração. Os sinalizadores não são mantidos entre sessões de depuração.  
  
## <a name="freezing-and-thawing-tasks"></a>Congelando e descongelando tarefas  
 Você pode congelar o thread no qual uma tarefa está sendo executada clicando com botão direito no item da lista de tarefas e clicando em **Congelar Thread Atribuído**. (Se uma tarefa já estiver congelada, o comando **descongelar thread atribuído**.) Quando você congela um thread, esse thread não será executado quando você percorrer o código após o ponto de interrupção atual. A **congelamento de todos os threads, mas este** comando congela todos os threads, exceto aquele que está executando o item da lista de tarefas.  
  
 A ilustração a seguir mostra os outros itens de menu para cada tarefa.  
  
 ![Menu de thread de atalho na janela tarefas paralelas](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>Consulte Também  
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Depuração de código gerenciado](../debugger/debugging-managed-code.md)   
 [Programação paralela](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Tempo de Execução de Simultaneidade](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Usando a janela pilhas paralelas](../debugger/using-the-parallel-stacks-window.md)   
 [Instruções passo a passo: depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md)
