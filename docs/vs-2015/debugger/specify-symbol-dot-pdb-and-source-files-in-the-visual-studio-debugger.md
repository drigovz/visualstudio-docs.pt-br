---
title: Especifique o símbolo (. pdb) e os arquivos de origem no depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4d4b02d512480d96c501758f4cf0f1313158942
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300546"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger"></a>Especificar arquivos de símbolo (.pdb) e de origem no Depurador do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um arquivo de banco de dados do programa (.pdb), também chamado de arquivo de símbolo, mapeia os identificadores que você cria em arquivos de origem para classes, métodos e outro código para os identificadores que são usados em executáveis compilados do seu projeto. O arquivo .pdb também mapeia as instruções no código-fonte para instruções de execução nos arquivos executáveis. O depurador usa essas informações para determinar duas informações principais: o arquivo de origem e o número da linhas que são exibidos no IDE do Visual Studio e o local no executável onde deve ocorrer a interrupção quando você definir um ponto de interrupção. Um arquivo de símbolo também contém o local original dos arquivos de origem e, opcionalmente, o local de um servidor de origem de onde os arquivos de origem podem ser recuperados.

 Quando você depura um projeto no IDE do Visual Studio, o depurador sabe o local padrão para os arquivos. PDB e de origem do seu código. Se desejar depurar o código fora do código-fonte do projeto, como o código do Windows ou de terceiros chamado por seu projeto, você terá que especificar o local do .pdb (e, opcionalmente, os arquivos de origem do código externo) e esses arquivos precisam corresponder exatamente à compilação dos executáveis.

 Antes do Visual Studio 2012, quando você depurava código gerenciado em um dispositivo remoto, precisa colocar os arquivos de símbolo no computador remoto. Esse não é mais o caso. Todos os arquivos de símbolo devem estar localizados no computador local ou em um local especificado na página **ferramentas/opções/depuração/símbolos** .

## <a name="where-the-debugger-searches-for-pdb-files"></a><a name="BKMK_Find_symbol___pdb__files"></a> Onde o depurador pesquisa arquivos. pdb

1. No local especificado dentro da DLL ou do arquivo executável.

     (Por padrão, se você compilou uma DLL ou um arquivo executável no seu computador, o vinculador coloca o caminho completo e o nome do arquivo associado .pdb dentro da DLL ou do arquivo executável. O depurador verifica primeiro se o arquivo de símbolo existe no local especificado dentro da DLL ou do arquivo executável. Isso é útil porque você sempre tem os símbolos disponíveis para o código que compilou no seu computador.)

2. Em arquivos .pdb que podem estar presentes na mesma pasta que a DLL ou o arquivo executável.

3. Em algumas pastas de cache de símbolo locais.

4. Em servidores de símbolo local, na rede ou Internet e nos locais em que são especificados, como o servidor de símbolo Microsoft, se habilitado.

### <a name="why-do-symbol-files-need-to-exactly-match-the-executable-files"></a><a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a> Por que os arquivos de símbolo precisam corresponder exatamente aos arquivos executáveis?
 O depurador carregará apenas um arquivo .pdb para um arquivo executável que corresponde exatamente ao arquivo .pdb criado quando o executável foi compilado (isto é, o .pdb deve ser o original ou uma cópia do arquivo .pdb original). Como o compilador é otimizado para a velocidade de compilação, além de sua tarefa principal de criar um código correto e eficiente, o layout real de um executável pode ser alterado mesmo se o código em si não tiver sido alterado. Para obter mais informações, confira [por que o Visual Studio exige arquivos de símbolo do depurador para corresponder exatamente aos arquivos binários com os quais eles foram criados?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).

### <a name="specify-symbol-locations-and-loading-behavior"></a><a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a> Especificar locais de símbolo e comportamento de carregamento
 Quando você depura um projeto no IDE do VS, o depurador carrega automaticamente os arquivos de símbolo localizados no diretório do projeto. Você pode especificar caminhos de pesquisa alternativos e servidores de símbolo para Microsoft, Windows ou componentes de terceiros em **ferramentas/opções/depuração/símbolos**. Você também pode especificar módulos específicos para os quais deseja que o depurador carregue símbolos automaticamente. E você pode alterar essas configurações manualmente quando estiver depurando ativamente.

