---
title: Depurar vários processos | Microsoft Docs
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 160e219b6fc2ab314f8d0dd91043c18101f2c3a5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302220"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Depurar múltiplos processos (C#, Visual Basic, C++)

O Visual Studio pode depurar uma solução que tem vários processos. Você pode iniciar e alternar entre processos, quebrar, continuar e passar pela fonte, parar de depurar e finalizar ou separar de processos individuais.

## <a name="start-debugging-with-multiple-processes"></a>Inicie a depuração com vários processos

Quando mais de um projeto em uma solução do Visual Studio pode ser executado de forma independente, você pode selecionar qual projeto o depurador inicia. O projeto de inicialização atual aparece em negrito no **Solution Explorer**.

Para alterar o projeto de inicialização, no **Solution Explorer,** clique com o botão direito do mouse em um projeto diferente e selecione **Set as StartUp Project**.

Para começar a depurar um projeto do **Solution Explorer** sem torná-lo o projeto de inicialização, clique com o botão direito do mouse no projeto e selecione **Debug** > **Iniciar nova instância** ou Entrar em nova **instância**.

**Para definir o projeto de inicialização ou vários projetos a partir de propriedades de solução:**

1. Selecione a solução no **Solution Explorer** e selecione o ícone **Propriedades** na barra de ferramentas ou clique com o botão direito do mouse na solução e selecione **Propriedades**.

