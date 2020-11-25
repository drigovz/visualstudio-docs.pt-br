---
title: Executar ferramentas de criação de perfil com ou sem o depurador | Microsoft Docs
description: Saiba mais sobre as diferenças entre os diferentes modos disponíveis para as ferramentas de criação de perfil
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0bd8f90c586366a298ba96009dfe5d87a042141b
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970294"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Executar ferramentas de criação de perfil com ou sem o depurador

O Visual Studio oferece uma opção de medida de desempenho e ferramentas de criação de perfil. Algumas ferramentas, como uso de CPU e uso de memória, podem ser executadas com ou sem o depurador e no lançamento ou depuração de configurações de compilação. As ferramentas que aparecem na [janela ferramentas de diagnóstico](../profiling/profiling-feature-tour.md#measure-performance-while-debugging) são executadas somente durante uma sessão de depuração. As ferramentas que aparecem no [criador de perfil de desempenho](../profiling/profiling-feature-tour.md#post_mortem) são executadas sem o depurador e você analisa os resultados depois de optar por parar e coletar dados (para análise pós-mortem).

>[!NOTE]
>É possível usar as ferramentas de desempenho de não depurador com o Windows 7 e posterior. O Windows 8 ou posterior é necessário para executar as ferramentas de criação de perfil integradas ao depurador.

O Criador de Perfil de Desempenho do não depurador e as Ferramentas de Diagnóstico integradas ao depurador fornecem diferentes informações e experiências. As ferramentas integradas ao depurador mostram valores variáveis e permitem que você use pontos de interrupção. Ferramentas de não depurador oferecem resultados mais próximos à experiência do usuário final.

Para ajudar a decidir quais ferramentas e os resultados usar, considere o seguinte:

- Ferramenta integrada do depurador versus ferramenta não depurador
  - Problemas de desempenho externos, como E/S de arquivo ou problemas na capacidade de resposta da rede, não terão uma aparência muito diferente nas ferramentas do depurador ou de não depurador.
  - O próprio depurador altera os tempos de desempenho, pois ele precisa de operações do depurador, como interceptar eventos de carregamento de exceção e módulo.
  - Os números de desempenho da compilação de versão no criador de perfil de desempenho são os mais precisos e precisos. Os resultados da ferramenta integrada ao depurador são mais úteis para comparar com outras medidas relacionadas à depuração ou para usar os recursos do depurador.
  - Algumas ferramentas, como a ferramenta de alocação de objeto .NET, estão disponíveis somente para cenários que não são do depurador.
- Depurar vs. Build de versão
  - Para problemas causados por chamadas com uso intensivo de CPU, pode haver diferenças consideráveis de desempenho entre compilações de versão e depuração. Verifique se o problema existe nas compilações de versão.
  - Se o problema ocorrer somente durante compilações de depuração, você provavelmente não precisará executar as ferramentas de não depurador. Para problemas de compilação de versão, decida se os recursos fornecidos pelas ferramentas integradas ao depurador ajudarão a identificar o problema.
  - Os builds de versão fornecem otimizações como embutimento de constantes e de chamadas de função, remoção de caminhos de código não utilizados e armazenamento de variáveis de maneiras que não possam ser usadas pelo depurador. Os números de desempenho nas compilações de depuração são menos precisos, pois as compilações de depuração não têm essas otimizações.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Coletar dados de criação de perfil ao depurar

Quando você inicia a depuração no Visual Studio selecionando **depurar**  >  **Iniciar Depuração** ou pressionando **F5**, a janela **ferramentas de diagnóstico** é exibida por padrão. Para abri-lo manualmente, selecione **depurar**  >  **janelas**  >  **Mostrar ferramentas de diagnóstico**. A janela **Ferramentas de Diagnóstico** mostra informações sobre eventos, memória do processo e uso da CPU.

![Captura de tela da janela de Ferramentas de Diagnóstico](../profiling/media/diagnostictoolswindow.png " Janela Ferramentas de Diagnóstico")

- Use o ícone **Configurações** na barra de ferramentas para selecionar se deseja exibir **Uso de Memória**, **Análise da interface do usuário** e **Uso da CPU**.

- Selecione **configurações** na lista suspensa **configurações** para abrir as **páginas de propriedades do ferramentas de diagnóstico** com mais opções.

- Se estiver executando Visual Studio Enterprise, você poderá habilitar ou desabilitar o IntelliTrace acessando **ferramentas**  >  **Opções**  >  **IntelliTrace**.

A sessão de diagnóstico termina quando você interrompe a depuração.

Para obter mais informações, consulte:

- [Medir o desempenho do aplicativo analisando o uso da CPU](../profiling/beginners-guide-to-performance-profiling.md)
- [Medir o uso de memória no Visual Studio](../profiling/memory-usage.md)

### <a name="the-events-tab"></a>A guia Eventos

Durante uma sessão de depuração, a guia Eventos da janela Ferramentas de Diagnóstico lista os eventos de diagnóstico que ocorrem. O *ponto de interrupção* de prefixos de categoria, *arquivo* e outros, permitem que você examine rapidamente a lista em busca de uma categoria ou ignore as categorias das quais você não se importa.

Use a lista suspensa **filtro** para filtrar eventos dentro e fora do modo de exibição, selecionando ou desmarcando categorias específicas de eventos.

![Captura de tela do filtro de eventos de diagnóstico](../profiling/media/diagnosticeventfilter.png "Filtro de eventos de diagnóstico")

Use a caixa de pesquisa para localizar uma cadeia de caracteres específica na lista de eventos. Aqui estão os resultados de uma pesquisa do *nome* da cadeia de caracteres que correspondeu a quatro eventos:

![Captura de tela da pesquisa de eventos de diagnóstico](../profiling/media/diagnosticseventsearch.png "Pesquisa de eventos de diagnóstico")

Para obter mais informações, consulte [Pesquisando e filtrando a guia de Eventos na janela de Ferramentas de Diagnóstico](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Coletar dados de criação de perfil sem depuração

Para coletar dados de desempenho sem depuração, é possível executar as ferramentas do Criador de Perfil de Desempenho.

1. Com um projeto aberto no Visual Studio, defina a configuração da solução como **liberar** e selecione **depurador local do Windows** (ou **computador local**) como o destino de implantação.

1. Selecione **debug**  >  **Performance Profiler** ou pressione **ALT** + **F2**.

1. Na página inicialização das ferramentas de diagnóstico, selecione uma ou mais ferramentas para executar. Somente as ferramentas aplicáveis ao tipo de projeto, ao sistema operacional e à linguagem de programação são mostradas. Selecione **Mostrar todas as ferramentas** para ver também as ferramentas desabilitadas para essa sessão de diagnóstico.

   ![Captura de tela das ferramentas de diagnóstico](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Para iniciar a sessão de diagnóstico, selecione **Iniciar**.

   Enquanto a sessão está em execução, algumas ferramentas mostram grafos de dados em tempo real na página ferramentas de diagnóstico, bem como controles para pausar e retomar a coleta de dados.

    ![Captura de tela da coleta de dados no criador de perfil de desempenho](../profiling/media/diaghubcollectdata.png "Coletar dados do Hub")

1. Para encerrar a sessão de diagnóstico, selecione **Interromper coleta**.

   Os dados analisados aparecem na página do **relatório** .

Você pode salvar os relatórios e abri-los na lista de **sessões abertas recentemente** na página de inicialização ferramentas de diagnóstico.

![Captura de tela de Ferramentas de Diagnóstico lista de sessões abertas recentemente](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

Para obter mais informações, consulte:

- [Analisar o uso da CPU](../profiling/cpu-usage.md)
- [Analisar o uso de memória para código .NET](../profiling/dotnet-alloc-tool.md)
- [Analisar o uso de memória](../profiling/memory-usage-without-debugging2.md)
- [Analisar o desempenho do código assíncrono do .NET](../profiling/analyze-async.md)
- [Analisar o desempenho do banco de dados](../profiling/analyze-database.md)
- [Analisar o uso da GPU](../profiling/gpu-usage.md)

## <a name="collect-profiling-data-from-the-command-line"></a>Coletar dados de criação de perfil da linha de comando

Para medir os dados de desempenho da linha de comando, você pode usar VSDiagnostics.exe, que está incluído com o Visual Studio ou o Ferramentas Remotas. Isso é útil para capturar rastreamentos de desempenho em sistemas nos quais o Visual Studio não está instalado ou para gerar scripts da coleção de rastreamentos de desempenho. Para obter instruções detalhadas, consulte [medir o desempenho do aplicativo na linha de comando](../profiling/profile-apps-from-command-line.md).