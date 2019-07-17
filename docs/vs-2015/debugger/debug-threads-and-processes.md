---
title: Depurar Threads e processos | Microsoft Docs
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
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df9bc7cdb185edd27d7572c1436db442514d38e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202560"
---
# <a name="debug-threads-and-processes"></a>Depurar threads e processos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Threads * e *processos* são conceitos relacionados em ciência da computação. Ambos representam sequências de instruções que devem executar em uma ordem específica. Instruções em threads ou processos separados, entretanto, podem ser executados em paralelo.  
  
 Os processos existem no sistema operacional e correspondem ao que os usuários veem como programas ou aplicativos. Um thread, por outro lado, existe dentro de um processo. Por esse motivo, os threads são às vezes chamados de *processos leves*. Cada processo consiste em um ou mais threads.  
  
 A existência de vários processos permite que um computador execute mais de uma tarefa de cada vez. A existência de vários threads permite que um processo separe o trabalho a ser executado paralelamente. Em um computador com multiprocessadores, os processos ou threads podem ser executados em processadores diferentes. Isso permite o verdadeiro processamento paralelo.  
  
 O processamento paralelo perfeito não é sempre possível. Às vezes os threads devem ser sincronizados. Um thread pode ter que aguardar um resultado de outro thread, ou um thread pode precisar de acesso exclusivo a um recurso que outro thread está usando. Problemas de sincronização são uma causa comum de erro em aplicativos com multithreads. Em alguns casos, os threads podem interromper espera de um recurso que nunca fica disponível. Isso resulta em uma condição chamada *deadlock*.  
  
 O depurador do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornece ferramentas avançadas e mas fáceis de usar para depurar threads e processos.  
  
## <a name="tools-for-debugging-threads-and-processes-in-visual-studio"></a>Ferramentas para depurar threads e processos no Visual Studio  
 As principais ferramentas para trabalhar com processos no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] são os **anexar ao processo** caixa de diálogo, o **processos** janela e o **local de depuração** barra de ferramentas. As ferramentas principais para depurar threads são a **Threads** janela, marcadores de thread em janelas de origem e o **local de depuração** barra de ferramentas.  
  
 As ferramentas principais para depurar aplicativos multissegmentados são as **pilhas paralelas** e **tarefas paralelas**, **inspeção paralela**, e **ThreadsdaGPU** windows.  
  
 A tabela a seguir mostra as informações disponíveis e as ações que você pode executar em cada um desses locais:  
  
