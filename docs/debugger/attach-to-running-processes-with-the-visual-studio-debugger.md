---
title: Anexar aos processos em execução com o depurador | Microsoft Docs
ms.custom: seodec18
ms.date: 04/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5305be7615e426d7792d8dd3fefb2579e2ab6be
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233021"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Anexar a processos em execução com o depurador do Visual Studio
Você pode anexar o depurador do Visual Studio a um processo de execução em um computador local ou remoto. Após a execução do processo, selecione **Depurar** > **Anexar ao processo** ou pressione **Ctrl**+**Alt**+**P** no Visual Studio e use a caixa de diálogo Anexar ao **processo** para anexar o depurador ao processo.

Você pode usar **o Attach to Process para** depurar aplicativos em computadores locais ou remotos, depurar vários processos simultaneamente, depurar aplicativos que não foram criados no Visual Studio ou depurar qualquer aplicativo que você não tenha começado no Visual Studio com o depurador conectado. Por exemplo, se você estiver executando um aplicativo sem o depurador e bater em uma exceção, você pode anexar o depurador ao processo que executa o aplicativo e começar a depurar.

> [!TIP]
> Não tem certeza se deve usar **o Attach to Process** para o seu cenário de depuração? Veja [cenários comuns de depuração](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a>Conecte-se a um processo de execução em sua máquina local

Para reconectar rapidamente a um processo ao qual você anexou anteriormente, consulte [Reanexar a um processo](#BKMK_reattach).

Para depurar um processo em um computador remoto, consulte [Anexar a um processo em um computador remoto](#BKMK_Attach_to_a_process_on_a_remote_computer).

::: moniker range=">= vs-2019"
Para depurar um processo .NET Core em um contêiner Linux Docker, consulte [Anexar a um contêiner Linux Docker](#BKMK_Linux_Docker_Attach).
::: moniker-end

**Para anexar a um processo em seu computador local:**

1. No Visual Studio, selecione **Debug** > **Attach to Process** (ou **pressione Ctrl**+**Alt**+**P**) para abrir a caixa de diálogo **'Anexar ao processo'.**

   **O tipo de conexão** deve ser definido **como Padrão**. **O alvo de conexão** deve ser o nome da máquina local.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. Na lista **de processos disponíveis,** encontre e selecione o processo ou processos a que deseja anexar.

   - Para selecionar rapidamente um processo, digite seu nome ou primeira letra na caixa **Processos Filter.**

   - Se você não sabe o nome do processo, navegue pela lista ou veja [cenários comuns de depuração](#BKMK_Scenarios) para alguns nomes de processo comuns.

   >[!TIP]
   >Os processos podem iniciar e parar em segundo plano enquanto a caixa de diálogo **Anexar ao processo** estiver aberta, de modo que a lista de processos em execução pode nem sempre estar atual. Você pode selecionar **Atualizar** a qualquer momento para ver a lista atual.

3. No **campo Anexar ao** campo, certifique-se de que o tipo de código que você planeja depurar está listado. A configuração **automática** padrão funciona para a maioria dos tipos de aplicativos.

   Para selecionar os tipos de código manualmente:
   1. Clique em **Selecionar**.
   1. Na **caixa de** diálogo Selecionar tipo de código, selecione **Depurar esses tipos de código**.
   1. Selecione os tipos de código que deseja depurar.
   1. Selecione **OK**.

4. Selecionar **Anexar**.

>[!NOTE]
>Você pode ser anexado a vários aplicativos para depuração, mas apenas um aplicativo está ativo no depurador de cada vez. Você pode definir o aplicativo ativo na barra de ferramentas visual studio **debug location** ou **processes.**

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Anexar a um processo em um computador remoto

Você também pode selecionar um computador remoto na caixa de diálogo **Anexar ao processo,** visualizar uma lista de processos disponíveis em execução nesse computador e anexar a um ou mais dos processos para depuração. O depurador remoto *(msvsmon.exe)* deve estar em execução no computador remoto. Para obter mais informações, consulte [Depuração remota](../debugger/remote-debugging.md).

Para obter instruções mais completas para depurar ASP.NET aplicativos que foram implantados no IIS, consulte [depuração remota ASP.NET em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Para anexar a um processo em execução em um computador remoto:**

1. No Visual Studio, selecione **Debug** > **Attach to Process** (ou **pressione Ctrl**+**Alt**+**P**) para abrir a caixa de diálogo **'Anexar ao processo'.**

2. **O tipo de conexão** deve ser **padrão** para a maioria dos casos. Na caixa **de destino Conexão,** selecione o computador remoto, usando um dos seguintes métodos:

   - Selecione a seta baixa ao lado **do destino Conexão**e selecione o nome do computador na lista de paradas.
   - Digite o nome do computador na caixa **de destino Conexão** e **pressione Enter**.

     Verifique se o Visual Studio adiciona a porta necessária ao nome do computador, que aparece no formato: ** \<nome do computador remoto>:port**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Se você não puder se conectar usando o nome do computador remoto, tente usar o endereço IP e porta (por exemplo, `123.45.678.9:4022`). 4024 é a porta padrão para o depurador remoto Visual Studio 2019 x64. Para outras atribuições remotas da porta de depurador, consulte [Atribuições de porta de depurador remotas](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Se você não puder se conectar usando o nome do computador remoto, tente usar o endereço IP e porta (por exemplo, `123.45.678.9:4022`). 4022 é a porta padrão para o visual studio 2017 x64 depurador remoto. Para outras atribuições remotas da porta de depurador, consulte [Atribuições de porta de depurador remotas](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Selecione o botão **Encontrar** ao lado da caixa **de destino Conexão** para abrir a caixa de diálogo **Conexões remotas.** A caixa de diálogo **Conexões Remotas** lista todos os dispositivos que estão na sua sub-rede local ou diretamente conectados ao seu computador. Talvez seja necessário abrir a [porta UDP 3702](../debugger/remote-debugger-port-assignments.md) no servidor para descobrir dispositivos remotos. Selecione o computador ou dispositivo que deseja e clique em **Selecionar**.

   > [!NOTE]
   > A **configuração do tipo Conexão** persiste entre as sessões de depuração. A configuração **de destino Conexão** persiste entre as sessões de depuração somente se ocorrer uma conexão de depuração bem-sucedida com esse destino.

3. Clique **em Atualizar** para preencher a lista de processos **disponíveis.**

    >[!TIP]
    >Os processos podem iniciar e parar em segundo plano enquanto a caixa de diálogo **Anexar ao processo** estiver aberta, de modo que a lista de processos em execução pode nem sempre estar atual. Você pode selecionar **Atualizar** a qualquer momento para ver a lista atual.

4. Na lista **de processos disponíveis,** encontre e selecione o processo ou processos a que deseja anexar.

   - Para selecionar rapidamente um processo, digite seu nome ou primeira letra na caixa **Processos Filter.**

   - Se você não sabe o nome do processo, navegue pela lista ou veja [cenários comuns de depuração](#BKMK_Scenarios) para alguns nomes de processo comuns.

   - Para encontrar processos em execução em todas as contas de usuário, selecione os processos Mostrar de todas as caixas de seleção **de usuários.**

     >[!NOTE]
     >Se você tentar anexar a um processo de propriedade de uma conta de usuário não confiável, aparecerá uma confirmação da caixa de diálogo de aviso de segurança. Para obter mais informações, consulte [aviso de segurança: Anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou, se você não tiver certeza, não anexe a esse processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. No **campo Anexar ao** campo, certifique-se de que o tipo de código que você planeja depurar está listado. A configuração **automática** padrão funciona para a maioria dos tipos de aplicativos.

   Para selecionar os tipos de código manualmente:
   1. Clique em **Selecionar**.
   1. Na **caixa de** diálogo Selecionar tipo de código, selecione **Depurar esses tipos de código**.
   1. Selecione os tipos de código que deseja depurar.
   1. Selecione **OK**.

6. Selecionar **Anexar**.

>[!NOTE]
>Você pode ser anexado a vários aplicativos para depuração, mas apenas um aplicativo está ativo no depurador de cada vez. Você pode definir o aplicativo ativo na barra de ferramentas visual studio **debug location** ou **processes.**

Em alguns casos, quando você depura em uma sessão de Área de Trabalho Remota (Serviços de Terminal), a lista **de processos disponíveis** não exibirá todos os processos disponíveis. Se você estiver executando o Visual Studio como um usuário que tem uma conta de usuário limitada, a lista **de processos disponíveis** não mostrará processos que estão sendo executados na Sessão 0. A sessão 0 é usada para serviços e outros processos de servidor, incluindo *w3wp.exe*. Você pode resolver o problema executando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em uma conta de administrador ou executando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no console do servidor em vez de uma sessão de Serviços de Terminal.

Se nenhuma dessas soluções alternativas é possível, uma terceira opção é anexar ao processo executando `vsjitdebugger.exe -p <ProcessId>` na linha de comando do Windows. Você pode determinar o ID do processo usando *tlist.exe*. Para obter *tlist.exe,* baixe e instale ferramentas de depuração para Windows, disponíveis nos [downloads WDK e WinDbg](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"


## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Anexar a um processo .NET Core em execução no Linux usando SSH

Para obter mais informações, consulte [Debug Remote .NET Core em execução no Linux usando SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a>Anexar a um processo em execução em um contêiner Linux Docker

Você pode anexar o depurador do Visual Studio a um processo em execução em um contêiner Linux .NET Core Docker em sua máquina local ou remota usando a caixa de diálogo **Anexar ao processo.**

> [!IMPORTANT]
> Para usar esse recurso, você deve instalar a carga de trabalho de desenvolvimento de plataformas cruzadas .NET Core e ter acesso local ao código-fonte.

**Para anexar a um processo de execução em um contêiner Linux Docker:**

1. No Visual Studio, selecione **Debug > Attach to Process (CTRL+ALT+P)** para abrir a caixa de diálogo **'Anexar ao processo'.**

![Anexar ao menu de processo](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Defina o **tipo de conexão** como **Docker (Contêiner Linux)**.
3. Selecione **Encontrar...** para definir o **destino Conexão** através da caixa de diálogo **Selecionar contêiner do Docker.**

    Você pode depurar um processo de contêiner Docker local ou remotamente.
    
    **Para depurar um processo de contêiner Docker localmente:**
    1. Definir **o host Docker CLI** para local **machine**.
    1. Selecione um recipiente em execução para anexar na lista e aperte **OK**.
    
    ![Selecione menu de contêiner docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. Para depurar remotamente um processo de contêiner Docker:**
    
    > [!NOTE] 
    > Existem duas opções para se conectar remotamente a um processo de execução em um contêiner Docker. A primeira opção, para usar o SSH, é ideal se você não tiver ferramentas Docker instaladas em sua máquina local.  Se você tiver ferramentas Docker instaladas localmente e tiver um daemon Docker configurado para aceitar solicitações remotas, tente a segunda opção, usando um daemon Docker.

    1. ***Para conectar a uma máquina remota via SSH:***
        1. Selecione **Adicionar...** para se conectar a um sistema remoto.<br/>
        ![Conecte-se a um sistema remoto](../debugger/media/connect-remote-system.png "Conecte-se a um sistema remoto")
        1. Selecione um recipiente em execução para anexar após se conectar ao SSH ou daemon com sucesso e aperte **OK**.

    
    1. ***Para definir o alvo para um contêiner remoto executando um processo através de um [daemon Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Especifique o endereço daemon (ou seja, via TCP, IP, etc.) no **host Docker (Opcional)** e clique no link de atualização.
        1. Selecione um recipiente em execução para anexar após conectar-se ao daemon com sucesso e aperte **OK**.

4. Escolha o processo de contêiner correspondente na lista de **processos disponíveis** e **selecione Anexar** para iniciar a depuração do processo de contêiner C# no Visual Studio!

    ![Menu de anexação do Docker concluído](../debugger/media/docker-attach-complete.png "Menu de anexo do Linux Docker concluído")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a>Anexar a um processo em execução em um contêiner Windows Docker

Você pode anexar o depurador do Visual Studio a um processo em execução em um contêiner Do Windows Docker em sua máquina local usando a caixa de diálogo **Anexar ao processo.**

> [!IMPORTANT]
> Para usar esse recurso com um processo .NET Core, você deve instalar a carga de trabalho de desenvolvimento de plataformas cruzadas .NET Core e ter acesso local ao código-fonte.

**Para anexar a um processo de execução em um contêiner do Windows Docker:**

1. No Visual Studio, selecione **Debug > Attach to Process** (ou **CTRL+ALT+P**) para abrir a caixa de diálogo **'Anexar ao processo'.**

   ![Anexar ao menu de processo](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Defina o **tipo de conexão** **como Docker (Contêiner do Windows)**.
3. Selecione **Encontrar...** para definir o **destino Conexão** usando a caixa de diálogo **Selecionar contêiner do Docker.**

    > [!IMPORTANT]
    > O processo de destino deve ter a mesma arquitetura do processador que o contêiner Docker Windows em que está sendo executado.
    
   A configuração do destino para um contêiner remoto via SSH está atualmente indisponível e só pode ser feita usando um daemon Docker.
    
    ***Para definir o alvo para um contêiner remoto executando um processo através de um [daemon Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
    1. Especifique o endereço daemon (ou seja, via TCP, IP, etc.) no **host Docker (Opcional)** e clique no link de atualização. 

    1. Selecione um recipiente em execução para anexar depois de conectar-se ao daemon com sucesso e escolha OK.
    
4. Escolha o processo de contêiner correspondente na lista de **processos disponíveis** e **selecione Anexar** para iniciar a depuração do processo de contêiner C#.

    ![Menu de anexação do Docker concluído](../debugger/media/docker-attach-complete-windows.png "Menu de anexação do Windows Docker concluído")
    

5.  Escolha o processo de contêiner correspondente na lista de processos disponíveis e escolha **Anexar** para iniciar a depuração do processo de contêiner C#.


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a>Reconecte-se a um processo

Você pode reconectar rapidamente aos processos aos quais você foi anteriormente anexado, escolhendo **Debug** > **Reattach to Process** **(Shift**+**Alt**+**P**). Ao escolher este comando, o depurador tentará imediatamente anexar aos últimos processos a que você anexou, primeiramente tentando corresponder ao ID do processo anterior e se isso falhar, combinando com o nome do processo anterior. Se não forem encontradas correspondências ou se vários processos tiverem o mesmo nome, a caixa de diálogo **Anexar ao processo** será aberta para que você possa selecionar o processo correto.

> [!NOTE]
> O comando **Reattach to Process** está disponível a partir do Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a>Cenários comuns de depuração

Para ajudá-lo a determinar se deve usar **O Attach to Process** e a qual processo anexar, a tabela a seguir mostra alguns cenários comuns de depuração, com links para mais instruções quando disponíveis. (A lista não é exaustiva.)

Para alguns tipos de aplicativos, como aplicativos Universal Windows App (UWP), você não se anexa diretamente a um nome de processo, mas usa a opção **Debug Installed App Package** menu no Visual Studio (ver tabela).

Para que o depurador se anexe ao código escrito em C++, o código precisa emitir `DebuggableAttribute`. Você pode adicionar isso ao seu código automaticamente vinculando à opção do vinculador [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

Para depuração de script do lado do cliente, a depuração de script deve ser ativada no navegador. Para depurar o script do lado do cliente no Chrome, escolha o **kit da Web** como o tipo de código e, `chrome.exe --remote-debugging-port=9222` dependendo do tipo de aplicativo, você pode precisar fechar todas as instâncias do Chrome e iniciar o navegador no modo de depuração (digite a partir de uma linha de comando).

Para selecionar rapidamente um processo de execução para anexar, no Visual Studio, digite **Ctrl**+**Alt**+**P**e digite a primeira letra do nome do processo.

|Cenário|Método de depuração|Nome do processo|Notas e links|
|-|-|-|-|
|Depuração remota ASP.NET 4 ou 4.5 em um servidor IIS|Use ferramentas remotas **e conecte-se ao processo**|*w3wp.exe*|Consulte [ASP.NET de depuração remota em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depuração remota ASP.NET Core em um servidor IIS|Use ferramentas remotas **e conecte-se ao processo**|*dotnet.exe* ou *appname.exe*|Para a implantação do aplicativo, consulte [Publicar para IIS](https://docs.asp.net/en/latest/publishing/iis.html). Para depuração, consulte [Depuração remota ASP.NET Core em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Depurar o script do lado do cliente em um servidor IIS local, para tipos de aplicativos suportados |Usar **anexar ao processo**|*chrome.exe*, *MicrosoftEdgeCP.exe* ou *iexplore.exe*|A depuração do script deve ser ativada. Para o Chrome, você também deve executar o Chrome no modo de depuração e selecionar **código Webkit** no **campo 'Anexar'.**|
|Depurar um aplicativo C#, Visual Basic ou C++ na máquina local|Use depuração padrão **(F5)** ou **Conecte-se ao processo**|*\<nome de aplicativo>.exe*|Na maioria dos cenários, use depuração padrão e não **seja anexado ao processo.**|
|Depuração remota de um aplicativo de desktop do Windows|Ferramentas remotas|N/D| Consulte [depurar remotamente um aplicativo C# ou Visual Basic](../debugger/remote-debugging-csharp.md) ou [depurar remotamente um aplicativo C++](../debugger/remote-debugging-cpp.md)|
|Debug .NET Core no Linux|Usar **anexar ao processo**|*dotnet.exe*|Para usar o SSH, consulte [Debug Remote .NET Core em execução no Linux usando SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). |
|Depurar um aplicativo de ASP.NET na máquina local depois de iniciar o aplicativo sem o depurador|Usar **anexar ao processo**|*iiexpress.exe*|Isso pode ser útil para fazer o seu aplicativo carregar mais rápido, como (por exemplo) ao traçar perfis. |
|Depurar outros tipos de aplicativos suportados em um processo de servidor|Se o servidor for remoto, use ferramentas remotas **e conecte-se ao processo**|*chrome.exe,* *iexplore.exe*ou outros processos|Se necessário, use o Resource Monitor para ajudar a identificar o processo. Consulte [Depuração remota](../debugger/remote-debugging.md).|
|Depurar remotamente um aplicativo Universal Windows (UWP), OneCore, HoloLens ou IoT|Depurar pacote do aplicativo instalado|N/D|Consulte [Debug um pacote de aplicativo instalado](debug-installed-app-package.md) em vez de usar O Attach to **Process**|
|Depurar um aplicativo Universal Windows (UWP), OneCore, HoloLens ou IoT que você não começou no Visual Studio|Depurar pacote do aplicativo instalado|N/D|Consulte [Debug um pacote de aplicativo instalado](debug-installed-app-package.md) em vez de usar O Attach to **Process**|

## <a name="use-debugger-features"></a>Use recursos de depurador

Para usar os recursos completos do depurador Visual Studio (como acertar pontos de interrupção) ao anexar a um processo, o aplicativo deve exatamente corresponder à sua fonte local e símbolos. Ou seja, o depurador deve ser capaz de carregar os arquivos de símbolo correto [(.pdb).](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Por padrão, isso requer uma compilação de depuração.

Para cenários de depuração remota, você deve ter o código-fonte (ou uma cópia do código-fonte) já aberto no Visual Studio. Os binários de aplicativos compilados na máquina remota devem vir da mesma compilação que na máquina local.

Em alguns cenários locais de depuração, você pode depurar no Visual Studio sem acesso à fonte se os arquivos de símbolo corretos estiverem presentes com o aplicativo. Por padrão, isso requer uma compilação de depuração. Para obter mais informações, consulte [Especificar símbolo e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Solucionar problemas de anexo
 Quando o depurador se anexa a um processo em execução, o processo pode conter um ou mais tipos de código. Os tipos de código aos quais o depurador pode se anexar são exibidos e selecionados na caixa de diálogo **Selecionar Tipo de Código**.

 Às vezes, o depurador pode ser anexado com êxito a um tipo de código, mas não a outro tipo de código. Isso pode ocorrer se você estiver tentando anexar a um processo que esteja sendo executado em um computador remoto. O computador remoto pode ter componentes de depuração remota instalados para alguns tipos de código mas não para outros. Isso também pode ocorrer se você tentar anexar a dois ou mais processos para depuração direta de banco de dados. A depuração de SQL dá suporte à anexação de apenas um único processo.

 Se o depurador é capaz de anexar a alguns, mas não a todos os tipos de código, você verá uma mensagem identificando quais tipos falharam em anexar.

 Se o depurador for anexado com êxito a pelo menos um tipo de código, você poderá depurar o processo. Você poderá depurar apenas os tipos de código que foram anexados com êxito. O código não conectado no processo ainda será executado, mas você não será capaz de definir pontos de interrupção, visualizar dados ou executar outras operações de depuração nesse código.

 Se você quiser informações mais específicas sobre por que o depurador falhou em anexar a um tipo de código, tente reconectar apenas esse tipo de código.

 **Para obter informações específicas sobre o motivo de um tipo de código ter falhado na anexação:**

1. Desanexe do processo. No menu **Debug,** selecione **Desapegar Todos**.

1. Reconecte-se ao processo, selecionando apenas o tipo de código que não conseguiu anexar.

    1. Na caixa de diálogo **Anexar ao Processo**, selecione o processo na lista **Processos Disponíveis**.

    2. Selecione **Selecionar**.

    3. Na caixa de diálogo **Tipo de Código Selecionado**, selecione **Depurar esses tipos de código** e o tipo de código que falhou em ser anexado. Desmarque os outros tipos de código.

    4. Selecione **OK**.

    5. Na caixa de diálogo 'Anexar ao processo', **selecione 'Anexar '''''''''''''''''''''** **Attach to Process**

    Desta vez, o anexo falhará completamente e você receberá uma mensagem de erro específica.

## <a name="see-also"></a>Confira também

- [Depurar vários processos](../debugger/debug-multiple-processes.md)
- [Depuração just-in-time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Depuração remota](../debugger/remote-debugging.md)
