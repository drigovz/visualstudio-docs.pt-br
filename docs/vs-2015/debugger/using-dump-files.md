---
title: Usando arquivos de despejo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: 56
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a2d6215887512f2e0c1410688b2bc924dc1fe3a
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387051"
---
# <a name="using-dump-files"></a>Usando arquivos de despejo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Arquivos de despejo com ou sem heaps; criar um arquivo de despejo; abrir um arquivo de despejo; localizar os binários, os pdbs e o arquivo de origem de um arquivo de despejo. 
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Índice  
 [O que é um arquivo de despejo?](#BKMK_What_is_a_dump_file_)  
  
 [Arquivos de despejo, com ou sem heaps](#BKMK_Dump_files__with_or_without_heaps)  
  
 [Requisitos e limitações](#BKMK_Requirements_and_limitations)  
  
 [Criar um arquivo de despejo](#BKMK_Create_a_dump_file)  
  
 [Abrir um arquivo de despejo](#BKMK_Open_a_dump_file)  
  
 [Localizar arquivos binários, de símbolo (.pdb) e de origem](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
## <a name="what-is-a-dump-file"></a><a name="BKMK_What_is_a_dump_file_"></a>O que é um arquivo de despejo?  
 Um *arquivo de despejo* é um instantâneo de um aplicativo no momento em que o despejo é feito. Ele mostra que processo estava sendo executado e que módulos foram carregados. Se o despejo foi salvo com informações de heap, o arquivo de despejo conterá um instantâneo do que estava na memória do aplicativo naquele momento. Abrir um arquivo de despejo com um heap no Visual Studio é como parar em um ponto de interrupção em uma sessão de depuração. Embora não seja possível continuar a execução, você pode examinar as pilhas, os threads e os valores das variáveis do aplicativo no momento em que o despejo ocorreu.  
  
 Os despejos são usados principalmente para depuração de problemas que ocorrem em computadores aos quais o desenvolvedor não tem acesso. Por exemplo, você pode usar um arquivo de despejo da máquina de um cliente quando não puder reproduzir o programa de falha ou sem resposta do cliente em seu computador. Os despejos também são criados por testadores para salvar dados de falha ou de programa sem resposta para que o computador de teste possa ser usado para mais testes. O depurador do Visual Studio pode salvar arquivos de despejo para código gerenciado ou nativo. O depurador pode carregar arquivos de despejo que foram criados pelo Visual Studio ou por outros programas que salvam arquivos no formato de *minidespejo* .  
  
 ![Voltar ao](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [conteúdo](#BKMK_Contents) superior  
  
## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a>Arquivos de despejo, com ou sem heaps  
 Você pode criar arquivos de despejo com ou sem informações de heap.  
  
- **Arquivos de despejo com heaps** contêm um instantâneo da memória do aplicativo. Isso inclui os valores das variáveis no momento em que o despejo foi criado. Se você carregar um arquivo de despejo que foi salvo com um heap, o Visual Studio poderá carregar os símbolos, mesmo se o binário do aplicativo não for encontrado. O Visual Studio também salva os binários de módulos nativos carregados no arquivo de despejo, o que pode facilitar muito a depuração.  
  
- **Arquivos de despejo sem heaps** são muito menores do que despejos com informações de heap. No entanto, o depurador precisa carregar os binários de aplicativo para localizar as informações do símbolo. Os binários devem ter uma correspondência exata dos binários que foram usados quando o despejo foi criado. Somente os valores das variáveis de pilha são salvos em arquivos de despejo sem dados de heap.  
  
  ![Voltar ao](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [conteúdo](#BKMK_Contents) superior  
  
## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Requisitos e limitações  
  
- Depurar arquivos de despejo de código otimizado pode ser confuso. Por exemplo, o compilador com funções embutidas pode resultar em pilhas de chamadas inesperadas e outras otimizações podem alterar o tempo de vida de variáveis.  
  
- Os arquivos de despejo de computadores de 64 bits devem ser depurados em uma instância do Visual Studio em execução em um computador de 64 bits.  
  
- Em versões do Visual Studio anteriores ao VS 2013, os despejos de aplicativos de 32 bits que eram executados em computadores de 64 bits que foram coletados por algumas ferramentas (como o Gerenciador de Tarefas e o WinDbg de 64 bits) não podiam ser abertos no Visual Studio. Essa limitação foi removida do VS 2013.  
  
- O Visual Studio pode depurar arquivos de despejo de aplicativos nativos em dispositivos ARM. O Visual Studio também pode depurar arquivos de despejo de aplicativos gerenciados em dispositivos ARM, mas somente no depurador nativo.  
  
- Para depurar arquivos de despejo no [modo kernel](https://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) no Visual Studio 2013, baixe a [versão Windows 8.1 das ferramentas de depuração para Windows](https://msdn.microsoft.com/windows/hardware/gg463009). Consulte [depuração de kernel no Visual Studio](https://msdn.microsoft.com/library/windows/hardware/jj149675.aspx).  
  
- O Visual Studio não pode depurar arquivos de despejo salvos no formato de despejo mais antigo conhecido como [despejo de modo de usuário completo](/windows-hardware/drivers/debugger/user-mode-dump-files#full). Observe que um despejo completo do modo de usuário não é igual a um despejo com heap.  
  
- Para depurar com o [SOS.dll (extensão de depuração SOS)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498) no Visual Studio, você deve instalar as ferramentas de depuração para Windows que fazem parte do WDK (Windows Driver Kit). Consulte [Windows 8.1 Preview: baixar kits, bits e ferramentas](https://msdn.microsoft.com/library/windows/hardware/bg127147.aspx).  
  
  ![Voltar ao](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [conteúdo](#BKMK_Contents) superior  
  
## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Criar um arquivo de despejo  
 Para criar um arquivo de despejo com o Visual Studio:  
  
- Enquanto você estiver depurando um processo no Visual Studio, será possível salvar um arquivo de despejo quando o depurador parar em uma exceção ou em um ponto de interrupção. Escolha **Salvar despejo como**, **depurar**. Na caixa de diálogo **Salvar despejo como** , na lista **salvar como tipo** , você pode selecionar **minidespejo** ou **minidespejo com heap** (o padrão).  
  
- Com a [depuração Just-in-time](../debugger/just-in-time-debugging-in-visual-studio.md) habilitada, você pode anexar o depurador a um processo com falha que está sendo executado fora do depurador e, em seguida, salvar um arquivo de despejo. Consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
  Você também pode criar arquivos de despejo com qualquer programa que ofereça suporte ao formato de minidespejo do Windows. Por exemplo, o utilitário de linha de comando **Procdump** do [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) pode criar arquivos de despejo de falha de processo com base em gatilhos ou sob demanda. Confira [requisitos e limitações](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) neste tópico para obter informações adicionais sobre como usar outras ferramentas para criar arquivos de despejo.  
  
  ![Voltar ao](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [conteúdo](#BKMK_Contents) superior  
  
## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Abrir um arquivo de despejo  
  
1. No Visual Studio, escolha **arquivo**, **abrir**, **arquivo**.  
  
2. Na caixa de diálogo **Abrir Arquivo**, localize e selecione o arquivo de despejo. Geralmente, ele terá uma extensão .dmp. Em seguida, escolha **OK**.  
  
3. A janela de **Resumo do arquivo de despejo** é exibida. Nessa janela, você pode exibir informações resumidas da depuração do arquivo de despejo, definir o caminho do símbolo, iniciar a depuração e copiar as informações resumidas na área de transferência.  
  
     ![Página de resumo do minidespejo](../debugger/media/dbg-dump-summarypage.png "DBG_DUMP_SummaryPage")  
  
4. Para iniciar a depuração, vá para a seção **ações** e escolha **Depurar somente com nativo** ou **depurar com misto**.  
  
## <a name="find-binaries-symbol-pdb-files-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a>Localizar arquivos binários, de símbolo (. pdb) e arquivos de origem  
 Para usar os recursos completos do Visual Studio a fim de depurar um arquivo de despejo, você precisar acessar:  
  
- O arquivo .exe para o qual o despejo foi feito e outros binários (DLL, etc.) que foram usados no processo de despejo.  
  
   Se você estiver depurando um despejo com dados de heap, o Visual Studio poderá lidar com binários ausentes para alguns módulos, mas deverá ter binários para módulos suficientes de modo a gerar pilhas de chamadas válidas. O Visual Studio inclui os módulos nativos em um arquivo de despejo com heap.  
  
- Arquivos de símbolo (.pdb) para o .exe e outros binários.  
  
- Arquivos de origem para os módulos em que você está interessado.  
  
   Os arquivos executável e .pdb devem corresponder exatamente à versão e à compilação dos arquivos usados quando o despejo foi criado.  
  
   Você pode depurar usando a desmontagem dos módulos, se não for possível localizar os arquivos de origem.  
  
  **Caminhos de pesquisa padrão para arquivos executáveis**  
  
  O Visual Studio pesquisa automaticamente esses locais em busca de arquivos executáveis que não estão incluídos no arquivo de despejo:  
  
1. O diretório que contém o arquivo de despejo.  
  
2. O caminho do módulo que é especificado no arquivo de despejo. Esse é o caminho do módulo no computador onde o despejo foi coletado.  
  
3. Os caminhos de símbolo especificados na página **depuração**, **Opções**, **símbolos** da caixa de diálogo **ferramentas**do Visual Studio, **Opções** . Você pode adicionar mais locais para pesquisa nessa página.  
  
   **Usando as páginas Nenhum Binário/Símbolo/Origem**  
  
   Se o Visual Studio não conseguir localizar os arquivos necessários para depurar um módulo no despejo, ele exibirá uma página apropriada (**nenhum binário encontrado**, **nenhum símbolo encontrado**ou **nenhuma fonte encontrada**). Essas páginas fornecem informações detalhadas sobre a causa do problema e fornecem links de ação que podem ajudar a identificar o local correto dos arquivos. Consulte [especificar símbolo (. pdb) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
   ![Voltar ao](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [conteúdo](#BKMK_Contents) superior  
  
## <a name="see-also"></a>Consulte Também  
 [Depuração Just-in-time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Especificar o símbolo (. pdb) e os arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)