|Interface do Usuário|Informação disponível|Ações que você pode executar|  
|--------------------|---------------------------|-----------------------------|  
|Caixa de diálogo **Anexar ao Processo**|Processos disponíveis você pode anexar:<br /><br /> – Nome do Processo (.exe)<br />– Número de identificação do processo<br />– Título da barra de menus<br />– Tipo (v4.0 gerenciado; v2.0 gerenciado, v1.1, v1.0; x86; x64; IA64)<br />– Nome de usuário (nome de conta)<br />– Número da sessão|Selecione um processo anexar.<br /><br /> Selecione um computador remoto<br /><br /> Altere o tipo de transporte para se conectar a computadores remotos|  
|Janela **Processos**|Processos anexados:<br /><br /> – Nome do processo<br />– Número de identificação do processo<br />– Caminho para o .exe do processo<br />– Título da barra de menus<br />– Estado (interrupção. em execução)<br />– Depurando (nativo, gerenciado, etc.)<br />– Tipo de transporte (padrão, nativo sem autenticação)<br />– Qualificador de transporte (computador remoto)|Ferramentas:<br /><br /> – Anexar<br />– Desanexar<br />– Encerrar<br /><br /> O menu de atalho:<br /><br /> – Anexar<br />– Desanexar<br />– Desanexar quando a depuração for interrompida<br />– Encerrar|  
|Janela **Threads**|Threads durante o processo atual:<br /><br /> – ID de thread<br />– ID gerenciada<br />– Categoria (thread principal, thread de interface, manipulador de chamada de procedimento remoto ou thread de trabalho)<br />– Nome do thread<br />– Localização em que o thread é criado<br />– Prioridade<br />– Máscara de afinidade<br />– Contagem suspensa<br />– Nome do processo<br />– Indicador de Sinalização<br />– Indexador suspenso|Ferramentas:<br /><br /> – Pesquisar<br />– Pesquisar pilha de chamadas<br />– Sinalizar Apenas Meu Código<br />– Sinalizar seleção de módulo personalizada<br />– Agrupar por<br />– Colunas<br />– Expandir/recolher pilhas de chamadas<br />– Expandir/recolher grupos<br />– Congelar/descongelar threads<br /><br /> O menu de atalho:<br /><br /> – Mostrar threads na origem<br />– Alternar para um thread<br />– Congelar um thread em execução<br />– Descongelar um thread congelado<br />– Sinalizar um thread para estudos adicionais<br />– Remover a sinalização de um thread<br />– Renomear um thread<br />– Exibir e ocultar threads<br /><br /> Outras ações:<br /><br /> – Exibir a pilha de chamadas para um thread em um DataTip|  
|Janela de origem|Indexadores de threads na medianiz esquerda indicam um ou vários segmentos (desativado por padrão, ativado usando o menu de atalho na janela **Threads**)|O menu de atalho:<br /><br /> – Alternar para um thread<br />– Sinalizar um thread para estudos adicionais<br />– Remover a sinalização de um thread|  
|Barra de ferramentas **Localização de Depuração**|– Processo atual<br />– Suspender o aplicativo<br />– Retomar o aplicativo<br />– Suspender e encerrar o aplicativo<br />– Thread atual<br />– Alternar o estado do sinalizador do thread atual<br />– Mostrar somente threads sinalizados<br />– Mostrar somente o processo atual<br />– Registro de ativação atual|– Alternar para outro processo<br />– Suspender, retomar ou encerrar o aplicativo<br />– Alternar para outro thread no processo atual<br />– Alternar para outro registro de ativação no thread atual<br />– Sinalizar ou remover sinalização de threads atuais<br />– Mostrar somente threads sinalizados<br />– Mostrar somente o processo atual|  
|Janela **Pilhas Paralelas**|– Pilhas de chamadas para vários threads em uma janela.<br />– Registro de ativação ativo para cada thread.<br />– Chamadores e receptores de qualquer método.|– Remover threads especificados<br />-Alternar para modo de exibição de tarefas paralelas<br />– Sinalizar ou remover sinalização de um thread<br />– Zoom|  
|**Tarefas paralelas** janela|– Exibir informações sobre os objetos de <xref:System.Threading.Tasks.Task>, incluindo ID de tarefa, status de tarefa (agendada, executando, em espera, em deadlock), bem como qual thread está atribuído à tarefa.<br />– Localização atual na pilha de chamadas.<br />– O delegado passado para a tarefa no horário de criação|– Alternar para a tarefa atual<br />– Sinalizar ou remover sinalização de uma tarefa<br />– Congelar ou descongelar uma tarefa|  
|Janela **Inspeção Paralela**|– A coluna do sinalizador, na qual você pode marcar um thread ao qual deseja prestar atenção especial.<br />– A coluna do quadro, na qual uma seta indica o quadro selecionado.<br />– Uma coluna configurável que pode exibir o computador, o processo, o bloco, a tarefa e o thread.|– Sinalizar ou remover sinalização de um thread<br />– Exibir somente threads sinalizados<br />– Quadros de opção<br />– Classificar uma coluna<br />– Agrupar threads<br />– Congelar ou descongelar threads<br />– Exportar os dados na janela Inspeção Paralela|  
|Janela **Threads de GPU**|– A coluna do sinalizador, na qual você pode marcar um thread ao qual deseja prestar atenção especial.<br />-A coluna thread ativo, em que uma seta amarela indica um thread ativo. Uma seta indica um thread onde a execução interrompe no depurador.<br />– A coluna **Contagem de Threads**, que exibe o número de threads na mesma localização.<br />– A coluna **Linha**, que exibe a linha de código na qual cada grupo de threads está localizado.<br />– A coluna de **Endereço**, que exibe o endereço da instrução no qual cada grupo de threads está localizado.<br />– A coluna **Localização**, que é a localização no código do endereço.<br />– A coluna **Status**, que mostra se o thread está ativo ou bloqueado.<br />– A coluna **Lado a lado**, que mostra o índice lado a lado para os threads na linha.|-Alterar para um thread ativo diferente<br />– Exibir um determinado bloco e thread<br />– Exibir ou ocultar uma coluna<br />– Classificar por coluna<br />– Agrupar threads<br />– Congelar ou descongelar threads<br />– Sinalizar ou remover sinalização de um thread<br />– Exibir somente threads sinalizados|  
  
## <a name="see-also"></a>Consulte também  
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Depurar aplicativos multi-threaded](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depurando código de GPU](../debugger/debugging-gpu-code.md)
