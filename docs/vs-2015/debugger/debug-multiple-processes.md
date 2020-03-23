---
title: Depurar processos múltiplos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a2679825d41a6360dde05e7511d607f8be69dfa
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302549"
---
# <a name="debug-multiple-processes"></a>Depurar vários processos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veja como iniciar processos de depuração, alternar entre processos, interromper e continuar a execução, percorrer o código-fonte, interromper a depuração e terminar ou desanexar dos processos.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Conteúdo  
 [Configurar o comportamento de execução de vários processos](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Encontre os arquivos de origem e símbolo (.pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Inicie vários processos em uma solução VS, conecte-se a um processo, inicie automaticamente um processo no depurador](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Alternar processos, quebrar e continuar a execução, passo através da fonte](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Parar a depuração, finalizar ou desanexar dos processos](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Configure o comportamento de execução de múltiplos processos  
 Por padrão, quando vários processos são executados no depurador, os comandos de quebra, avanço e interrupção do depurador geralmente afetam todos os processos. Por exemplo, quando um processo é suspenso em um ponto de interrupção, a execução de todos outros processos é suspendida também. Você pode alterar esse comportamento padrão para obter mais controle sobre os destinos dos comandos de execução.  
  
1. No menu de **Depurar**, escolha **Opções e Configurações**.  
  
2. Na **página Depuração**, **Geral,** limpe todos **os processos quando um processo quebrar** a caixa de seleção.  
  
   ![De volta ao conteúdo](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superior](#BKMK_Contents)  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Localize a fonte e os arquivos de símbolo (.pdb)  
 Para navegar no código-fonte de um processo, o depurador precisa acessar os arquivos de origem e os arquivos do símbolo do processo. Consulte [Especificar símbolo (.pdb) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Se você não conseguir acessar arquivos para um processo, poderá navegar usando a janela de desmontagem. [Veja como: Usar a janela de desmontagem](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![De volta ao conteúdo](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superior](#BKMK_Contents)  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>Inicie vários processos em uma solução VS, conecte-se a um processo, inicie automaticamente um processo no depurador  
  
- [Inicie a depuração de múltiplos processos em uma solução do Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • Mude o projeto de [inicialização](#BKMK_Change_the_startup_project) • [Inicie um projeto específico em uma solução](#BKMK_Start_a_specific_project_in_a_solution) • Inicie vários projetos em uma [solução](#BKMK_Start_multiple_projects_in_a_solution) • [Conecte-se a um processo](#BKMK_Attach_to_a_process) • Inicie automaticamente um processo no [depurador](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> O depurador não é anexado automaticamente a um processo filho que é inicializado por um processo depurado, mesmo se o projeto filho estiver na mesma solução. Para depurar um processo filho:  
> 
> - Anexar ao processo filho depois que for iniciado.  
> 
>   -ou-  
>   - Configurar o Windows para iniciar automaticamente o processo filho em uma nova instância do depurador.  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Comece a depurar vários processos em uma solução do Visual Studio  
 Quando você tiver mais de um projeto em uma solução do Visual Studio que pode executar de forma independente (projetos que são executados em processos separados), será possível selecionar quais projetos o depurador inicia.  
  
 ![Alterando o tipo de inicialização para um projeto](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a>Mude o projeto de startup  
 Para alterar o projeto de inicialização de uma solução, selecione o projeto no Solution Explorer e escolha **Definir como Projeto de Inicialização** no menu de contexto.  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a>Inicie um projeto específico em uma solução  
 Para iniciar um projeto para uma solução sem alterar o projeto de inicialização padrão, selecione o projeto no Solution Explorer e escolha **Debug** no menu de contexto. Em seguida, você pode escolher **Iniciar nova instância** ou entrar em nova **instância**.  
  
 ![De volta ao topo](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inicie vários processos em uma solução VS, conecte-se a um processo, inicie automaticamente um processo no depurador](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![De volta ao conteúdo](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superior](#BKMK_Contents)  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a>Inicie vários projetos em uma solução  
  
1. Selecione a solução no Solution Explorer e escolha **Propriedades** no menu de contexto.  
  
2. Selecione **Propriedades Comuns**, **Projeto de inicialização** na caixa de diálogo **Propriedades.**  
  
3. Para cada projeto que você deseja alterar, escolha **Iniciar,** **Iniciar sem depuração**ou **Nenhum**.  
  
   ![De volta ao topo](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inicie vários processos em uma solução VS, conecte-se a um processo, inicie automaticamente um processo no depurador](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![De volta ao conteúdo](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superior](#BKMK_Contents)  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> Anexar a um processo  
 O depurador também pode *anexar* a programas que estão sendo executados em processos fora do Visual Studio, incluindo programas que estão sendo executados em um dispositivo remoto. Após vincular-se a um programa, você poderá usar comandos de execução do depurador, inspecionar o estado do programa e assim por diante. A capacidade de inspecionar o programa pode ser limitada se o programa foi criado com informações de depuração, se você tem acesso ao código-fonte do programa, e se o compilador just-in-time (JIT) do Common Language Runtime está controlando as informações de depuração.  
  
 Consulte [Anexar-se aos processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) para obter mais informações.  
  
 **Anexar a um processo que está executando em seu computador local**  
  
 Escolha **Depurar,** **Anexar ao processo**. Na caixa de diálogo Anexar ao processo, selecione o processo na lista **Processos disponíveis** e, em seguida, escolha 'Anexar '''''''''''''''''''''''''''''''''''''''''''' **Attach to Process** **Attach**  
  
 ![Anexar à caixa de diálogo Processar](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![De volta ao conteúdo](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superior](#BKMK_Contents)  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Inicie automaticamente um processo no depurador  
 Às vezes, pode ser necessário depurar o código de inicialização para um programa que foi iniciado por outro processo. Os exemplos incluem serviços e ações de configuração personalizada. Nesses cenários, você poderá fazer com que o depurador seja iniciado e automaticamente anexado quando seu aplicativo iniciar.  
  
1. Inicie o Editor de Registro **(regedit.exe).**  
  
2. Navegue até a pasta **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Image File Execution Options.**  
  
3. Selecione a pasta do aplicativo que você deseja iniciar o depurador.  
  
    Se o nome do aplicativo não estiver listado como uma pasta filho, selecione **Opções de execução de arquivo de imagem** e escolha **Nova**, **Chave** no menu de contexto. Selecione a nova tecla, escolha **Renomear** no menu de atalho e digite o nome do aplicativo.  
  
4. No menu de contexto da pasta do aplicativo, escolha **Novo**, **Valor de cadeia**.  
  
5. Alterar o nome do novo valor `debugger`de Novo **Valor** para .  
  
6. No menu de contexto da entrada de depurador, escolha **Modificar**.  
  
7. Na caixa de diálogo `vsjitdebugger.exe` Editar seqüência de diálogo, digite a **caixa de dados Valor.**  
  
    ![Editar caixa de diálogo String](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Entrada automática de início do depurador em regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![De volta ao conteúdo](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superior](#BKMK_Contents)  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Alternar processos, quebrar e continuar a execução, passo através da fonte  
  
- [Alternar entre processos](#BKMK_Switch_between_processes) • [Quebrar, passo e continuar comandos](#BKMK_Break__step__and_continue_commands)  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Alternar entre processos  
 Você pode conectar-se a vários processos quando está depurando, mas somente um processo está ativo no depurador em um determinado momento. Você pode definir o processo ativo ou *atual* na barra de ferramentas Debug Location ou na janela **Processos.** Para alternar entre processos, ambos os processos devem estar no modo de interrupção.  
  
 **Para definir o processo atual**  
  
- Na barra de ferramentas Debug Location, escolha **'Processar'** para exibir a caixa **'Processo'** lista. Selecione o processo que você deseja designar como o processo atual.  
  
   ![Alternar entre processos](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Se a barra de ferramentas **Debug Location** não estiver visível, escolha **Ferramentas**, **Personalizar**. Na guia **Barras de ferramentas,** escolha **Depuração localização**.  
  
- Abra a janela **Processos** (atalho **Ctrl+Alt+Z),** encontre o processo que deseja definir como o processo atual e clique duas vezes nele.  
  
   ![Janela de processos](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   O processo atual é marcado por uma seta amarela.  
  
  Alternar para um projeto o torna o processo atual para fins de depuração. Qualquer janela do depurador que você exibir mostrará o estado do processo atual e todos os comandos das etapas afetarão somente o processo atual.  
  
  ![De volta aos principais](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [processos do Switch, quebre e continue a execução, passo a lado da fonte](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![De volta ao conteúdo](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superior](#BKMK_Contents)  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Comandos de interromper, depurar e continuar  
  
> [!NOTE]
> Por padrão, os comandos interromper, continuar e avançar depurador afetam todos os processos que estão sendo depurados. Para alterar esse comportamento, consulte [Configurar o comportamento de execução de múltiplos processos](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Comando**|**Quebre todos os processos quando um processo se quebra**<br /><br /> Verificado (Padrão)|**Quebre todos os processos quando um processo se quebra**<br /><br /> Desmarcada|  
|**Menu de depuração:**<br /><br /> -   **Quebrar tudo**|Todos os processos são interrompidos.|Todos os processos são interrompidos.|  
|**Menu de depuração:**<br /><br /> -   **Continuar**|Todos os processos são retomados.|Todos os processos suspensos são retomados.|  
|**Menu de depuração:**<br /><br /> -   **Passo em**<br />-   **Passo mais**<br />-   **Sair**|Todos os processos estão em execução durante as etapas de processo atual.<br /><br /> Em seguida, todos os processos são interrompidos.|Etapas de processo atual.<br /><br /> Retomada de processos suspensos.<br /><br /> Executando a continuação dos processos.|  
|**Menu de depuração:**<br /><br /> -   **Passo no processo atual**<br />-   **Passo sobre o processo atual**<br />-   **Sair processo atual**|N/D|Etapas de processo atual.<br /><br /> Outros processos mantém o estado existente (suspenso ou em execução).|  
|Janela de origem<br /><br /> -   **Interrupção**|Todos os processos são interrompidos.|Somente quebras do processo da janela de origem.|  
|Menu de contexto da janela de origem:<br /><br /> -   **Corra para o cursor**<br /><br /> A janela de origem deve estar no processo atual.|Todos os processos estão em execução enquanto o processo da janela de origem executa ao cursor e depois interrompe.<br /><br /> Em seguida, todos os outros processos não interrompidos.|O processo da janela de origem é executado para o cursor.<br /><br /> Outros processos mantém o estado existente (suspenso ou em execução).|  
|Menu de contexto de janela **de processos:**<br /><br /> -   **Processo de quebra**|N/D|Quebras selecionadas do processo.<br /><br /> Outros processos mantém o estado existente (suspenso ou em execução).|  
|Menu de contexto de janela **de processos:**<br /><br /> -   **Continuar processo**|N/D|O processo selecionado é retomado.<br /><br /> Outros processos mantém o estado existente (suspenso ou em execução).|  
  
 ![De volta aos principais](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [processos do Switch, quebre e continue a execução, passo a lado da fonte](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![De volta ao conteúdo](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superior](#BKMK_Contents)  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Pare de depurar, encerrar ou separar dos processos  
  
- [Parar, finalizar e desanexar comandos](#BKMK_Stop__terminate__and_detach_commands)  
  
  Por padrão, quando você escolhe **Depurar**, **Pare de depurar** quando vários processos estão abertos no depurador, o depurador termina ou se desprende de todos os processos, dependendo de como o processo foi aberto no depurador:  
  
- Se o processo atual foi iniciado no depurador, esse processo é finalizado.  
  
- Se você já anexou o depurador ao processo atual, o depurador será desanexado do processo e o deixará em execução.  
  
  Por exemplo, se você começar a depurar um processo a partir de uma solução do Visual Studio, anexar a outro processo que já está sendo executado e, em seguida, escolher **Parar de depurar**, a sessão de depuração termina, o processo que foi iniciado no Visual Studio é encerrado, enquanto o processo que você anexou é deixado em execução. Você pode usar os seguintes procedimentos para controlar a maneira que você interrompe a depuração.  
  
> [!NOTE]
> O **Break all processes quando um processo quebra** a opção não afeta parar a depuração ou o término e a desvinculação dos processos.  
  
 **Para alterar como a depuração de parada afeta um processo individual**  
  
- Abra a janela **Processos** (atalho **Ctrl+Alt+Z**). Selecione um processo e selecione ou limpe o **Desapego quando a depuração parou** a caixa de seleção.  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a>Pare, termine e desconecte os comandos  
  
|||  
|-|-|  
|**Comando**|**Descrição**|  
|**Menu de depuração:**<br /><br /> -   **Parar de depuração**|A menos que o comportamento seja alterado pela janela **Processos** **Desconecte-se quando a opção de depuração pára:**<br /><br /> 1. Os processos iniciados pelo depurador são encerrados.<br />2. Os processos anexados são separados do depurador.|  
|**Menu de depuração:**<br /><br /> -   **Terminar tudo**|Todos os processos são encerrados.|  
|**Menu de depuração:**<br /><br /> -   **Desapegar todos**|O depurador desanexa todos os processos.|  
|Menu de contexto de janela **de processos:**<br /><br /> -   **Processo de desapego**|O depurador dispara do processo selecionado.<br /><br /> Outros processos mantém o estado existente (suspenso ou em execução).|  
|Menu de contexto de janela **de processos:**<br /><br /> -   **Processo de término**|O processo selecionado é finalizado.<br /><br /> Outros processos mantém o estado existente (suspenso ou em execução).|  
|Menu de contexto de janela **de processos:**<br /><br /> -   **Desconecte-se quando a depuração parar**|Alterna o comportamento do **Debug**, **Pare de depurar** para o processo selecionado:<br /><br /> - Verificado: O depurador se desprende do processo.<br />- Liberado: O processo está encerrado.|  
  
 ![De volta ao topo](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Pare de depurar, terminar ou separar dos processos](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![De volta ao conteúdo](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [superior](#BKMK_Contents)  
  
## <a name="see-also"></a>Consulte Também  
 [Especificar símbolo (.pdb) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Anexar aos processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Navegando através do Código com o Depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Depuração just-in-time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Depurar aplicativos multi-threaded](../debugger/debug-multithreaded-applications-in-visual-studio.md)
