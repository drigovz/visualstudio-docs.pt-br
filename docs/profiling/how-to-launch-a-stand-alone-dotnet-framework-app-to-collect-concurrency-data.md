---
title: 'Linha de comando Profiler: Abra o aplicativo .NET do cliente, obtenha dados de concorrência'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4a52c65f8a53d62edde42c26fafef9940046ba5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775386"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Como iniciar um aplicativo do .NET Framework autônomo com o criador de perfil para coletar dados de simultaneidade usando a linha de comando
Este tópico descreve como usar ferramentas de linha de comando das Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para iniciar um aplicativo autônomo (cliente) do .NET Framework e coletar dados de simultaneidade de thread e processo

> [!NOTE]
> Para obter o caminho para as ferramentas de criação de perfil, confira [Especificar o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Em computadores de 64 bits, as versões de 64 e de 32 bits das ferramentas estão disponíveis. Para usar ferramentas de linha de comando do criador de perfil, você precisa adicionar o caminho das ferramentas à variável de ambiente PATH da janela de Prompt de Comando ou adicioná-lo ao próprio comando.

 Enquanto o criador de perfil estiver anexado ao aplicativo, você pode pausar e retomar a coleta de dados. Para concluir uma sessão de criação de perfil, o Criador de perfil não pode mais estar anexado ao aplicativo e o Criador de perfil deve ser desligado explicitamente.

## <a name="start-the-application-with-the-profiler"></a>Iniciar o aplicativo com o criador de perfil
 Para iniciar um aplicativo de destino do .NET Framework com o criador de perfil, use *VSPerfClrEnv.exe* para definir as variáveis de criação de perfil do .NET Framework. Use as opções **/start** e **/launch** do VSPerfCmd para inicializar o criador de perfil e iniciar o aplicativo. Você pode especificar **/start** e **/launch** e suas opções respectivas em uma única linha de comando. Você também pode adicionar a opção **/globaloff** à linha de comando para pausar a coleta de dados no início do aplicativo de destino. Use **/globalon** em uma linha de comando separada para começar a coletar dados.

#### <a name="to-start-an-application-with-the-profiler"></a>Para iniciar um aplicativo com o criador de perfil

1. Abra una janela de prompt de comando.

2. Inicie o criador de perfil. Tipo:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/output:**`OutputFile` [`Options`]

   - A opção [/start](../profiling/start.md) inicializa o criador de perfil.

     | | |
     |-------------------------------------| - |
     | **/start:concurrency** | Permite a coleta de dados de contenção de recursos e de execução do thread. |
     | **/start:concurrency,resourceonly** | Habilita apenas a coleta de dados de contenção de recursos. |
     | **/start:concurrency,threadonly** | Habilita apenas a coleta de dados de execução de thread. |

   - A [opção /saída](../profiling/output.md)**:** `OutputFile` é necessária com **/start**. `OutputFile` especifica o nome e o local do arquivo de dados de criação de perfil (.vsp).

     É possível usar qualquer uma das opções a seguir com a opção **/start:concurrency**.

   | Opção | Descrição |
   | - | - |
   | [/usuário:](../profiling/user-vsperfcmd.md) **:**`domain\`[ ]`username` | Especifica o domínio e o nome de usuário opcional da conta que receberá acesso ao criador de perfil. |
   | [/sessão cruzada](../profiling/crosssession.md) | Habilita a criação de perfil de processos em outras sessões de logon. |
   | [/wincounter:](../profiling/wincounter.md) **:**`WinCounterPath` | Especifica um contador de desempenho do Windows que deve ser coletado durante a criação de perfil. |
   | [/marca automática:](../profiling/automark.md) **:**`Interval` | Use somente com **/wincounter**. Especifica o número de milissegundos entre eventos de coleta do contador de desempenho do Windows. O padrão é 500 ms. |
   | [/eventos:](../profiling/events-vsperfcmd.md) **:**`Config` | Especifica um evento de ETW (Rastreamento de Eventos para Windows) a ser coletado durante a criação de perfil. Os eventos ETW são coletados separadamente (.* etl*) arquivo. |

3. Inicie o aplicativo de destino. Tipo:

    **VSPerfCmd**[/lançamento](../profiling/launch.md) `Options` **:** `AppName` `Sample Event`[ ] [ ]  

    É possível usar qualquer uma das opções a seguir com a opção **/launch**.

   |Opção|Descrição|
   |------------|-----------------|
   |[/args:](../profiling/args.md) **:**`Arguments`|Especifica uma cadeia de caracteres que contém os argumentos de linha de comando a serem passados para o aplicativo de destino.|
   |[/console](../profiling/console.md)|Inicia o aplicativo de destino de linha de comando em uma janela separada.|
   |[/targetclr:](../profiling/targetclr.md) **:**`Version`|Especifica a versão do CLR (Common Language Runtime) a ser analisada quando mais de uma versão de tempo de execução for carregada em um aplicativo.|

## <a name="control-data-collection"></a>Controlar a coleta de dados
 Enquanto o aplicativo de destino estiver em execução, você pode controlar a coleta de dados iniciando e parando a gravação de dados no arquivo usando as opções de *VSPerfCmd.exe*. Controlar a coleta de dados permite coletar dados de uma parte específica da execução do programa, como o início ou o desligamento do aplicativo.

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar e interromper a coleta de dados

1. Os seguintes pares de opções *VSPerfCmd.exe* iniciam e param a coleta de dados. Especifica cada opção em uma linha de comando separada. É possível ativar e desativar a coleta de dados várias vezes.

    |Opção|Descrição|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) ou interrompe (**/globaloff**) a coleta de dados para todos os processos.|
    |[/processon:](../profiling/processon-and-processoff.md) **:** `PID` [/processoff:](../profiling/processon-and-processoff.md) **:**`PID`|Inicia (**/processon**) ou interrompe (**/processoff**) a coleta de dados para o processo especificado pela ID de processo (`PID`).|
    |[/attach:](../profiling/attach.md) **:**`PID` { `ProcName`&#124;} [/desapego](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** começa a coletar dados para o processo especificado pela ID de processo (`PID`) ou pelo nome de processo (ProcName). **/detach** interrompe a coleta de dados para o processo especificado ou para todos os processos se nenhum processo específico for especificado.|

## <a name="end-the-profiling-session"></a>Encerrar a sessão de criação de perfil
 Para encerrar uma sessão de criação de perfil, o criador de perfil não pode estar coletando dados. Você pode parar a coleta de dados de simultaneidade ao fechar o aplicativo analisado ou ao invocar a opção **VSPerfCmd /detach**. Depois, você invoca a opção **VSPerfCmd /shutdown** para desligar o criador de perfil e fechar o arquivo de dados de criação de perfil. O comando **VSPerfClrEnv /off** limpa as variáveis de ambiente da criação de perfil.

#### <a name="to-end-a-profiling-session"></a>Para encerrar uma sessão de criação de perfil

1. Siga um destes procedimentos para desanexar o criador de perfil do aplicativo de destino.

    - Feche o aplicativo de destino.

         -ou-

    - Tipo **VSPerfCmd/desapego**

2. Desligue o criador de perfil

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Confira também
- [Coletar dados de concorrência](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)
