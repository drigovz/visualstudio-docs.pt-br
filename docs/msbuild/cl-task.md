---
title: Tarefa CL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), CL task
- CL task (MSBuild (C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb0e1feee1f7e1d271dd436a1879731354cbd8bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78865330"
---
# <a name="cl-task"></a>tarefa CL

Encapsula a ferramenta de compilador do Microsoft C++, *cl.exe*. O compilador produz arquivos executáveis (*. exe*), arquivos de biblioteca de vínculo dinâmico (*. dll*) ou arquivos de módulo de código (*. netmodule*). Para obter mais informações, consulte [Opções do compilador](/cpp/build/reference/compiler-options) e usar o [MSBuild na linha de comando](/cpp/build/msbuild-visual-cpp) e [usar o conjunto de ferramentas do Microsoft C++ na linha de comando](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parâmetros

 A lista a seguir descreve os parâmetros da tarefa **CL**. A maioria dos parâmetros de tarefa e alguns conjuntos de parâmetros correspondem a uma opção de linha de comando.

- **AdditionalIncludeDirectories**

   Parâmetro String[] opcional.

   Adiciona um diretório à lista de diretórios que são pesquisados para arquivos de inclusão.

   Para obter mais informações, consulte [/i (diretórios de inclusão adicionais)](/cpp/build/reference/i-additional-include-directories).

- **AdditionalOptions**

   Parâmetro String opcional.

   Uma lista de opções de linha de comando. Por exemplo, "/ \<option1>  / \<option2>  / \<option#> ". Use esse parâmetro para especificar opções de linha de comando não representadas por nenhum outro parâmetro da tarefa.

   Para obter mais informações, consulte [Opções do compilador](/cpp/build/reference/compiler-options).

- **AdditionalUsingDirectories**

   Parâmetro String[] opcional.

   Especifica um diretório em que o compilador pesquisará para resolver referências de arquivo passadas para diretiva **#using**.

   Para obter mais informações, consulte [/ai (especificar diretórios de metadados)](/cpp/build/reference/ai-specify-metadata-directories).

- **AlwaysAppend**

   Parâmetro String opcional.

   Uma cadeia de caracteres sempre é emitida na linha de comando. Seu valor padrão é "**/c**".

- **AssemblerListingLocation**

   Cria um arquivo de listagem que contém o código do assembly.

   Para obter mais informações, consulte a opção **/FA** em [/FA,/FA (arquivo de listagem)](/cpp/build/reference/fa-fa-listing-file).

- **AssemblerOutput**

   Parâmetro String opcional.

   Cria um arquivo de listagem que contém o código do assembly.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **Nolistando** - *\<none>*

  - **AssemblyCode**  -  **/FA**

  - **AssemblyAndMachineCode**  -  **/Fac**

  - **AssemblyAndSourceCode**  -  **/FAS**

  - **Todos**  -  **/FACS**

    Para obter mais informações, consulte as opções **/FA**, **/fac**, **/FAS**e **/FACS** em [/FA,/FA (arquivo de listagem)](/cpp/build/reference/fa-fa-listing-file).

- **BasicRuntimeChecks**

   Parâmetro String opcional.

   Habilita e desabilita o recurso de verificações de erro em tempo de execução, em conjunto com o pragma [runtime_checks](/cpp/preprocessor/runtime-checks).

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **Os** -                          *\<none>*

  - **StackFrameRuntimeCheck**  -  **/RTCs**

  - **UninitializedLocalUsageCheck**  -  **/RTCu**

  - **EnableFastChecks**  -                           **/RTC1**

    Para obter mais informações, consulte [/RTC (verificações de erro em tempo de execução)](/cpp/build/reference/rtc-run-time-error-checks).

- **BrowseInformation**

   Parâmetro Boolean opcional.

   Se `true`, criará um arquivo de informações de procura.

   Para obter mais informações, consulte a opção **/fr** em [/fr,/fr (Create. sbr File)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BrowseInformationFile**

   Parâmetro String opcional.

   Especifica um nome de arquivo para o arquivo de informações de procura.

   Para obter mais informações, consulte o parâmetro **BrowseInformation** nesta tabela e também consulte [/fr,/fr (Create. sbr File)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BufferSecurityCheck**

   Parâmetro Boolean opcional.

   Se `true`, detectará alguns estouros de buffer que substituem o endereço de retorno, uma técnica comum para explorar o código que não impõe restrições de tamanho do buffer.

   Para obter mais informações, confira [/GS (Verificação de segurança do buffer)](/cpp/build/reference/gs-buffer-security-check).

- **BuildingInIDE**

   Parâmetro Boolean opcional.

   Se `true`, indicará que **MSBuild** é invocado pelo IDE. Caso contrário, **MSBuild** será invocado na linha de comando.

- **CallingConvention**

   Parâmetro String opcional.

   Especifica a convenção de chamada, que determina a ordem na qual os argumentos de função são colocados na pilha, se a função do chamador ou a função chamada remove os argumentos da pilha no final da chamada e a convenção de decoração de nome que o compilador usa para identificar funções individuais.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **Cdecl**  -  **/Gd**

  - **FastCall**  -                           **/Gr**

  - **Stdcall**  -                           **/Gz**

    Para obter mais informações, consulte [/gd,/GR,/GV,/gz (Convenção de chamada)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **CompileAs**

   Parâmetro String opcional.

   Especifica se o arquivo de entrada deve ser compilado como um arquivo de origem C ou C++.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **Os** - *\<none>*

  - **CompileAsC**  -  **/TC**

  - **CompileAsCpp**  -  **/TP**

    Para obter mais informações, consulte [/TC,/TP,/TC,/TP (especificar tipo de arquivo de origem)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).

- **CompileAsManaged**

   Parâmetro String opcional.

   Permite que aplicativos e componentes usem recursos do CLR (Common Language Runtime).

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **for** - *\<none>*

  - **verdadeiro**  -  **/CLR**

  - **Puro**  -  **/CLR: Pure**

  - **Seguro**  -  **/CLR: safe**

  - **OldSyntax**  -  **/CLR: oldSyntax**

    Para obter mais informações, confira [/clr (Compilação do Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).

- **CreateHotpatchableImage**

   Parâmetro Boolean opcional.

   Se `true`, informará ao compilador para preparar uma imagem para *aplicação de patch sob demanda*. Esse parâmetro garante que a primeira instrução de cada função tenha dois bytes, o que é necessário para aplicação de patch sob demanda.

   Para obter mais informações, consulte [/hotpatch (criar imagem Hotpatchable)](/cpp/build/reference/hotpatch-create-hotpatchable-image).

- **DebugInformationFormat**

   Parâmetro String opcional.

   Seleciona o tipo de informações de depuração criadas para o seu programa e se essas informações são mantidas em arquivos de objeto (*. obj*) ou em um banco de dados de programa (PDB).

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **RAISEERROR**  -  **/Z7**

  - **ProgramDatabase**  -  **/Zi**

  - **EditAndContinue**  -  **/Zi**

    Para obter mais informações, consulte [/Z7,/Zi,/Zi (formato de informações de depuração)](/cpp/build/reference/z7-zi-zi-debug-information-format).

- **DisableLanguageExtensions**

   Parâmetro Boolean opcional.

   Se **true**, dirá ao compilador para emitir um erro para construções de linguagem que não sejam compatíveis com ANSI C ou ANSI C++.

   Para obter mais informações, consulte a opção **/za** em [/za,/Ze (desabilitar extensões de linguagem)](/cpp/build/reference/za-ze-disable-language-extensions).

- **DisableSpecificWarnings**

   Parâmetro String[] opcional.

   Desabilita os números de aviso especificados em uma lista delimitada por ponto e vírgula.

   Para obter mais informações, consulte a `/wd` opção em [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/wo,/WV,/WX (nível de aviso)](/cpp/build/reference/compiler-option-warning-level).

- **EnableEnhancedInstructionSet**

   Parâmetro String opcional.

   Especifica a arquitetura para a geração de código que usa as instruções SSE (Streaming SIMD Extensions) e SSE2 (Streaming SIMD Extensions 2).

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **StreamingSIMDExtensions**  -  **/Arch: SSE**

  - **StreamingSIMDExtensions2**  -  **/Arch: SSE2**

    Para obter mais informações, consulte [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimizations**

   Parâmetro Boolean opcional.

   Se `true`, dê suporte a segurança de fibra para dados alocados usando armazenamento local de thread estático, ou seja, dados alocados usando `__declspec(thread)`.

   Para obter mais informações, consulte [/gt (suporte ao armazenamento local de thread de fibra segura)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).

- **EnablePREfast**

   Parâmetro Boolean opcional.

   Se `true`, habilitará análise de código.

   Para obter mais informações, consulte [/Analyze (análise de código)](/cpp/build/reference/analyze-code-analysis).

- **ErrorReporting**

   Parâmetro String opcional.

   Permite que você forneça informações de ICE (erro interno do compilador) diretamente à Microsoft. Por padrão, a configuração em compilações do IDE é **Aviso** e a configuração em compilações de linha de comando é **Fila**.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **Nenhum**  -  **/errorreport: None**

  - **Aviso**  -  **/errorreport: prompt**

  - **Fila**  -  **/errorreport: Queue**

  - **Enviar**  -  **/errorreport: send**

    Para obter mais informações, consulte [/errorReport (relatar erros de compilador interno)](/cpp/build/reference/errorreport-report-internal-compiler-errors).

- **ExceptionHandling**

   Parâmetro String opcional.

   Especifica o modelo de tratamento de exceções a ser utilizado pelo compilador.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **for** - *\<none>*

  - **Async**  -  **/EHA**

  - **Sincronizar**  -  **/EHsc**

  - **SyncCThrow**  -  **O/EHS**

    Para obter mais informações, consulte [/eh (modelo de tratamento de exceção)](/cpp/build/reference/eh-exception-handling-model).

- **ExpandAttributedSource**

   Parâmetro Boolean opcional.

   Se `true`, criará um arquivo de listagem com atributos expandidos injetados no arquivo de origem.

   Para obter mais informações, consulte [/FX (mesclar código injetado)](/cpp/build/reference/fx-merge-injected-code).

- **FavorSizeOrSpeed**

   Parâmetro String opcional.

   Especifica se tamanho ou velocidade do código deve ser favorecido.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **Delas** - *\<none>*

  - **Tamanho**  -  **/Os**

  - **Velocidade**  -  **/OT**

    Para obter mais informações, consulte [/os,/OT (favorecer código pequeno, favorecer código rápido)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **FloatingPointExceptions**

   Parâmetro Boolean opcional.

   Se `true`, habilitará o modelo de exceção de ponto flutuante confiável. As exceções serão geradas imediatamente depois de serem disparadas.

   Para obter mais informações, consulte a opção/**fp: except** no [/FP (especificar comportamento de ponto flutuante)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **FloatingPointModel**

   Parâmetro String opcional.

   Define o modelo de ponto flutuante.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **Preciso**  -  **/fp: preciso**

  - **Estrito**  -  **/fp: estrito**

  - **Rápida**  -  **/fp: rápido**

    Para obter mais informações, consulte [/FP (especificar comportamento de ponto flutuante)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **ForceConformanceInForLoopScope**

   Parâmetro Boolean opcional.

   Se `true`, implementará o comportamento padrão do C++ em loops [for](/cpp/cpp/for-statement-cpp) que usem extensões da Microsoft ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)).

   Para obter mais informações, consulte [/Zc: forScope (forçar conformidade no escopo do loop for)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).

- **ForcedIncludeFiles**

   Parâmetro `String[]` opcional.

   Faz o pré-processador processar um ou mais arquivos de cabeçalho especificados.

   Para obter mais informações, consulte [/Fi (arquivo de inclusão forçada de nome)](/cpp/build/reference/fi-name-forced-include-file).

- **ForcedUsingFiles**

   Parâmetro opcional de **cadeia de caracteres []** .

   Faz o pré-processador processar um ou mais arquivos **#using** especificados.

   Para obter mais informações, consulte [/Fu (nome forçado #using arquivo)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **FunctionLevelLinking**

   Parâmetro `Boolean` opcional.

   Se `true`, permitirá que o compilador empacote funções individuais na forma de funções empacotadas (COMDATs).

   Para obter mais informações, consulte [/GY (habilitar vinculação no nível de função)](/cpp/build/reference/gy-enable-function-level-linking).

- **GenerateXMLDocumentationFiles**

   Parâmetro `Boolean` opcional.

   Se `true` , faz com que o compilador processe comentários de documentação em arquivos de código-fonte e crie um arquivo *. xdc* para cada arquivo de código-fonte que tenha comentários de documentação.

   Para obter mais informações, consulte [/Doc (comentários de documentação do processo) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Consulte também o parâmetro **XMLDocumentationFileName** nesta tabela.

- **IgnoreStandardIncludePath**

   Parâmetro `Boolean` opcional.

   Se `true`, evitará que o compilador pesquise os arquivos de inclusão em diretórios especificados nas variáveis de ambiente PATH e INCLUDE.

   Para obter mais informações, consulte [/x (ignorar caminhos de inclusão padrão)](/cpp/build/reference/x-ignore-standard-include-paths).

- **InlineFunctionExpansion**

   Parâmetro de **cadeia de caracteres** opcional.

   Especifica o nível de expansão de função embutida para o build.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **Os** - *\<none>*

  - **Desabilitado**  -  **/Ob0**

  - **OnlyExplicitInline**  -  **/Ob1**

  - **AnySuitable**  -  **/Ob2**

    Para obter mais informações, consulte [/Ob (expansão de função embutida)](/cpp/build/reference/ob-inline-function-expansion).

- **IntrinsicFunctions**

   Parâmetro `Boolean` opcional.

   Se `true`, substituirá algumas chamadas de função com formas da função intrínsecas ou especiais de outra maneira que ajudem o aplicativo a ser executado mais rapidamente.

   Para obter mais informações, consulte [/Oi (gerar funções intrínsecas)](/cpp/build/reference/oi-generate-intrinsic-functions).

- **MinimalRebuild**

   Parâmetro `Boolean` opcional.

   Se `true`, habilitará recompilação mínima, que determina se os arquivos de origem C++ que incluem definições de classe C++ alteradas (armazenadas nos arquivos de cabeçalho (.h)) devem ser recompilados.

   Para obter mais informações, consulte [/GM (habilitar recompilação mínima)](/cpp/build/reference/gm-enable-minimal-rebuild).

- **MultiProcessorCompilation**

   Parâmetro `Boolean` opcional.

   Se `true`, use vários processadores para compilar. Esse parâmetro cria um processo para cada processador efetivo no seu computador.

   Para obter mais informações, consulte [/MP (criar com vários processos)](/cpp/build/reference/mp-build-with-multiple-processes). Consulte também o parâmetro **ProcessorNumber** nesta tabela.

- **ObjectFileName**

   Parâmetro de **cadeia de caracteres** opcional.

   Especifica um nome de arquivo de objeto (.obj) ou diretório a ser usado no lugar do padrão.

   Para obter mais informações, confira [/Fo (Nome do arquivo-objeto)](/cpp/build/reference/fo-object-file-name).

- **ObjectFiles**

   Parâmetro opcional de **cadeia de caracteres []** .

   Uma lista de arquivos de objeto.

- **OmitDefaultLibName**

   Parâmetro `Boolean` opcional.

   Se `true` , omite o nome padrão da biblioteca de tempo de execução do C do arquivo de objeto (*. obj*). Por padrão, o compilador coloca o nome da biblioteca no arquivo *. obj* para direcionar o vinculador para a biblioteca correta.

   Para obter mais informações, consulte [/zl (omitir nome de biblioteca padrão)](/cpp/build/reference/zl-omit-default-library-name).

- **OmitFramePointers**

   Parâmetro `Boolean` opcional.

   Se `true`, suprimirá a criação de ponteiros de quadro na pilha de chamadas.

   Para obter mais informações, consulte [/Oy (omissão do ponteiro de quadro)](/cpp/build/reference/oy-frame-pointer-omission).

- **OpenMPSupport**

   Parâmetro `Boolean` opcional.

   Se `true`, fará o compilador processar cláusulas e diretivas OpenMP.

   Para obter mais informações, consulte [/OpenMP (habilitar suporte a openmp 2,0)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **Otimização**

   Parâmetro de **cadeia de caracteres** opcional.

   Especifica várias otimizações de código para velocidade e tamanho.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **Desabilitado**  -  **/OD**

  - **MinSpace**  -  **/O1**

  - **MaxSpeed**  -  **/O2**

  - **Completo**  -  **/Ox**

    Para obter mais informações, confira [Opções de /S (Otimizar código)](/cpp/build/reference/o-options-optimize-code).

- **PrecompiledHeader**

   Parâmetro de **cadeia de caracteres** opcional.

   Crie ou use um arquivo de cabeçalho pré-compilado (*. pch*) durante a compilação.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **Não usando** - *\<none>*

  - **Criar**  -  **/YC**

  - **Usar**  -  o **/Yu**

    Para obter mais informações, consulte [/Yc (criar arquivo de cabeçalho pré-compilado)](/cpp/build/reference/yc-create-precompiled-header-file) e [/Yu (usar arquivo de cabeçalho pré-compilado)](/cpp/build/reference/yu-use-precompiled-header-file). Consulte também os parâmetros **PrecompiledHeaderFile** e **PrecompiledHeaderOutputFile** nessa tabela.

- **PrecompiledHeaderFile**

   Parâmetro de **cadeia de caracteres** opcional.

   Especifica um nome de arquivo de cabeçalho pré-compilado para criar ou usar.

   Para obter mais informações, consulte [/Yc (criar arquivo de cabeçalho pré-compilado)](/cpp/build/reference/yc-create-precompiled-header-file) e [/Yu (usar arquivo de cabeçalho pré-compilado)](/cpp/build/reference/yu-use-precompiled-header-file).

- **PrecompiledHeaderOutputFile**

   Parâmetro de **cadeia de caracteres** opcional.

   Especifica um nome de caminho para um cabeçalho pré-compilado em vez de usar o nome do caminho padrão.

   Para obter mais informações, consulte [/FP (arquivo Name. pch)](/cpp/build/reference/fp-name-dot-pch-file).

- **PreprocessKeepComments**

   Parâmetro `Boolean` opcional.

   Se `true`, preservará comentários durante o pré-processamento.

   Para obter mais informações, consulte [/c (preservar comentários durante o pré-processamento)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **PreprocessorDefinitions**

   Parâmetro `String[]` opcional.

   Define um símbolo de pré-processamento para seu arquivo de origem.

   Para obter mais informações, consulte [/d (definições de pré-processador)](/cpp/build/reference/d-preprocessor-definitions).

- **PreprocessOutput**

   Parâmetro `ITaskItem[]` opcional.

   Define uma matriz de itens de saída do pré-processador que podem ser consumidos e emitidos por tarefas.

- **PreprocessOutputPath**

   Parâmetro `String` opcional.

   Especifica o nome do arquivo de saída para o qual o parâmetro **PreprocessToFile** grava a saída pré-processada.

   Para obter mais informações, consulte [/Fi (nome do arquivo de saída de pré-processamento)](/cpp/build/reference/fi-preprocess-output-file-name).

- **PreprocessSuppressLineNumbers**

   Parâmetro `Boolean` opcional.

   Se `true`, pré-processará arquivos de origem em C e C++ e copiará os arquivos pré-processados para o dispositivo de saída padrão.

   Para obter mais informações, consulte [/EP (pré-processar para stdout sem #line diretivas)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **PreprocessToFile**

   Parâmetro `Boolean` opcional.

   Se `true`, pré-processará arquivos de origem em C e C++ e gravará a saída pré-processada em um arquivo.

   Para obter mais informações, consulte [/p (pré-processar para um arquivo)](/cpp/build/reference/p-preprocess-to-a-file).

- **ProcessorNumber**

   Parâmetro `Integer` opcional.

   Especifica o número máximo de processadores a serem usados em uma compilação multiprocessador. Use esse parâmetro em combinação com o parâmetro **MultiProcessorCompilation**.

- **ProgramDataBaseFileName**

   Parâmetro `String` opcional.

   Especifica um nome de arquivo para o arquivo PDB (banco de dados do programa).

   Para obter mais informações, consulte [/FD (nome do arquivo de banco de dados do programa)](/cpp/build/reference/fd-program-database-file-name).

- **RuntimeLibrary**

   Parâmetro `String` opcional.

   Indica se um módulo com multithread é uma DLL e seleciona versões de varejo ou de depuração da biblioteca em tempo de execução.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **Multithread**  -  **/MT**

  - **MultiThreadedDebug**  -  **/MTD**

  - **MultiThreadedDLL**  -  **/MD**

  - **MultiThreadedDebugDLL**  -  **/MDD**

    Para obter mais informações, consulte [/MD,/MT,/LD (usar biblioteca de tempo de execução)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **RuntimeTypeInfo**

   Parâmetro `Boolean` opcional.

   Se `true`, adicionará código para verificar os tipos de objeto C++ no tempo de execução (informações de tipo de tempo de execução).

   Para obter mais informações, consulte [/gr (habilitar informações de tipo de tempo de execução)](/cpp/build/reference/gr-enable-run-time-type-information).

- **ShowIncludes**

   Parâmetro `Boolean` opcional.

   Se `true`, fará o compilador gerar uma lista dos arquivos de inclusão.

   Para obter mais informações, consulte [/showIncludes (listar arquivos de inclusão)](/cpp/build/reference/showincludes-list-include-files).

- **SmallerTypeCheck**

   Parâmetro `Boolean` opcional.

   Se `true`, relatará um erro em tempo de execução se um valor for atribuído a um tipo de dados menor e provocará perda de dados.

   Para obter mais informações, consulte a opção **/RTCc** em [/RTC (verificações de erro em tempo de execução)](/cpp/build/reference/rtc-run-time-error-checks).

- **Fontes**

   Parâmetro `ITaskItem[]` obrigatório.

   Especifica uma lista de arquivos de origem separados por espaços.

- **StringPooling**

   Parâmetro `Boolean` opcional.

   Se `true`, permitirá que o compilador crie uma cópia de cadeias de caracteres idênticas na imagem do programa.

   Para obter mais informações, consulte [/GF (eliminar cadeias de caracteres duplicadas)](/cpp/build/reference/gf-eliminate-duplicate-strings).

- **StructMemberAlignment**

   Parâmetro `String` opcional.

   Especifica o alinhamento de byte para todos os membros em uma estrutura.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **Padrão**  -  **/Zp1**

  - **1Byte**  -  **/Zp1**

  - **2Bytes**  -  **/Zp2**

  - **4Bytes**  -  **/Zp4**

  - **8Bytes**  -  **/Zp8**

  - **16Bytes**  -  **/Zp16**

    Para obter mais informações, consulte [/ZP (alinhamento de membro de struct)](/cpp/build/reference/zp-struct-member-alignment).

- **SuppressStartupBanner**

   Parâmetro `Boolean` opcional.

   Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.

   Para obter mais informações, consulte [/nologo (suprimir a faixa de inicialização) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **TrackerLogDirectory**

   Parâmetro `String` opcional.

   Especifica o diretório intermediário em que os logs de rastreamento para essa tarefa são armazenados.

   Para obter mais informações, consulte os parâmetros **TLogReadFiles** e **TLogWriteFiles** nesta tabela.

- **TreatSpecificWarningsAsErrors**

   Parâmetro opcional de **cadeia de caracteres []** .

   Trata a lista especificada de avisos do compilador como erros.

   Para obter mais informações, consulte a opção **/We** `n` em [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/wo,/WV,/WX (nível de aviso)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWarningAsError**

   Parâmetro `Boolean` opcional.

   Se `true`, tratará todos os avisos do compilador como erros.

   Para obter mais informações, consulte a opção **/WX** em [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/wo,/WV,/WX (nível de aviso)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWChar_tAsBuiltInType**

   Parâmetro `Boolean` opcional.

   Se `true`, trate o tipo `wchar_t` como um tipo nativo.

   Para obter mais informações, confira [/Zc:wchar_t (wchar_t é o tipo nativo)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).

- **UndefineAllPreprocessorDefinitions**

   Parâmetro `Boolean` opcional.

   Se `true`, cancelará a definição de símbolos específicos da Microsoft que o compilador definir.

   Para obter mais informações, consulte a opção **/u** em [/u,/u (undefine Symbols)](/cpp/build/reference/u-u-undefine-symbols).

- **UndefinePreprocessorDefinitions**

   Parâmetro `String[]` opcional.

   Especifica uma lista de um ou mais símbolos de pré-processador a excluir.

   Para obter mais informações, consulte a opção **/u** em [/u,/u (undefine Symbols)](/cpp/build/reference/u-u-undefine-symbols).

- **UseFullPaths**

   Parâmetro `Boolean` opcional.

   Se `true`, exibirá o caminho completo dos arquivos de código-fonte passados para o compilador no diagnóstico.

   Para obter mais informações, consulte [/FC (caminho completo do arquivo de código-fonte no diagnóstico)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **UseUnicodeForAssemblerListing**

   Parâmetro `Boolean` opcional.

   Se `true`, fará o arquivo de saída ser criado em formato UTF-8.

   Para obter mais informações, consulte a opção **/FAU** em [/FA,/FA (arquivo de listagem)](/cpp/build/reference/fa-fa-listing-file).

- **WarningLevel**

   Parâmetro `String` opcional.

   Especifica o nível mais alto de aviso que deverá ser gerado pelo compilador.

   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.

  - **TurnOffAllWarnings**  -  **/W0**

  - **Level1**  -  **/W1**

  - **Level2**  -  **/W2**

  - **Level3**  -  **/W3**

  - **Level4**  -  **/W4**

  - **EnableAllWarnings**  -  **/Wall**

    Para obter mais informações, consulte a opção **/w**_n_ em [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/wo,/WV,/WX (nível de aviso)](/cpp/build/reference/compiler-option-warning-level).

- **WholeProgramOptimization**

   Parâmetro `Boolean` opcional.

   Se `true`, habilitará a otimização de todo o programa.

   Para obter mais informações, consulte [/GL (otimização do programa inteiro)](/cpp/build/reference/gl-whole-program-optimization).

- **XMLDocumentationFileName**

   Parâmetro `String` opcional.

   Especifica o nome dos arquivos de documentação XML gerados. Esse parâmetro pode ser um nome de arquivo ou de diretório.

   Para obter mais informações, consulte o `name` argumento em [/Doc (comentários de documentação do processo) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Consulte também o parâmetro **GenerateXMLDocumentationFiles** nesta tabela.

- **MinimalRebuildFromTracking**

   Parâmetro `Boolean` opcional.

   Se `true`, um build incremental controlada será executada; se `false`, será executada uma recompilação.

- **TLogReadFiles**

   Parâmetro `ITaskItem[]` opcional.

   Especifica uma matriz de itens que representam os *logs de acompanhamento do arquivo de leitura*.

   Um log de controle de arquivo de leitura (*. tlog*) contém os nomes dos arquivos de entrada que são lidos por uma tarefa e é usado pelo sistema de compilação do projeto para dar suporte a compilações incrementais. Para obter mais informações, consulte os parâmetros **TrackerLogDirectory** e **TrackFileAccess** nesta tabela.

- **TLogWriteFiles**

   Parâmetro `ITaskItem[]` opcional.

   Especifica uma matriz de itens que representam os *logs de acompanhamento do arquivo de gravação*.

   Um log de rastreamento de arquivo de gravação (*. tlog*) contém os nomes dos arquivos de saída que são gravados por uma tarefa e é usado pelo sistema de compilação do projeto para dar suporte a compilações incrementais. Para obter mais informações, consulte os parâmetros **TrackerLogDirectory** e **TrackFileAccess** nesta tabela.

- **TrackFileAccess**

   Parâmetro `Boolean` opcional.

   Se `true`, controlará os padrões de acesso de arquivo.

   Para obter mais informações, consulte os parâmetros **TLogReadFiles** e **TLogWriteFiles** nesta tabela.

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