1. Na página **Propriedades,** selecione **Common Properties** > **Startup Project**.

   ![Alterando o tipo de inicialização para um projeto](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Selecione **Seleção Atual,** **Projeto de inicialização única** e um arquivo de projeto ou vários projetos de **inicialização**.

   Se você selecionar **Vários projetos de inicialização,** você pode alterar a ordem de inicialização e a ação a tomar para cada projeto: **Start**, **Start sem depuração,** ou **Nenhum**.

1. Selecione **Aplicar**ou **OK** para aplicar e fechar a caixa de diálogo.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> Anexar a um processo

O depurador também pode *ser anexado* a aplicativos em execução em processos fora do Visual Studio, inclusive em dispositivos remotos. Depois de anexar a um aplicativo, você pode usar o depurador visual studio. Os recursos de depuração podem ser limitados. Depende se o aplicativo foi construído com informações de depuração, se você tem acesso ao código-fonte do aplicativo e se o compilador JIT está rastreando informações de depuração.

Para obter mais informações, consulte [Anexar aos processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Para anexar a um processo em execução:**

1. Com o aplicativo em execução, selecione **Depuração** > **Anexar ao Processo**.

   ![Anexar à caixa de diálogo Processar](../debugger/media/dbg_attachtoprocessdlg.png "Caixa de diálogo Anexar ao Processo")

1. Na caixa de diálogo 'Anexar ao processo', selecione o processo na lista **'Processos disponíveis'** e selecione 'Anexar ''''''''''''''''''''''''''''''''''''''''''' **Attach to Process** **Attach**

>[!NOTE]
>O depurador não é anexado automaticamente a um processo filho que é inicializado por um processo depurado, mesmo se o projeto filho estiver na mesma solução. Para depurar um processo filho, seja anexado ao processo filho após o início ou configure o Editor de Registro do Windows para iniciar o processo filho em uma nova instância de depurador.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Use o Editor de Registro para iniciar automaticamente um processo no depurador

Às vezes, você pode precisar depurar o código de inicialização de um aplicativo que é lançado por outro processo. Os exemplos incluem serviços e ações de configuração personalizada. Você pode ter o lançamento do depurador e anexar automaticamente ao aplicativo.

1. Inicie o Editor de Registro do Windows executando *regedit.exe*.

1. No Editor de Registro, navegue até **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Opções**de execução de arquivos de imagem .

1. Selecione a pasta do aplicativo que você deseja iniciar o depurador.

   Se o aplicativo não estiver listado como uma pasta filho, clique com o botão direito do mouse Opções de **execução de arquivo**de imagem, selecione **Nova** > **chave**e digite o nome do aplicativo. Ou clique com o botão direito do mouse na nova tecla na árvore, selecione **Renomear**e digite o nome do aplicativo.

1. Clique com o botão direito do mouse na nova tecla na árvore e selecione **Novo** > **valor de cadeia**.

1. Alterar o nome do novo valor `debugger`de Novo Valor **#1** para .

1. Clique com o botão **direito do** mouse e selecione **Modificar**.

   ![Editar caixa de diálogo String](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Editar caixa de diálogo String")

1. Na caixa de diálogo `vsjitdebugger.exe` Editar **seqüência** de diálogo, digite a caixa de dados **Valor** e, em seguida, selecione **OK**.

   ![Entrada automática de início do depurador em regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "Entrada automática de início do depurador em regedit.exe")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Depurar com vários processos
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Ao depurar um aplicativo com vários processos, os comandos de quebra, revisão e depuração contínua afetam todos os processos por padrão. Por exemplo, quando um processo é suspenso em um ponto de ruptura, a execução de todos os outros processos também é suspensa. Você pode alterar esse comportamento padrão para obter mais controle sobre os destinos dos comandos de execução.

**Para alterar se todos os processos estão suspensos quando um processo se rompe:**

- Em **Ferramentas** (ou **Depuração)**>**Depuração de** >  **Opções** > **Geral,** selecione ou limpe os **processos Break all when one process breaks** sobox.

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Comandos de interromper, depurar e continuar

A tabela a seguir descreve os comportamentos dos comandos de depuração quando o **Break todos os processos quando um processo quebra** a caixa de seleção é selecionado ou desmarcado:

|**Comando**|Selecionado|Desmarcado|
|-|-|-|
|**Debug**  > **Break All**|Todos os processos são interrompidos.|Todos os processos são interrompidos.|
|**Debug** > **Continue**|Todos os processos são retomados.|Todos os processos suspensos são retomados.|
|**Depurar** > **passo para** **dentro, passo sobre**ou **sair**|Todos os processos estão em execução durante as etapas de processo atual. <br />Em seguida, todos os processos são interrompidos.|Etapas de processo atual. <br />Retomada de processos suspensos. <br />Executando a continuação dos processos.|
|**Depurar** > **o processo atual,** passar sobre o processo **atual**ou sair do **processo atual**|N/D|Etapas de processo atual.<br />Outros processos mantém o estado existente (suspenso ou em execução).|
|Ponto de ruptura da janela **de origem**|Todos os processos são interrompidos.|Somente quebras do processo da janela de origem.|
|Janela de origem **Executar para cursor**<br />A janela de origem deve estar no processo atual.|Todos os processos estão em execução enquanto o processo da janela de origem executa ao cursor e depois interrompe.<br />Em seguida, todos os outros processos não interrompidos.|O processo da janela de origem é executado para o cursor.<br />Outros processos mantém o estado existente (suspenso ou em execução).|
|**Processo** de quebra de > de janela **de processos**|N/D|Quebras selecionadas do processo.<br />Outros processos mantém o estado existente (suspenso ou em execução).|
|**Processo** de janela de processos > **continuar**|N/D|O processo selecionado é retomado.<br />Outros processos mantém o estado existente (suspenso ou em execução).|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Localize a fonte e os arquivos de símbolo (.pdb)
Para navegar pelo código fonte de um processo, o depurador precisa acessar seus arquivos de origem e arquivos de símbolos. Para obter mais informações, confira [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Se você não puder acessar os arquivos de um processo, você pode navegar usando a janela **Desmontagem.** Para obter mais informações, [consulte Como: Usar a janela Desmontagem](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Alternar entre processos

Você pode anexar a vários processos quando estiver depurando, mas apenas um processo está ativo no depurador a qualquer momento. Você pode definir o processo ativo *atual* ou na barra de ferramentas do **Localização de Depuração** ou na janela **Processos**. Para alternar entre processos, ambos os processos devem estar no modo de interrupção.

**Para definir o processo atual a partir da barra de ferramentas Debug Location:**

1. Para abrir a barra de ferramentas **Debug Location,** **selecione Exibir** > **local de depuração de****barras** > de ferramentas .

1. Durante a depuração, na barra de ferramentas **Debug Location,** selecione o processo que deseja definir como o processo atual a partir da parada **do processo.**

   ![Alternar entre processos](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Para definir o processo atual a partir da janela Processos:**

1. Para abrir a janela **Processos,** durante a depuração, selecione **Depurar** > **processos do****Windows** > .

1. Na janela **Processos,** o processo atual é marcado por uma seta amarela. Clique duas vezes no processo que deseja definir como o processo atual.

   ![Janela de processos](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Mudar para um processo define-o como o processo atual para fins de depuração. Janelas de depurador mostram o estado para o processo atual e os comandos de revisão afetam apenas o processo atual.

## <a name="stop-debugging-with-multiple-processes"></a>Pare de depurar com vários processos

Por padrão, quando você seleciona **Depuração** > **Parar de depurar,** o depurador termina ou se desprende de todos os processos.

- Se o processo atual foi iniciado no depurador, o processo será encerrado.

- Se você já anexou o depurador ao processo atual, o depurador será desanexado do processo e o deixará em execução.

Se você começar a depurar um processo a partir de uma solução do Visual Studio, então anexe a outro processo que já está sendo executado e, em seguida, escolha **Parar de depurar**, a sessão de depuração termina. O processo que foi iniciado no Visual Studio termina, enquanto o processo que você anexou continua sendo executado.

Para controlar a maneira como o **Stop Debugging** afeta um processo individual, na janela **Processos,** clique com o botão direito do mouse em um processo e, em seguida, selecione ou limpe o **Desapego quando a depuração parou** a caixa de seleção.

>[!NOTE]
>O **Break all processes when one process breaks** debugger option não afeta a interrupção, o término ou a desvinculação dos processos.

### <a name="stop-terminate-and-detach-commands"></a>Parar, finalizar e desanexar comandos

A tabela a seguir descreve os comportamentos dos comandos de depuração parar, encerrar e desvincular com vários processos:

|**Comando**|**Descrição**|
|-|-|
|**Depuração** > **Stop**|A menos que o comportamento seja alterado na janela **Processos,** os processos iniciados pelo depurador são encerrados e os processos anexados são separados.|
|**Debug** > **Terminate All**|Todos os processos estão encerrados.|
|**Depurar** > **Todos**|O depurador desanexa todos os processos.|
|**Processo** de **desapego** > janela de processos|O depurador dispara do processo selecionado.<br />Outros processos mantém o estado existente (suspenso ou em execução).|
|**Processos** de janela > **término de processo**|O processo selecionado é encerrado.<br />Outros processos mantém o estado existente (suspenso ou em execução).|
|**Processos** > de janela **desacoplquando a depuração pára**|Se selecionado, **Debug** > **Stop Debugging** se desprende do processo selecionado. <br />Se não for selecionado, **a Depuração Debug** > **Stop** termina o processo selecionado. |

## <a name="see-also"></a>Confira também

- [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Navegar pelo código com o depurador](../debugger/navigating-through-code-with-the-debugger.md)
- [Depuração just-in-time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Depurar aplicativos multithreaded](../debugger/debug-multithreaded-applications-in-visual-studio.md)