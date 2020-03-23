---
title: 'Linha de comando Profiler: Componente .NET do cliente do instrumento, obtenha dados de tempo'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: ef50983d964c4b7ef6479117ed2501569a77a62d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778902"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Como instrumentar um componente do .NET Framework autônomo e coletar dados de tempo com o criador de perfil usando a linha de comando
Este tópico descreve como usar as ferramentas da linha de comando das Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para instrumentar um componente do .NET Framework, como um arquivo .*exe* ou .*dll*, e coletar dados de tempo detalhados.

> [!NOTE]
> Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos UWP também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Para obter o caminho para as ferramentas de criação de perfil, confira [Especificar o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Em computadores de 64 bits, as versões de 64 e de 32 bits das ferramentas estão disponíveis. Para usar ferramentas de linha de comando do criador de perfil, você precisa adicionar o caminho das ferramentas à variável de ambiente PATH da janela de Prompt de Comando ou adicioná-lo ao próprio comando.
>
> Adicionar dados de interação de camada a uma execução de criação de perfil requer procedimentos específicos com ferramentas de criação de perfil de linha de comando. Confira [Coletar dados de interação de camada](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Para coletar dados detalhados de tempo de um componente do .NET Framework usando o método de instrumentação, você usa a ferramenta [VSInstr.exe](../profiling/vsinstr.md) para gerar uma versão instrumentada do componente e a ferramenta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar variáveis de ambiente de criação de perfil. Em seguida, inicie o criador de perfil.

 Quando o componente instrumentado é executado, os dados de tempo são automaticamente coletados para um arquivo de dados. Você pode pausar e retomar a coleta de dados durante a sessão de criação de perfil.

 Para terminar uma sessão de criação de perfil, feche o aplicativo de destino e feche explicitamente o criador de perfil. Na maioria dos casos, recomendamos desmarcar as variáveis de ambiente de criação de perfil no final de uma sessão.

## <a name="start-the-profiling-session"></a>Iniciar a sessão de criação de perfil

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Para iniciar a criação de perfil usando o método de instrumentação

1. Abra uma janela de Prompt de Comando. Se necessário, adicione o diretório das ferramentas do criador de perfil à variável de ambiente PATH. O caminho não é adicionado na instalação.

2. Use a ferramenta **VSInstr** para gerar uma versão instrumentada do aplicativo de destino.

3. Inicialize as variáveis de ambiente de criação de perfil do .NET Framework. Tipo:

    **VSPerfClrEnv /traceon**

4. Inicie o criador de perfil. Tipo:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - A opção [/start](../profiling/start.md)**:trace** inicializa o criador de perfil.

   - A [opção /saída](../profiling/output.md)**:** `OutputFile` é necessária com **/start**. `OutputFile` especifica o nome e o local do arquivo de dados de criação de perfil (.vsp).

     É possível usar qualquer uma das opções a seguir com a opção **/start:trace**.

   | Opção | Descrição |
   | - | - |
   | [/usuário:](../profiling/user-vsperfcmd.md) **:**`Domain`**\\**[ ]`UserName` | Especifica o domínio e o nome de usuário da conta que possui o processo analisado. Esta opção será necessária apenas se o processo estiver sendo executado como um usuário diferente do usuário conectado. O proprietário do processo é listado na coluna **Nome de Usuário** na guia **Processos** do Gerenciador de Tarefas do Windows. |
   | [/sessão cruzada](../profiling/crosssession.md) | Habilita a criação de perfil de processos em outras sessões. Esta opção será necessária se o aplicativo ASP.NET estiver em execução em uma sessão diferente. O identificador da sessão é listado na coluna **ID da Sessão** na guia **Processos** do Gerenciador de Tarefas do Windows. **/CS** pode ser especificado como uma abreviação de **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Inicia o criador de perfil com a coleta de dados em pausa. Use [/globalon](../profiling/globalon-and-globaloff.md) para retomar a criação de perfil. |
   | [/contador:](../profiling/counter.md) **:**`Config` | Coleta informações do contador de desempenho do processador que é especificado em `Config`. As informações do contador são adicionadas aos dados que são coletados em cada evento de criação de perfil. |
   | [/wincounter:](../profiling/wincounter.md) **:**`WinCounterPath` | Especifica um contador de desempenho do Windows que deve ser coletado durante a criação de perfil. |
   | [/marca automática:](../profiling/automark.md) **:**`Interval` | Use somente com **/wincounter**. Especifica o número de milissegundos entre eventos de coleta do contador de desempenho do Windows. O padrão é 500 ms. |
   | [/eventos:](../profiling/events-vsperfcmd.md) **:**`Config` | Especifica um evento de ETW (Rastreamento de Eventos para Windows) a ser coletado durante a criação de perfil. Os eventos ETW são coletados separadamente (.* etl*) arquivo. |

5. Inicie o aplicativo de destino na janela do Prompt de Comando.

## <a name="control-data-collection"></a>Controlar a coleta de dados
 Quando o aplicativo de destino estiver em execução, você pode controlar a coleta de dados iniciando e interrompendo a gravação de dados no arquivo de dados do criador de perfil usando as opções do *VSPerfCmd.exe*. Controlar a coleta de dados permite coletar dados de uma parte específica da execução do programa, como a inicialização ou o desligamento do aplicativo.

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar e interromper a coleta de dados

- Os pares de opções a seguir iniciam e interrompem a coleta de dados. Especifique cada opção em uma linha de comando separada. É possível ativar e desativar a coleta de dados várias vezes.

    |Opção|Descrição|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) ou interrompe (**/globaloff**) a coleta de dados para todos os processos.|
    |[/processon:](../profiling/processon-and-processoff.md) **:** `PID` [/processoff:](../profiling/processon-and-processoff.md) **:**`PID`|Inicia (**/processon**) ou interrompe (**/processoff**) a coleta de dados para o processo especificado pela ID de processo (`PID`).|
    |[/threadon:](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff:](../profiling/threadon-and-threadoff.md) **:**`TID`|Inicia (**/threadon**) ou interrompe (**/threadoff**) a coleta de dados para o thread especificado pela ID do thread (`TID`).|

## <a name="end-the-profiling-session"></a>Encerrar a sessão de criação de perfil
 Para terminar uma sessão de criação de perfil, feche o aplicativo que está executando o componente instrumentado. Chame a opção **VSPerfCmd** [/shutdown](../profiling/shutdown.md) para desligar o criador de perfil e fechar o arquivo de dados de criação de perfil. O comando **VSPerfClrEnv /off** limpa as variáveis de ambiente da criação de perfil.

#### <a name="to-end-a-profiling-session"></a>Para encerrar uma sessão de criação de perfil

1. Feche o aplicativo de destino.

2. Desligue o criador de perfil. Tipo:

     **VSPerfCmd /shutdown**

3. (Opcional) desmarcar as variáveis de ambiente de criação de perfil. Tipo:

     **VSPerfClrEnv /off**

## <a name="see-also"></a>Confira também
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Visualizações de dados do método de instrumentação](../profiling/instrumentation-method-data-views.md)
