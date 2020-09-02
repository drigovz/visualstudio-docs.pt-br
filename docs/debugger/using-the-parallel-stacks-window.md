---
title: Exibir threads na janela de pilhas paralelas | Microsoft Docs
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9728346bc4c6d805bb0febd3a0d5bef0ed809a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62902247"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>Exibir threads e tarefas na janela de pilhas paralelas (C#, Visual Basic, C++)

A janela de **pilhas paralelas** é útil para depurar aplicativos multithread. Ele tem várias exibições:

- A [exibição threads](#threads-view) mostra informações de pilha de chamadas para todos os threads no aplicativo. Você pode navegar entre threads e quadros de pilha nesses threads.

- A [exibição tarefas](#tasks-view) mostra informações da pilha de chamadas centradas em tarefas.
  - Em código gerenciado, a exibição **tarefas** mostra pilhas de chamadas de <xref:System.Threading.Tasks.Task?displayProperty=fullName> objetos.
  - No código nativo, a exibição **tarefas** mostra pilhas de chamadas [de grupos de tarefas](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algoritmos paralelos](/cpp/parallel/concrt/parallel-algorithms), [agentes assíncronos](/cpp/parallel/concrt/asynchronous-agents)e [tarefas leves](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).

- A [exibição do método](#method-view) dinamiza a pilha de chamadas em um método selecionado.

## <a name="use-the-parallel-stacks-window"></a>Usar a janela Pilhas Paralelas

Para abrir a janela de **pilhas paralelas** , você deve estar em uma sessão de depuração. Selecione **depurar**  >  **Windows**  >  **pilhas paralelas**do Windows.

### <a name="toolbar-controls"></a>Controles da barra de ferramentas

A janela de **pilhas paralelas** tem os seguintes controles de barra de ferramentas:

![Barra de ferramentas na janela pilhas paralelas](../debugger/media/parallel_stackstoolbar.png "Barra de ferramentas de pilhas paralelas")

|ícone|Control|Descrição|
|-|-|-|
|![Caixa de combinação de threads e tarefas](media/parallel_toolbar1.png "Caixa de combinação de threads e tarefas")|**Threads** / Caixa de combinação **tarefas**|Alterna a exibição entre pilhas de chamadas de threads e pilhas de chamadas de tarefas. Para obter mais informações, confira [Exibição de tarefas](#tasks-view) e [Exibição de threads](#threads-view).|
|![Mostrar somente ícone sinalizado](media/parallel_toolbar2.png "Mostrar somente ícone sinalizado")|Mostrar somente sinalizados|Mostra pilhas de chamadas somente para os threads sinalizados em outras janelas do depurador, como a janela **threads de GPU** e a janela de **inspeção paralela** .|
|![Ícone de exibição do método de alternância](media/parallel_toolbar3.png "Ícone de exibição do método de alternância")|Alternar **Exibição do Método**|Alterna entre exibições de pilha de chamadas e **exibição de método**. Para obter mais informações, confira [Exibição do Método](#method-view).|
|![Rolar automaticamente para o ícone atual](media/parallel_toolbar4.png "Rolar automaticamente para o ícone atual")|Autorrolagem para Quadro de Pilha Atual|Rola o grafo para que o quadro de pilhas atual esteja na exibição. Esse recurso é útil quando você altera o quadro de pilhas atual de outras janelas ou quando você clica em um novo ponto de interrupção em gráficos grandes.|
|![Alternar ícone de zoom](media/parallel_toolbar5.png "Alternar ícone de zoom")|Ativar/Desativar Controle de Zoom|Mostra ou oculta o controle de zoom à esquerda da janela. <br /><br />Independentemente da visibilidade do controle de zoom, você também pode aplicar zoom pressionando **Ctrl** e girando a roda do mouse, ou pressionando **Ctrl** + **Shift** + **+** para ampliar e **Ctrl** + **Shift** + **-** para reduzir. |

### <a name="stack-frame-icons"></a>Ícones de quadros de pilhas
Os ícones a seguir fornecem informações sobre os quadros de pilhas ativo e atual em todas as exibições:

|ícone|Descrição|
|-|-|
|![Seta amarela](media/icon_parallelyellowarrow.gif)|Indica o local atual (quadro de ativação ativo) do thread atual.|
|![Ícone de threads](media/icon_parallelthreads.gif)|Indica o local atual (quadro de ativação ativo) de um thread não atual.|
|![Seta Verde](media/icon_parallelgreenarrow.gif)|Indica o quadro de pilhas atual (o contexto do depurador atual). O nome do método é negrito onde for exibido.|

### <a name="context-menu-items"></a>Itens de menu de contexto
Os itens de menu de atalho a seguir estão disponíveis quando você clica com o botão direito do mouse em um método no modo de exibição **threads** ou **tarefas** . Os últimos seis itens são os mesmos da [janela pilha de chamadas](how-to-use-the-call-stack-window.md).

![Menu de atalho na janela pilhas paralelas](../debugger/media/parallel_contmenu.png "Menu de atalho na janela pilhas paralelas")

|Item de menu|Descrição|
|-|-|
|**Identificar**|Sinaliza o item selecionado.|
|**Remover Sinalização**|Remove a sinalização do item selecionado.|
|**Congelamento**|Congela o item selecionado.|
|**Congelar**|Descongela o item selecionado.|
|**Alternar para Quadro**|O mesmo que o comando de menu correspondente na janela **pilha de chamadas** . No entanto, na janela **pilhas paralelas** , um método pode estar em vários quadros. Você pode selecionar o quadro desejado no submenu para este item. Se um dos quadros de pilha estiver no thread atual, esse quadro será selecionado por padrão no submenu.|
|**Ir para a tarefa** ou **ir para o thread**|Alterna para a exibição de **tarefa** ou **threads** e mantém o mesmo quadro de pilha realçado.|
|**Ir para Código Fonte**|Vai para o local correspondente na janela de código-fonte. |
|**Ir para Desmontagem**|Vai para o local correspondente na janela de **desmontagem** .|
|**Mostrar Código Externo**|Mostra ou oculta o código externo.|
|**Exibição Hexadecimal**|Alterna entre a exibição decimal e hexadecimal.|
|**Mostrar Threads na Origem**|Sinaliza o local do thread na janela de código-fonte. |
|**Informações de Carregamento de Símbolos**|Abre a caixa de diálogo **informações de carregamento de símbolo** .|
|**Configurações de Símbolo**|Abre a caixa de diálogo **configurações de símbolo** . |

## <a name="threads-view"></a>exibição Threads

No modo de exibição **threads** , o quadro de pilha e o caminho de chamada do thread atual são realçados em azul. O local atual do thread é mostrado pela seta amarela.

Para alterar o registro de ativação atual, clique duas vezes em um método diferente. Isso também pode mudar o thread atual, dependendo se o método selecionado faz parte do thread atual ou de outro thread.

Quando o grafo de exibição de **threads** é muito grande para se ajustar à janela, o controle de **exibição olho de pássaro** aparece na janela. Você pode mover o quadro no controle para navegar para diferentes partes do grafo.

A ilustração a seguir mostra um thread que passa do principal para uma transição de código de gerenciado para nativo. Seis threads estão no método atual. Um continua a thread. Sleep e outro continua a console. WriteLine e, em seguida, para SyncTextWriter. WriteLine.

 ![Exibição de threads na janela de pilhas paralelas](../debugger/media/parallel_stack1.png "Exibição de threads na janela de pilhas paralelas")

A tabela a seguir descreve os principais recursos do modo de exibição **threads** :

|Balão|Nome do elemento|Descrição|
|-|-|-|
|1|Segmento ou nó da pilha de chamadas|Contém uma série de métodos para um ou mais threads. Se o quadro não tiver linhas de Seta conectadas a ele, o quadro mostrará o caminho de chamada inteiro para os threads.|
|2|Realce azul|Indica o caminho da chamada do thread atual.|
|3|Linhas de seta|Conecte os nós para compor o caminho inteiro de chamada para os threads.|
|4|Cabeçalho do nó|Mostra o número de processos e threads para o nó.|
|5|Método|Representa uma ou mais quadros de pilha no mesmo método.|
|6|Dica de ferramenta no método|Aparece quando você passa o mouse sobre um método. Na exibição **threads** , a dica de ferramenta mostra todos os threads, em uma tabela semelhante à janela **threads** . |

## <a name="tasks-view"></a>Exibição de tarefas
Se seu aplicativo usa <xref:System.Threading.Tasks.Task?displayProperty=fullName> objetos (código gerenciado) ou `task_handle` objetos (código nativo) para expressar o paralelismo, você pode usar o modo de exibição **tarefas** . A exibição de **Tarefas** mostra as pilhas de chamadas de tarefas reais em vez de threads.

No modo de exibição **tarefas** :

- As pilhas de chamadas de threads que não estão executando tarefas não são mostradas.
- As pilhas de chamadas de threads que estão executando tarefas são visualmente cortadas na parte superior e inferior, para mostrar os quadros mais relevantes para as tarefas.
- Quando várias tarefas estão em um thread, as pilhas de chamadas dessas tarefas são mostradas em nós separados.

Para ver uma pilha de chamadas inteira, alterne de volta para a exibição **threads** clicando com o botão direito do mouse em um quadro de pilha e selecionando **ir para thread**.

A ilustração a seguir mostra a exibição **threads** na parte superior e a exibição **tarefas** correspondentes na parte inferior.

![Exibições de threads e tarefas](../debugger/media/parallel_threads-tasks.png "Exibições de threads e tarefas")

Focalize um método para mostrar uma dica de ferramenta com informações adicionais. No modo de exibição **tarefas** , a dica de ferramenta mostra todas as tarefas em uma tabela semelhante à janela **tarefas** .

A imagem a seguir mostra a dica de ferramenta para um método na exibição **threads** na parte superior e para a exibição **tarefas** correspondentes na parte inferior.

![Dicas de ferramentas de threads e tarefas](../debugger/media/parallel_threads-tasks-tooltips.png "Dicas de ferramentas de threads e tarefas")

## <a name="method-view"></a>Modo de Exibição do Método
Do modo de exibição de **threads** ou de **tarefas** , você pode dinamizar o grafo no método atual selecionando o ícone de **exibição de método de alternância** na barra de ferramentas. A **Exibição do Método** mostra rapidamente todos os métodos em todos os threads que chamam ou são chamados pelo método atual. A ilustração a seguir mostra como as mesmas informações são exibidas no modo de exibição **threads** à esquerda e no **modo de exibição de método** à direita.

![Exibição de threads e exibição de método](../debugger/media/parallel_methodview.png "Exibição de threads e exibição de método")

Se você alternar para um novo registro de ativação, fará com que esse método o método atual e o **modo de exibição de método** mostre todos os chamadores e chamadas para o novo método. Isso pode fazer os threads serem exibidos ou desaparecerem da exibição, dependendo se esse método for exibido em suas pilhas de chamadas. Para retornar à exibição da pilha de chamadas, selecione o ícone **Exibir método** da barra de ferramentas novamente.

## <a name="see-also"></a>Confira também
- [Introdução à depuração de um aplicativo multithread](../debugger/get-started-debugging-multithreaded-apps.md)
- [Passo a passo: depurar um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Introdução ao depurador](../debugger/debugger-feature-tour.md)
- [Depuração de código gerenciado](../debugger/debugging-managed-code.md)
- [Programação paralela](/dotnet/standard/parallel-programming/index)
- [Usar a janela Tarefas](../debugger/using-the-tasks-window.md)
- [Classe de tarefa](../extensibility/debugger/task-class-internal-members.md)
