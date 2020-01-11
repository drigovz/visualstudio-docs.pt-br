---
title: Anexar a processos em execução com o depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b30e171756527352976dcb03abb0d1c32370c442
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849887"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Anexar aos processos em execução com o Depurador do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode anexar o depurador do Visual Studio a um processo em execução em um computador local ou remoto. Depois que o processo estiver em execução, clique em **Depurar/anexar ao processo** (ou pressione **Ctrl + Alt + P**) para abrir a caixa **de diálogo anexar ao processo** .

Você pode usar essa capacidade para depurar aplicativos que estão sendo executados em um computador local ou remoto, depurar vários processos simultaneamente ou depurar um aplicativo que não foi criado no Visual Studio. Geralmente, é útil quando você deseja depurar um aplicativo, mas (por qualquer motivo) você não iniciou o aplicativo do Visual Studio com o depurador anexado. Por exemplo, se você estiver executando o aplicativo sem o depurador e clicar em uma exceção, você poderá anexar ao processo que executa o aplicativo para iniciar a depuração.

> [!TIP]
> Não tem certeza se você precisa usar **anexar ao processo** para seu cenário de depuração? Consulte [cenários comuns de depuração](#BKMK_Scenarios). Se você quiser depurar aplicativos ASP.NET que foram implantados no IIS, consulte [depuração remota ASP.net em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="BKMK_Attach_to_a_running_process"></a>Anexar a um processo em execução no computador local
 Para anexar a um processo, você deve saber o nome do processo (consulte [cenários comuns de depuração](#BKMK_Scenarios) para alguns nomes de processo comuns).

1. No Visual Studio, selecione **Depurar/anexar para processar** (ou pressione **Ctrl + Alt + P**).

2. Na caixa de diálogo **anexar ao processo** , localize o programa que você deseja anexar na lista **processos disponíveis** .

     Para selecionar rapidamente o processo desejado, digite a primeira letra do nome do processo. Se você não souber o nome do processo, consulte [cenários comuns de depuração](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Se o processo estiver sendo executado em uma conta de usuário diferente, marque a caixa de seleção **Mostrar processos de todos os usuários**.

3. Na caixa **anexar a** , verifique se o tipo de código que você irá depurar está listado. A configuração **automática** padrão tenta determinar o tipo de código que você deseja depurar. Para definir o tipo de código manualmente, faça o seguinte

    1. Na caixa **anexar a** , clique em **selecionar**.

    2. Na caixa de diálogo **Selecionar tipo de código** , clique em **depurar esses tipos de código** e selecione os tipos a serem depurados.

    3. Clique em **OK**.

4. Clique em **Anexar**.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Anexar a um processo em um computador remoto
 Para anexar a um processo, você deve saber o nome do processo (consulte [cenários comuns de depuração](#BKMK_Scenarios) para alguns nomes de processo comuns). Para obter uma orientação mais completa para aplicativos ASP.NET que foram implantados no IIS, consulte [depuração remota ASP.net em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Para outros aplicativos, é possível encontrar o nome do processo no Gerenciador de tarefas.

 Ao usar a caixa de diálogo **anexar ao processo** , você pode selecionar outro computador que tenha sido configurado para depuração remota. Para obter mais informações, consulte [depuração remota](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Quando você tiver selecionado um computador remoto, poderá exibir uma lista de processos disponíveis que estão em execução no computador e anexá-la a um ou mais processos para depuração.

 **Para selecionar um computador remoto:**

1. No Visual Studio, selecione **Depurar/anexar para processar** (ou pressione **Ctrl + Alt + P**).

2. Na caixa de diálogo **anexar ao processo** , selecione o tipo de conexão apropriado na lista de **transporte** . O **padrão** é a configuração correta para a maioria dos casos.

   A configuração de **transporte** persiste entre sessões de depuração.

3. Use a caixa de listagem **qualificador** para escolher o nome do computador remoto por um dos seguintes métodos:

   1. Digite o nome na caixa de listagem **qualificador** .

      > [!NOTE]
      > Se, em etapas posteriores, você não puder se conectar usando o nome do computador remoto, use o endereço IP. (O número da porta pode aparecer automaticamente após a seleção do processo. Você também pode inseri-lo manualmente. Na ilustração a seguir, 4020 é a porta padrão para o depurador remoto.)

   2. Clique na seta suspensa anexada à caixa de listagem **qualificador** e selecione o nome do computador na lista suspensa.

   3. Clique no botão **Localizar** ao lado da lista **qualificador** para abrir a caixa de diálogo **selecionar conexão do depurador remoto** . A caixa de diálogo **selecionar conexão do depurador remoto** lista todos os dispositivos que estão na sua subrede local e qualquer dispositivo conectado diretamente ao computador por meio de um cabo Ethernet. Clique no computador ou dispositivo desejado e, em seguida, clique em **selecionar**.

      A configuração do **qualificador** persiste entre sessões de depuração somente se uma conexão de depuração bem-sucedida ocorrer com esse qualificador.

4. Cliquem em **Atualizar**.

     A lista **Processos Disponíveis** é exibida automaticamente quando você abre a caixa de diálogo **Processos**. Os processos podem iniciar e parar em segundo plano quando a caixa de diálogo está aberta. No entanto, o conteúdo nem sempre será atual. Você pode atualizar a lista a qualquer momento para ver a lista atual de processos clicando em **Atualizar**.

5. Na caixa de diálogo **anexar ao processo** , localize o programa que você deseja anexar na lista **processos disponíveis** .

    Se o processo estiver sendo executado em uma conta de usuário diferente, marque a caixa de seleção **Mostrar processos de todos os usuários**.

6. Clique em **Anexar**.

## <a name="additional-info"></a>Informações adicionais

Você pode estar associado a vários programas enquanto depura, mas somente um programa está ativo no depurador em um determinado momento. Você pode definir o programa ativo na barra de ferramentas **local de depuração** ou na janela **processos** . Para obter mais informações, consulte [como: definir o programa atual](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Se você tentar anexar a um processo de propriedade de uma conta de usuário não confiável, aparecerá uma confirmação da caixa de diálogo de aviso de segurança. Para obter mais informações, consulte [aviso de segurança: Anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou, se você não tiver certeza, não anexe a esse processo](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).

Em alguns casos, quando você depura em uma sessão Área de Trabalho Remota (serviços de terminal), a lista de **processos disponíveis** não exibirá todos os processos disponíveis. Se você estiver executando o Visual Studio como um usuário que tem uma conta de usuário limitada, a lista de **processos disponíveis** não mostrará os processos em execução na sessão 0, que é usado para serviços e outros processos de servidor, incluindo w3wp. exe. Você pode resolver o problema executando o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] em uma conta de administrador ou executando o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no console do servidor em vez de uma sessão de Serviços de Terminal. Se nenhuma dessas soluções alternativas for possível, uma terceira opção é anexar ao processo Executando `vsjitdebugger.exe -p` *ProcessId* na linha de comando do Windows. Você pode determinar a ID do processo usando tlist.exe. Para obter tlist. exe, baixe e instale as ferramentas de depuração para Windows, disponíveis em [downloads do WDK e do WinDbg](https://docs.microsoft.com/windows-hardware/drivers/dashboard/).

## <a name="BKMK_Scenarios"></a>Cenários comuns de depuração

Para ajudá-lo a identificar se você precisa usar **anexar ao processo** e a qual processo anexar, alguns cenários de depuração comuns são mostrados aqui (a lista não é exaustiva). Onde mais instruções estão disponíveis, fornecemos links.

Para alguns tipos de aplicativos (como aplicativos da Windows Store), você não anexa diretamente a um nome de processo, mas usa a opção de menu **depurar pacote de aplicativo instalado** em vez disso (consulte a tabela).

> [!NOTE]
> Para obter informações sobre a depuração básica no Visual Studio, consulte [introdução ao depurador](../debugger/getting-started-with-the-debugger.md).

|Cenário|Método de depuração|{1&gt;Nome do Processo&lt;1}|Anotações e links|
|-|-|-|-|
|Depurar um aplicativo gerenciado ou nativo no computador local|Usar anexar ao processo ou à [depuração padrão](../debugger/getting-started-with-the-debugger.md)|*appname*.exe|Para acessar rapidamente a caixa de diálogo, use **Ctrl + Alt + P** e digite a primeira letra do nome do processo.|
|Depurar aplicativos ASP.NET no computador local depois de iniciar o aplicativo sem o depurador|Usar anexar ao processo|iiexpress.exe|Isso pode ser útil para fazer com que seu aplicativo seja carregado mais rapidamente, como (por exemplo) durante a criação de perfil. |
|Depuração remota ASP.NET 4 ou 4,5 em um servidor IIS|Usar as ferramentas remotas e anexar ao processo|w3wp.exe|Consulte [depuração remota ASP.net em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|ASP.NET Core de depuração remota em um servidor IIS|Usar as ferramentas remotas e anexar ao processo|dnx.exe|Para a implantação de aplicativo, consulte [publicar no IIS](https://docs.asp.net/en/latest/publishing/iis.html). Para depuração, consulte [depuração remota ASP.net em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depurar outros tipos de aplicativos com suporte em um processo de servidor|Usar ferramentas remotas (se o servidor for remoto) e anexar ao processo|iexplore. exe ou outros processos|Se necessário, use o Gerenciador de tarefas para ajudar a identificar o processo. Consulte [depuração remota](../debugger/remote-debugging.md) e seções posteriores neste tópico|
|Depuração remota de um aplicativo de área de trabalho do Windows|Ferramentas Remotas e F5|{1&gt;N/A&lt;1}| Consulte [depuração remota](../debugger/remote-debugging.md)|
|Depuração remota de um aplicativo Windows universal (UWP), OneCore, HoloLens ou IoT|Depurar pacote do aplicativo instalado|{1&gt;N/A&lt;1}|Usar **depuração/outros destinos de depuração/depurar pacote do aplicativo instalado** em vez de **anexar ao processo**|
|Depurar um aplicativo Windows universal (UWP), OneCore, HoloLens ou IoT que você não iniciou no Visual Studio|Depurar pacote do aplicativo instalado|{1&gt;N/A&lt;1}|Usar **depuração/outros destinos de depuração/depurar pacote do aplicativo instalado** em vez de **anexar ao processo**|

> [!WARNING]
> Para anexar a um aplicativo universal do Windows que é escrito em JavaScript, primeiro você deve habilitar a depuração para o aplicativo. Consulte [anexar o depurador](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) no centro de desenvolvimento do Windows.

> [!NOTE]
> Para que o depurador se anexe ao código escrito em C++, o código precisa emitir `DebuggableAttribute`. Você pode adicionar isso ao seu código automaticamente vinculando à opção do vinculador [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).

## <a name="what-debugger-features-can-i-use"></a>Quais recursos do depurador posso usar?

Para usar os recursos completos do depurador do Visual Studio (como atingir pontos de interrupção) ao anexar a um processo, o executável deve corresponder exatamente à fonte local e aos símbolos (ou seja, o depurador deve ser capaz de carregar os [arquivos de símbolo (. pbd)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)corretos). Por padrão, isso requer uma compilação de depuração.

Para cenários de depuração remota, você deve ter o código-fonte (ou uma cópia do código-fonte) já aberto no Visual Studio. Os binários de aplicativo compilados no computador remoto devem vir da mesma compilação que no computador local.

Em alguns cenários de depuração local, você pode depurar no Visual Studio sem acesso à origem se os arquivos de símbolo corretos estiverem presentes com o aplicativo (por padrão, isso requer uma compilação de depuração). Para obter mais informações, consulte [especificar o símbolo e os arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a> Solucionar problemas de anexo
 Quando o depurador se anexa a um processo em execução, o processo pode conter um ou mais tipos de código. Os tipos de código aos quais o depurador pode se anexar são exibidos e selecionados na caixa de diálogo **Selecionar Tipo de Código**.

 Às vezes, o depurador pode ser anexado com êxito a um tipo de código, mas não a outro tipo de código. Isso pode ocorrer se você estiver tentando anexar a um processo que esteja sendo executado em um computador remoto. O computador remoto pode ter componentes de depuração remota instalados para alguns tipos de código mas não para outros. Isso também pode ocorrer se você tentar anexar a dois ou mais processos para depuração direta de banco de dados. A depuração de SQL dá suporte à anexação de apenas um único processo.

 Se o depurador puder se conectar a alguns, mas não a todos os tipos de código, você verá uma mensagem identificando quais tipos não conseguiram estabelecer conexão.

 Se o depurador for anexado com êxito a pelo menos um tipo de código, você poderá depurar o processo. Você poderá depurar apenas os tipos de código que foram anexados com êxito. A mensagem do exemplo anterior mostra que o tipo de código de script não foi anexado. Portanto, você não pode depurar o código do script dentro do processo. O código de script no processo ainda seria executado, mas você não poderia definir pontos de interrupção, exibir dados ou executar outras operações de depuração no script.

 Se você desejar informações mais específicas sobre por que o depurador não foi anexado a um tipo de código, tente reanexar somente àquele tipo de código.

 **Para obter informações específicas sobre por que um tipo de código falhou ao anexar**

1. Desanexe do processo. No menu **depurar** , clique em **desanexar tudo**.

2. Anexe o processo novamente, selecionando apenas um único tipo de código.

   1. Na caixa de diálogo **anexar ao processo** , selecione o processo na lista **processos disponíveis** .

   2. Clique em **Selecionar**.

   3. Na caixa de diálogo **Tipo de Código Selecionado**, selecione **Depurar esses tipos de código** e o tipo de código que falhou em ser anexado. Limpe qualquer outro código.

   4. Clique em **OK**. A caixa de diálogo **Selecionar tipo de código** é fechada.

   5. Na caixa de diálogo **anexar ao processo** , clique em **anexar**.

      Desta vez, o anexo falhará completamente e você receberá uma mensagem de erro específica.

## <a name="see-also"></a>Veja também
 [Depurar vários processos](../debugger/debug-multiple-processes.md) a depuração [remota](../debugger/remote-debugging.md) [just-in-time](../debugger/just-in-time-debugging-in-visual-studio.md)