1. No Visual Studio, abra a página **ferramentas/opções/depuração/símbolos** .

    ![Ferramentas &#45; opções &#45; página de símbolos de &#45; de depuração](../debugger/media/dbg-tools-options-symbols.png "DBG_Tools_Options_Symbols")

2. Escolha as ferramentas de pasta ![&#47; opções&#47; depuração de&#47;símbolos](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") ícone de pasta ícone. O texto editável aparece na caixa de **locais do arquivo de símbolo (. pdb)** .

3. Digite o caminho do diretório ou a URL do servidor de símbolos ou local do símbolo. O preenchimento de instruções ajuda você a localizar o formato correto.

4. Para melhorar o desempenho de carregamento de símbolos, digite um diretório local no qual os símbolos possam ser copiados por servidores de símbolos na caixa de **cache símbolos nesse diretório** , um diretório local para o qual os símbolos podem ser copiados.

   > [!NOTE]
   > Não coloque o cache de símbolo em uma pasta protegida (como a pasta C:\Windows ou uma de suas subpastas). Use uma pasta de leitura/gravação.

   **Especificar o comportamento de carregamento de símbolos**

   Você pode especificar os arquivos que deseja que sejam carregados automaticamente dos locais da caixa de **locais do arquivo de símbolo (. pdb)** ao iniciar a depuração. Os arquivos de símbolo no diretório do projeto são sempre carregados.

5. Escolha **todos os módulos, a menos** que sejam excluídos para carregar todos os símbolos para todos os módulos, exceto aqueles que você especificar ao escolher o link **especificar módulos excluídos** .

6. Escolha a opção **somente módulos especificados** e escolha **especificar módulos** para listar os módulos dos quais você deseja que os arquivos de símbolos sejam carregados automaticamente. Os arquivos de símbolo para outros módulos são ignorados.

   **Especificar opções adicionais de símbolo**

   Você também pode definir as seguintes opções na página **ferramentas/opções/depuração/símbolos** :

   **Avisar se nenhum símbolo for iniciado (somente nativo)**

   Quando selecionada, exibirá uma caixa de diálogo de aviso quando você tentar depurar um programa para o qual o depurador não tem nenhuma informação simbólica.

   **{1&amp;gt;Carregar exportações de DLL&amp;lt;1}**

   Quando selecionada, carrega as tabelas de exportação de DLL. Informações simbólicas das tabelas de exportação de DLL podem ser úteis se você estiver trabalhando com mensagens do Windows, procedimentos do Windows (WindowProcs), objetos COM, ou marshaling, ou qualquer DLL para a qual você não tem símbolos. A leitura das informações de exportação de DLL gera certa sobrecarga. Desse modo, esse recurso é desativado por padrão.

   Para ver quais símbolos estão disponíveis na tabela de exportação de uma DLL, use `dumpbin /exports`. Os símbolos estão disponíveis para qualquer DLL de 32 bits do sistema. Ao ler a saída `dumpbin /exports`, você pode ver o nome exato da função, incluindo caracteres não alfanuméricos. Isso é útil para definir um ponto de interrupção em uma função. Os nomes de função de tabelas de exportação de DLL podem aparecer truncados em qualquer outro lugar no depurador. As chamadas são listadas na ordem de chamada, com a função atual (a mais profundamente aninhada) na parte superior. Para obter mais informações, confira [dumpbin /exports](https://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).

### <a name="use-symbol-servers-to-find-symbol-files-not-on-your-local-machine"></a><a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a> Usar servidores de símbolos para localizar arquivos de símbolo que não estão em seu computador local
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pode baixar arquivos de símbolo de depuração de servidores de símbolos que implementam o protocolo symsrv. O [Visual Studio Team Foundation Server](https://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6) e as [ferramentas de depuração para Windows](https://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) são duas ferramentas que podem implementar servidores de símbolo. Você especifica os servidores de símbolo a serem usados na caixa de diálogo **Opções** do vs.

 Os servidores de símbolo que você pode usar incluem:

 **Servidores de símbolo públicos da Microsoft**

 Para depurar uma pane que ocorre durante uma chamada a uma DLL do sistema ou a uma biblioteca de terceiros, você normalmente precisará dos arquivos de sistema .pdb, que contêm símbolos de DLLs, EXEs e drivers de dispositivo do Windows. Você pode obter esses símbolos de servidores de símbolo públicos da Microsoft. Os servidores de símbolo públicos da Microsoft fornecem símbolos para sistemas operacionais Windows, além do MDAC, IIS, ISA e [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Para usar os servidores de símbolo da Microsoft, escolha **Opções e configurações** no menu **depurar** e, em seguida, escolha **símbolos**. Selecione **servidores de símbolos da Microsoft**.

 **Servidores de símbolos em uma rede interna ou em seu computador local**

 Sua equipe ou empresa pode criar servidores de símbolo para seus próprios produtos e como um cache para símbolos de fontes externas. Você pode ter um servidor de símbolo no seu próprio computador. Você pode inserir o local dos servidores de símbolo como uma URL ou como um caminho na página **Debugging** / **símbolos** de depuração da caixa de **diálogo de opção**do vs.

 **Servidores de símbolos de terceiros**

 Provedores de terceiros de aplicativos e bibliotecas do Windows podem fornecer acesso ao servidor de símbolo na Internet. Você também insere a URL desses servidores de símbolos na página de símbolos de **depuração** / **Symbols** ,

> [!NOTE]
> Ao usar um servidor de símbolo que não seja um dos servidores de símbolo públicos da Microsoft, verifique se o servidor de símbolo e seu caminho são confiáveis. Como os arquivos de símbolo podem conter códigos executáveis arbitrários, você pode ser exposto às ameaças de segurança.

### <a name="find-and-load-symbols-while-debugging"></a><a name="BKMK_Find_and_load_symbols_while_debugging"></a> Localizar e carregar símbolos durante a depuração
 Sempre que o depurador estiver no modo de interrupção, você poderá carregar símbolos para um módulo que foi excluído anteriormente pelas opções de depurador ou que o compilador não pôde localizar. É possível carregar símbolos usando os menus de atalho das janelas Pilha de Chamadas, Módulos, Locais, Autos e de todas as janelas de Inspeção. Se o depurador for interrompido no código que não tenha arquivos de símbolo ou de origem disponíveis, será exibida uma janela de documento. Aqui você pode localizar informações sobre os arquivos ausentes e executar ações para encontrá-los e carregá-los.

 **Localizar símbolos com as páginas de documento Nenhum Símbolo Carregado**

 Há várias maneiras de o depurador ser interrompido em um código que não tenha símbolos disponíveis:

1. Entrando no código.

2. Sendo interrompido no código a partir de um ponto de interrupção ou exceção.

3. Alternando para outro thread.

4. Alterando o registro de ativação clicando duas vezes em um quadro na janela Pilha de Chamadas.

   Quando um desses eventos ocorre, o depurador exibe a página **nenhum símbolo carregado** para ajudá-lo a localizar e carregar os símbolos necessários.

   ![Página nenhum símbolo carregado](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

- Para alterar os caminhos de pesquisa, escolha um caminho não selecionado ou escolha **novo** e insira um novo caminho. Escolha **carregar** para pesquisar os caminhos novamente e carregar o arquivo de símbolo se ele for encontrado.

- Escolha **procurar e localize**_nome-executável_**...** para substituir qualquer opção de símbolo e repita os caminhos de pesquisa. O arquivo do símbolo será carregado, se for encontrado, ou um Explorador de Arquivos será exibido para que você selecione manualmente o arquivo de símbolo.

- Escolha **alterar configurações de símbolo...** para exibir **Debugging**a  /  página**símbolos** de depuração da caixa de diálogo opções do vs.

- Escolha **Exibir desmontagem** para mostrar a desmontagem em uma nova janela uma vez.

- Para sempre mostrar a desmontagem quando os arquivos de origem ou de símbolo não forem encontrados, escolha o link de **diálogo opções** e selecione **habilitar a depuração de nível de endereço** e **Mostrar desmontagem se a fonte não estiver disponível**.

   ![Opções &#47; depuração &#47; opções de desmontagem gerais](../debugger/media/dbg-options-general-disassembly-checkbox.png "DBG_Options_General_disassembly_checkbox")

  **Alterar opções de símbolo no menu de atalho**

  No modo de interrupção, você pode localizar e carregar símbolos para itens que são exibidos nas janelas Pilha de Chamadas, Módulos, Locais, Autos e todas as janelas de Inspeção. Selecione um item na janela, abra o menu de atalho e escolha uma das seguintes opções:

|Opção|Descrição|
|------------|-----------------|
|**Carregar símbolos**|Tenta carregar símbolos de locais especificados na **Debugging**  /  página**símbolos** de depuração da caixa de diálogo **Opções** . Se o arquivo de símbolo não puder ser encontrado, o Explorador de Arquivos será iniciado para que você possa especificar um novo local de pesquisa.|
|**Informações de Carregamento de Símbolos**|Apresenta informações que mostram o local de um arquivo de símbolo carregado ou os locais que foram pesquisados se o depurador não puder localizar o arquivo.|
|**Configurações de símbolo...**|Abre a **Debugging**  /  página**símbolos** de depuração da caixa de diálogo **Opções** do vs.|
|**Sempre Carregar Automaticamente**|Adiciona o arquivo de símbolo à lista de arquivos que são automaticamente carregados pelo depurador.|

### <a name="set-compiler-options-for-symbol-files"></a><a name="BKMK_Set_compiler_options_for_symbol_files"></a> Definir opções de compilador para arquivos de símbolo
 Quando você cria seu projeto no IDE do VS e usa a configuração de compilação de **depuração** padrão, o C++ e os compiladores gerenciados criam os arquivos de símbolos apropriados para seu código. Também é possível definir opções de compilador na linha de comando para criar arquivos de símbolo.

 **Opções do C++**

 Um arquivo de banco de dados do programa (.pdb) contém informações de depuração e estado do projeto que permite a vinculação incremental de uma configuração de depuração do seu programa. Um arquivo. pdb é criado quando você cria com [/Zi ou/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) (para C/C++).

 No [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , a opção [/FD](https://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a) nomeia o arquivo. pdb criado pelo compilador. Quando você cria um projeto no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usando assistentes, a opção **/FD** é definida para criar um arquivo. pdb chamado *Project*. pdb.

 Se você criar seu aplicativo C/C++ usando um makefile e especificar **/Zi** ou **/Zi** sem **/fd**, você acabará com dois arquivos. PDB:

- VC*x*. pdb, em que *x* representa a versão de Visual C++, por exemplo, VC11. pdb. Esse arquivo armazena todas as informações de depuração para arquivos OBJ individuais e reside no mesmo diretório que o makefile do projeto.

- project.pdb   Esse arquivo armazena todas as informações de depuração para o arquivo .exe. No C/C++, ele reside no subdiretório \debug.

  Cada vez que ele cria um arquivo OBJ, o compilador C/C++ mescla informações de depuração no VC*x*. pdb. As informações inseridas incluem informações de tipo, mas não incluem informações de símbolo como definições de função. Portanto, mesmo que todos os arquivos de origem incluam arquivos de cabeçalho comuns, como \<windows.h> , os TYPEDEFs desses cabeçalhos são armazenados apenas uma vez, em vez de estarem em todos os arquivos obj.

  O vinculador cria project.pdb, que contém informações de depuração para o arquivo EXE do projeto. O arquivo Project. pdb contém informações completas de depuração, incluindo protótipos de função, não apenas as informações de tipo encontradas no VC*x*. pdb. Ambos os arquivos .pdb permitem atualizações incrementais. O vinculador também insere o caminho no arquivo .pdb do arquivo .exe ou .dll que ele cria.

  O depurador do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usa o caminho para o arquivo .pdb no arquivo EXE ou DLL para localizar o arquivo project.pdb. Se o depurador não encontrar o arquivo. pdb nesse local ou se o caminho for inválido (por exemplo, se o projeto foi movido para outro computador), o depurador pesquisará o caminho que contém o EXE, os caminhos de símbolo especificados na caixa de diálogo **Opções** (pasta de**depuração** , nó de **símbolos** ). O depurador não carregará um arquivo .pdb que não corresponde ao executável que está sendo depurado. Se o depurador não conseguir localizar um arquivo. pdb, será exibida uma caixa de diálogo **Localizar símbolos** , que permite pesquisar símbolos ou adicionar outros locais ao caminho de pesquisa.

  **Opções do .NET Framework**

  Um arquivo de banco de dados do programa (.pdb) contém informações de depuração e estado do projeto que permite a vinculação incremental de uma configuração de depuração do seu programa. Um arquivo. pdb é criado quando você cria com **/debug**. Você pode criar aplicativos com **/debug: Full** ou **/debug: pdbonly**. Compilando com **/debug: Full** gera o código depurável. A compilação com **/debug: pdbonly** gera arquivos. pdb, mas não gera o `DebuggableAttribute` que informa ao compilador JIT que as informações de depuração estão disponíveis. Use **/debug: pdbonly** se você quiser gerar arquivos. pdb para uma compilação de versão que não deseja que seja depurável. Para obter mais informações, consulte [/debug (opções do compilador C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969) ou [/debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).

  O depurador do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usa o caminho para o arquivo .pdb no arquivo EXE ou DLL para localizar o arquivo project.pdb. Se o depurador não encontrar o arquivo. pdb nesse local ou se o caminho for inválido, o depurador pesquisará o caminho que contém o EXE e, em seguida, os caminhos de símbolo especificados na caixa de diálogo **Opções** . Esse caminho é geralmente a pasta de **depuração** no nó **símbolos** . O depurador não carregará um arquivo .pdb que não corresponde ao arquivo executável que está sendo depurado. Se o depurador não conseguir localizar um arquivo. pdb, será exibida uma caixa de diálogo **Localizar símbolos** , que permite pesquisar símbolos ou adicionar outros locais ao caminho de pesquisa.

  **Aplicativos Web**

  O arquivo de configuração do aplicativo (Web.config) deve ser definido para o modo de depuração. O modo de depuração faz com que o ASP.NET gere símbolos para arquivos gerados dinamicamente e permite que o depurador se anexe ao aplicativo ASP.NET. O VS define isso automaticamente quando você inicia a depuração, caso você tenha criado o projeto do modelo Projetos Web.

## <a name="find-source-files"></a><a name="BKMK_Find_source_files"></a> Localizar arquivos de origem

### <a name="where-the-debugger-searches-for-source-files"></a><a name="BKMK_Where_the_debugger_searches_for_source_files"></a> Onde o depurador pesquisa arquivos de origem
 O depurador procura arquivos de origem nos seguintes locais:

1. Em arquivos abertos no IDE da instância do Visual Studio que iniciou o depurador.

2. Arquivos na solução que está aberta na instância do Visual Studio.

3. Diretórios que são especificados na página de arquivos de origem de depuração de **Propriedades comuns**  /  **Debug Source Files** nas propriedades da solução. (No **Gerenciador de soluções**, selecione o nó da solução, clique com o botão direito do mouse e selecione **Propriedades**. )

4. Nas informações de origem do .pdb do módulo. Esse pode ser o local do arquivo de origem quando o módulo foi compilado ou pode ser um comando para um servidor de origem.

### <a name="find-and-load-source-files-with-the-no-source--no-symbols-loaded-pages"></a><a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a> Localizar e carregar arquivos de origem com as páginas nenhuma fonte/nenhum símbolo carregado
 Quando o depurador interrompe a execução em um local onde o arquivo de origem não está disponível, ele exibirá as páginas **nenhuma fonte carregada** ou **nenhum símbolo carregado** que pode ajudá-lo a encontrar o arquivo de origem. O **carregamento nenhum** símbolo é exibido quando o depurador não consegue encontrar um arquivo de símbolos (. pdb) para o arquivo executável concluir sua pesquisa. A página Nenhum Símbolo fornece opções para procurar o arquivo. Se o .pdb for encontrado depois que você executar uma das opções e se o depurador puder recuperar o arquivo de origem usando as informações no arquivo de símbolos, a origem será exibida. Caso contrário, uma página **nenhuma fonte carregada** será exibida, descrevendo o problema. A página exibe links de opções que podem executar ações que podem resolver o problema.

### <a name="add-source-file-search-paths-to-a-solution"></a><a name="BKMK_Add_source_file_search_paths_to_a_solution"></a> Adicionar caminhos de pesquisa de arquivo de origem a uma solução
 Você pode especificar uma rede ou diretórios locais para procurar arquivos de origem.

1. Selecione a solução em Gerenciador de Soluções e, em seguida, escolha **Propriedades** no menu de atalho.

2. No nó **Propriedades comuns** , escolha **depurar arquivos de origem**.

3. Clique no ícone ![ferramentas de pasta&#47; opções&#47; depuração&#47;símbolos](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") ícone de pasta. O texto editável é exibido nos **diretórios que contêm a lista de códigos-fonte** .

4. Adicione o caminho que deseja pesquisar.

   Observe que somente o diretório especificado será pesquisado. Você deve adicionar entradas para todos os subdiretórios que deseja pesquisar.

### <a name="use-source-servers"></a><a name="BKMK_Use_source_servers"></a> Usar servidores de origem
 Quando não há nenhum código-fonte no computador local ou o arquivo .pdb não corresponde ao código-fonte, você pode usar o servidor de origem para ajudar na depuração de um aplicativo. O Servidor de Origem recebe solicitações de arquivos e retorna os arquivos reais. O Servidor de Origem é executado por meio de um arquivo DLL chamado srcsrv.dll. O Servidor de Origem lê o arquivo .pdb do aplicativo, que contém ponteiros para o repositório do código-fonte, bem como os comandos usados para recuperar o código-fonte do repositório. Você pode limitar quais comandos terão permissão para execução do arquivo .pdb, listando os comandos permitidos dentro de um arquivo denominado srcsrv.ini, que deve ser colocado no mesmo diretório que srcsrv.dll e devenv.exe.

> [!IMPORTANT]
> Os comandos arbitrários podem ser inseridos no arquivo .pdb do aplicativo, portanto, certifique-se de colocar somente aqueles que você deseja executar no arquivo srcsrv.ini. Qualquer tentativa de executar um comando que não esteja no arquivo srcsvr.ini fará com que uma caixa de diálogo de confirmação seja exibida. Para obter mais informações, consulte [aviso de segurança: o depurador deve executar o comando não confiável](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nenhuma validação é feita em parâmetros do comando. Portanto, tenha cuidado com comandos confiáveis. Por exemplo, se você confiar no cmd.exe, um usuário mal-intencionado pode especificar parâmetros que tornariam o comando perigoso.

 **Para permitir o uso de um Servidor de Origem**

1. Você deve cumprir as medidas de segurança descritas na seção anterior.

2. No menu **Ferramentas**, escolha **Opções**.

     A caixa de diálogo **Opções** é exibida.

3. No nó **depuração** , escolha **geral**.

4. Marque a caixa de seleção **habilitar suporte ao servidor de origem** .

     ![Habilitar opções do servidor de origem](../debugger/media/dbg-options-general-enablesrcsrvr-checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

5. (Opcional) Escolha as opções filho que você deseja.

     Observe que ambos **permitem que o servidor de origem para assemblies de confiança parcial (somente gerenciados)** e **sempre execute comandos de servidor de origem não confiáveis sem avisar** pode aumentar os riscos de segurança discutidos acima.

## <a name="see-also"></a>Consulte Também
 [Carregamento de símbolo remoto do .NET alterações no Visual Studio 2012 e 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
