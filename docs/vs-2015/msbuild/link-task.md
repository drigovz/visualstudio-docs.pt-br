---
title: Tarefa Link | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), Link task
- Link task (MSBuild (Visual C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 930cec012bfda49c61116ada2ba6df10c3a48f51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850994"
---
# <a name="link-task"></a>Tarefa Link
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Encapsula a ferramenta de vinculador do Visual C++, link.exe. A ferramenta de vinculador vincula arquivos de objeto e bibliotecas de formato COFF (Common Object File Format) para criar um arquivo executável (.exe) ou uma DLL (biblioteca de vínculo dinâmico). Para obter mais informações, consulte [Opções do vinculador](https://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **Link**. A maioria dos parâmetros de tarefa e alguns conjuntos de parâmetros correspondem a uma opção de linha de comando.  
  
- **AdditionalDependencies**  
  
   Parâmetro opcional de **cadeia de caracteres []** .  
  
   Especifica uma lista de arquivos de entrada para adicionar ao comando.  
  
   Para obter mais informações, consulte [vincular arquivos de entrada](https://msdn.microsoft.com/library/bb26fcc5-509a-4620-bc3e-b6c6e603a412).  
  
- **AdditionalLibraryDirectories**  
  
   Parâmetro opcional de **cadeia de caracteres []** .  
  
   Substitui o caminho da biblioteca de ambiente. Especifique um nome de diretório.  
  
   Para obter mais informações, consulte [/LIBPATH (Libpath Adicional)](https://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba).  
  
- **AdditionalManifestDependencies**  
  
   Parâmetro opcional de **cadeia de caracteres []** .  
  
   Especifica atributos que serão colocados na seção `dependency` do arquivo de manifesto.  
  
   Para obter mais informações, consulte [/MANIFESTDEPENDENCY (especificar dependências de manifesto)](https://msdn.microsoft.com/library/e4b68313-33a2-4c3e-908e-ac2b9f7d6a73). Consulte também os "Arquivos de Configuração do Distribuidor" no site do [MSDN](https://msdn.microsoft.com/).  
  
- **AdditionalOptions**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Uma lista de opções de vinculador, conforme especificado na linha de comando. Por exemplo, **"**_/option1/option2/Option #_". Use esse parâmetro para especificar opções de vinculador que não são representadas por qualquer outro parâmetro de tarefa **Link**.  
  
   Para obter mais informações, consulte [Opções do vinculador](https://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
- **AddModuleNamesToAssembly**  
  
   Parâmetro opcional de **cadeia de caracteres []** .  
  
   Adiciona uma referência de módulo a um assembly.  
  
   Para obter mais informações, consulte [/ASSEMBLYMODULE (adicionar um módulo MSIL ao assembly)](https://msdn.microsoft.com/library/67357da8-e4b6-49fd-932c-329a5777f143).  
  
- **AllowIsolation**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, fará com que o sistema operacional realize pesquisas de manifesto e carregamentos. Se `false`, indicará que as DLLs serão carregadas como se não houvesse nenhum manifesto.  
  
   Para obter mais informações, consulte [/ALLOWISOLATION (manifesto Lookup)](https://msdn.microsoft.com/library/6d41851e-b3c1-4bdf-beaa-031773089d6f).  
  
- **AssemblyDebug**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, emitirá o atributo **DebuggableAttribute** junto com o acompanhamento de informações de depuração e desabilitará otimizações JIT. Se `false`, emitirá o atributo **DebuggableAttribute**, mas desabilitará o acompanhamento de informações de depuração e as otimizações JIT.  
  
   Para obter mais informações, consulte [/ASSEMBLYDEBUG (Adicionar DebuggableAttribute)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).  
  
- **AssemblyLinkResource**  
  
   Parâmetro opcional de **cadeia de caracteres []** .  
  
   Cria um link para um recurso do .NET Framework no arquivo de saída; o arquivo de recurso não é colocado no arquivo de saída. Especifique o nome do recurso.  
  
   Para obter mais informações, consulte [/ASSEMBLYLINKRESOURCE (link para .NET Framework recurso)](https://msdn.microsoft.com/library/8b6ad184-1b33-47a4-8513-4803cf915b64).  
  
- **AttributeFileTracking**  
  
   Parâmetro **Booliano** implícito.  
  
   Habilita um acompanhamento de arquivos mais profundo a fim de capturar o comportamento incremental do link. Sempre retorna `true`.  
  
- **BaseAddress**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Define um endereço básico para o programa ou DLL que está sendo criado. Especifique `{address[,size] | @filename,key}`.  
  
   Para obter mais informações, consulte [/base (endereço base)](https://msdn.microsoft.com/library/00b9f6fe-0bd2-4772-a69c-7365eb199069).  
  
- **BuildingInIDE**  
  
   Parâmetro **booliano** opcional.  
  
   Se for true, indica que o MSBuild é chamado do IDE. Caso contrário, indica que o MSBuild é chamado da linha de comando.  
  
   Esse parâmetro não tem nenhuma opção de vinculador equivalente.  
  
- **CLRImageType**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Define o tipo de uma imagem CLR (Common Language Runtime).  
  
   Especifique um dos valores a seguir, cada um correspondente a uma opção de vinculador.  
  
  - **Os** - *\<none>*  
  
  - **ForceIJWImage**  -  **/CLRIMAGETYPE: IJW**  
  
  - **ForcePureILImage**  -  **/CLRIMAGETYPE: puro**  
  
  - **ForceSafeILImage**  -  **/CLRIMAGETYPE: seguro**  
  
    Para obter mais informações, consulte [/CLRIMAGETYPE (especificar o tipo de imagem CLR)](https://msdn.microsoft.com/library/04c60ee6-9dd7-4391-bc03-6926ad0fa116).  
  
- **CLRSupportLastError**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Preserva o código de erro mais recente de funções chamadas por meio do mecanismo P/Invoke.  
  
   Especifique um dos valores a seguir, cada um correspondente a uma opção de vinculador.  
  
  - **Habilitado**  -  **/CLRSupportLastError**  
  
  - **Desabilitado**  -  **/CLRSupportLastError: não**  
  
  - **SystemDlls**  -  **/CLRSupportLastError: SYSTEMDLL**  
  
    Para obter mais informações, consulte [/CLRSUPPORTLASTERROR (preservar o último código de erro para chamadas do PInvoke)](https://msdn.microsoft.com/library/b7057990-4154-4b1d-9fc9-6236f7be7575).  
  
- **CLRThreadAttribute**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica explicitamente o atributo de thread para o ponto de entrada de seu programa CLR.  
  
   Especifique um dos valores a seguir, cada um correspondente a uma opção de vinculador.  
  
  - **DefaultThreadingAttribute**  -  **/CLRTHREADATTRIBUTE: nenhum**  
  
  - **MTAThreadingAttribute**  -  **/CLRTHREADATTRIBUTE: MTA**  
  
  - **STAThreadingAttribute**  -  **/CLRTHREADATTRIBUTE: STA**  
  
    Para obter mais informações, consulte [/CLRTHREADATTRIBUTE (Set CLR thread Attribute)](https://msdn.microsoft.com/library/4907e9ef-5031-446c-aecf-0a0b32fae1e8).  
  
- **CLRUnmanagedCodeCheck**  
  
   Parâmetro **booliano** opcional.  
  
   Especifica se o vinculador aplicará o atributo **SuppressUnmanagedCodeSecurityAttribute** às chamadas P/Invoke geradas pelo vinculador do código gerenciado nas DLLs nativas.  
  
   Para obter mais informações, confira [/CLRUNMANAGEDCODECHECK (Adicionar o SuppressUnmanagedCodeSecurityAttribute)](https://msdn.microsoft.com/library/73abc426-dab0-45e2-be85-0f9a14206cc2).  
  
- **CreateHotPatchableImage**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Prepara uma imagem para patch instantâneo.  
  
   Especifique um dos valores a seguir, que corresponda a uma opção de vinculador.  
  
  - **Habilitado**  -  **/FUNCTIONPADMIN**  
  
  - **X86Image**  -  **/FUNCTIONPADMIN: 5**  
  
  - **X64Image**  -  **/FUNCTIONPADMIN: 6**  
  
  - **ItaniumImage**  -  **/FUNCTIONPADMIN: 16**  
  
    Para obter mais informações, consulte [/FUNCTIONPADMIN (criar imagem Hotpatchable)](https://msdn.microsoft.com/library/25b02c13-1add-4fbd-add9-fcb30eb2cae7).  
  
- **DataExecutionPrevention**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, indicará que um executável foi testado e considerado compatível com o recurso de Prevenção de Execução de Dados do Windows.  
  
   Para obter mais informações, consulte [/NXCOMPAT (Compatível com a Prevenção de Execução de Dados)](https://msdn.microsoft.com/library/5858e7ff-24d3-4ac3-9046-af2c9e220d9b).  
  
- **DelayLoadDLLs**  
  
   Parâmetro opcional de **cadeia de caracteres []** .  
  
   Esse parâmetro causa um *atraso no carregamento* de DLLs. Especifique o nome de uma DLL para atrasar o carregamento.  
  
   Para obter mais informações, consulte [/DELAYLOAD (atrasar carga de importação)](https://msdn.microsoft.com/library/39ea0f1e-5c01-450f-9c75-2d9761ff9b28).  
  
- **DelaySign**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, assinará parcialmente um assembly. Por padrão, o valor é `false`.  
  
   Para obter mais informações, consulte [/DelaySign (parcialmente assinante de um assembly)](https://msdn.microsoft.com/library/15244d30-3ecb-492f-a408-ffe81f38de20).  
  
- **Driver**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifique esse parâmetro para criar um driver de modo de kernel do Windows NT.  
  
   Especifique um dos valores a seguir, cada um correspondente a uma opção de vinculador.  
  
  - **NotSet** - *\<none>*  
  
  - Do **Driver**  -  **/Driver**  
  
  - **Somente**  -  **/Driver: somente**  
  
  - **WDM**  -  **/Driver: WDM**  
  
    Para obter mais informações, consulte [/Driver (driver de modo de kernel do Windows NT)](https://msdn.microsoft.com/library/aeee8e28-5d97-40f5-ba16-9f370fe8a1b8).  
  
- **EmbedManagedResourceFile**  
  
   Parâmetro opcional de **cadeia de caracteres []** .  
  
   Insere um arquivo de recurso em um assembly. Especifique o nome do arquivo de recurso necessário. Como opção, especifique o nome lógico, usado para carregar o recurso e a opção **PRIVADO**, que indica no manifesto do assembly que o arquivo de recurso é privado.  
  
   Para obter mais informações, consulte [/ASSEMBLYRESOURCE (inserir um recurso gerenciado)](https://msdn.microsoft.com/library/0ce6e1fb-921b-4b1b-a59c-d35388d789f2).  
  
- **EnableCOMDATFolding**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, habilitará a dobra COMDAT idêntica.  
  
   Para obter mais informações, consulte o argumento `ICF[= iterations]` de [/OPT (Otimizações)](https://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **EnableUAC**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, especificará que as informações do UAC (Controle de Conta de Usuário) estão inseridas no manifesto do programa.  
  
   Para obter mais informações, consulte [/MANIFESTUAC (Insere informações UAC no manifesto)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **EntryPointSymbol**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica uma função de ponto de entrada como o endereço de início para um arquivo .exe ou DLL. Especifique um nome de função como valor do parâmetro.  
  
   Para obter mais informações, consulte [/Entry (símbolo de ponto de entrada)](https://msdn.microsoft.com/library/26c62ba2-4f52-4882-a7bd-7046a0abf445).  
  
- **FixedBaseAddress**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, criará um programa ou DLL que pode ser carregado somente em seu endereço básico preferido.  
  
   Para obter mais informações, consulte [/Fixed (endereço base fixo)](https://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).  
  
- **ForceFileOutput**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Instrui o vinculador a criar um arquivo válido .exe ou DLL mesmo que um símbolo esteja referenciado, mas não definido, ou seja, definido várias vezes.  
  
   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
  - **Habilitado**  -  **/Force**  
  
  - **MultiplyDefinedSymbolOnly**  -  **/Force: vários**  
  
  - **UndefinedSymbolOnly**  -  **/Force: não resolvido**  
  
    Para obter mais informações, consulte [/Force (forçar saída do arquivo)](https://msdn.microsoft.com/library/b1e9a218-a5eb-4e60-a4a4-65b4be15e5da).  
  
- **ForceSymbolReferences**  
  
   Parâmetro opcional de **cadeia de caracteres []** .  
  
   Esse parâmetro instrui o vinculador a adicionar um símbolo especificado à tabela de símbolos.  
  
   Para obter mais informações, consulte [/include (referências de símbolo de força)](https://msdn.microsoft.com/library/4a039677-360a-480f-bd0b-448e239b449c).  
  
- **FunctionOrder**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Esse parâmetro otimiza seu programa colocando as funções empacotadas (COMDATs) especificadas na imagem em uma ordem predeterminada.  
  
   Para obter mais informações, consulte [/Order (put functions in order)](https://msdn.microsoft.com/library/ecf5eb3e-e404-4e86-9a91-4e5ec157261a).  
  
- **GenerateDebugInformation**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, criará informações de depuração para o arquivo .exe ou DLL.  
  
   Para obter mais informações, consulte [/debug (gerar informações de depuração)](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).  
  
- **GenerateManifest**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, criará um arquivo de manifesto lado a lado.  
  
   Para obter mais informações, consulte [/manifest (criar manifesto de assembly lado a lado)](https://msdn.microsoft.com/library/98c52e1e-712c-4f49-b149-4d0a3501b600).  
  
- **GenerateMapFile**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, criará um *arquivo de mapa*. A extensão de nome de arquivo do arquivo de mapa é .map.  
  
   Para obter mais informações, consulte [/MAP (gerar mapa)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).  
  
- **HeapCommitSize**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica a quantidade de memória física no heap a se alocar por vez.  
  
   Para obter mais informações, consulte o `commit` argumento em [/heap (definir o tamanho do heap)](https://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Consulte também o parâmetro **HeapReserveSize**.  
  
- **HeapReserveSize**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica a alocação de heap total na memória virtual.  
  
   Para obter mais informações, consulte o `reserve` argumento em [/heap (definir o tamanho do heap)](https://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Consulte também o parâmetro **HeapCommitSize** nesta tabela.  
  
- **IgnoreAllDefaultLibraries**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, instruirá o vinculador a remover uma ou mais bibliotecas padrão da lista de bibliotecas pesquisadas ao resolver referências externas.  
  
   Para obter mais informações, consulte [/NODEFAULTLIB (ignorar bibliotecas)](https://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **IgnoreEmbeddedIDL**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, especificará que qualquer atributo IDL em código-fonte não deve ser processado em um arquivo .idl.  
  
   Para obter mais informações, consulte [/IGNOREIDL (não processar atributos no MIDL)](https://msdn.microsoft.com/library/29514098-6a1c-4317-af2f-1dc268972780).  
  
- **IgnoreImportLibrary**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, especificará que a biblioteca de importações gerada por esta configuração não deve ser importada para os projetos dependentes.  
  
   Esse parâmetro não corresponde a uma opção de vinculador.  
  
- **IgnoreSpecificDefaultLibraries**  
  
   Parâmetro opcional de **cadeia de caracteres []** .  
  
   Especifica um ou mais nomes de bibliotecas padrão a serem ignoradas. Separe várias bibliotecas usando ponto e vírgula.  
  
   Para obter mais informações, consulte [/NODEFAULTLIB (ignorar bibliotecas)](https://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **ImageHasSafeExceptionHandlers**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, o vinculador produzirá uma imagem somente se também puder produzir uma tabela de manipuladores de exceção segura da imagem.  
  
   Para obter mais informações, consulte [/SAFESEH (a imagem tem manipuladores de exceção segura)](https://msdn.microsoft.com/library/7722ff99-b833-4c65-a855-aaca902ffcb7).  
  
- **ImportLibrary**  
  
   Um nome de biblioteca de importação especificado pelo usuário que substitui o nome da biblioteca padrão.  
  
   Para obter mais informações, consulte [/IMPLIB (biblioteca de importação de nome)](https://msdn.microsoft.com/library/fe8f71ab-7055-41b5-8ef8-2b97cfa4a432).  
  
- **KeyContainer**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Contêiner que contém a chave para um assembly assinado.  
  
   Para obter mais informações, consulte [/keycontainer (especifique um contêiner de chave para assinar um assembly)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e). Consulte também o parâmetro **KeyFile** nesta tabela.  
  
- **Chaves**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica um arquivo que contém a chave para um assembly assinado.  
  
   Para obter mais informações, consulte [/keyfile (especifique a chave ou o par de chaves para assinar um assembly)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06). Consulte também o parâmetro **KeyContainer**.  
  
- **LargeAddressAware**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, o aplicativo poderá identificar endereços maiores do que 2 gigabytes.  
  
   Para obter mais informações, consulte [/LARGEADDRESSAWARE (tratar endereços grandes)](https://msdn.microsoft.com/library/a29756c8-e893-47a9-9750-1f0d25359385).  
  
- **LinkDLL**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, criará uma DLL como o arquivo de saída principal.  
  
   Para obter mais informações, consulte [/DLL (Compilar uma DLL)](https://msdn.microsoft.com/library/c7685aec-31d0-490f-9503-fb5171a23609).  
  
- **LinkErrorReporting**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Permite que você forneça informações de ICE (erro interno do compilador) diretamente à Microsoft.  
  
   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
  - **NoErrorReport** - **/ERRORREPORT:NONE**  
  
  - **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
  - **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
  - **SendErrorReport** - **/ERRORREPORT:SEND**  
  
    Para obter mais informações, consulte [/errorReport (relatar erros internos do vinculador)](https://msdn.microsoft.com/library/f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28).  
  
- **LinkIncremental**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, habilitará a vinculação incremental.  
  
   Para obter mais informações, consulte [/incremental (link incremental)](https://msdn.microsoft.com/library/135656ff-94fa-4ad4-a613-22e1a2a5d16b).  
  
- **LinkLibraryDependencies**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, especificará que as saídas de biblioteca das dependências do projeto serão vinculadas automaticamente.  
  
   Esse parâmetro não corresponde a uma opção de vinculador.  
  
- **LinkStatus**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, especificará que o vinculador deve exibir um indicador de progresso que mostrará o percentual concluído do link.  
  
   Para obter mais informações, consulte o `STATUS` argumento de [/LTCG (geração de código de tempo de vinculação)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **LinkTimeCodeGeneration**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica opções para a otimização guiada por perfil.  
  
   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
  - **Os** - *\<none>*  
  
  - **UseLinkTimeCodeGeneration**  -  **/LTCG**  
  
  - **PGInstrument**  -  **/LTCG: PGInstrument**  
  
  - **PGOptimization**  -  **/LTCG: PGOptimize**  
  
  - **PGUpdate**  
  
     \- **/LTCG:PGUpdate**  
  
    Para obter mais informações, consulte [/LTCG (geração de código de tempo de vinculação)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **ManifestFile**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Altera o nome do arquivo de manifesto padrão para o nome de arquivo especificado.  
  
   Para obter mais informações, consulte [/MANIFESTFILE (nomear arquivo de manifesto)](https://msdn.microsoft.com/library/befa5ab2-a9cf-4c9b-969a-e7b4a930f08d).  
  
- **MapExports**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, instruirá o vinculador a incluir funções exportadas em um arquivo de mapa.  
  
   Para obter mais informações, consulte o `EXPORTS` argumento de [/MAPINFO (inclua informações em mapa)](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).  
  
- **MapFileName**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Altera o nome do arquivo de mapa padrão para o nome de arquivo especificado.  
  
- **MergedIDLBaseFileName**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica o nome de arquivo e a extensão de nome de arquivo .idl.  
  
   Para obter mais informações, consulte [/IDLOUT (nome de arquivos de saída MIDL)](https://msdn.microsoft.com/library/10d00a6a-85b4-4de1-8732-e422c6931509).  
  
- **MergeSections**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Combina seções em uma imagem. Especifique `from-section=to-section`.  
  
   Para obter mais informações, consulte [/Merge (Combine Sections)](https://msdn.microsoft.com/library/10fb20c2-0b3f-4c8d-98a8-f69aedf03d52).  
  
- **MidlCommandFile**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifique o nome de um arquivo que contém opções de linha de comando MIDL.  
  
   Para obter mais informações, consulte [/MIDL (especifique as opções de linha de comando MIDL)](https://msdn.microsoft.com/library/22dc259e-b34c-4ed3-a380-4beb734482c1).  
  
- **MinimumRequiredVersion**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica a versão mínima necessária do subsistema. Os argumentos são números decimais no intervalo de 0 a 65535.  
  
- **ModuleDefinitionFile**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica o nome de um [arquivo de definição de módulo](https://msdn.microsoft.com/library/08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8).  
  
   Para obter mais informações, consulte [/def (especificar arquivo de definição de módulo)](https://msdn.microsoft.com/library/6497fa68-65f0-48ca-8f66-b87166fc631a).  
  
- **MSDOSStubFileName**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Anexa o programa stub MS-DOS especificado a um programa Win32.  
  
   Para obter mais informações, consulte [/stub (nome do arquivo stub do MS-dos)](https://msdn.microsoft.com/library/65221ffe-4f9a-4a14-ac69-3cfb79b40b5f).  
  
- **NoEntryPoint**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, criará uma DLL somente de recursos.  
  
   Para obter mais informações, consulte [/NOENTRY (nenhum ponto de entrada)](https://msdn.microsoft.com/library/0214dd41-35ad-43ab-b892-e636e038621a).  
  
- **ObjectFiles**  
  
   Parâmetro implícito **Cadeia de Caracteres[]**.  
  
   Especifica os arquivos-objeto vinculados.  
  
- **OptimizeReferences**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, eliminará a funções e/ou dados que nunca são referenciados.  
  
   Para obter mais informações, consulte o argumento `REF` em [/OPT (Otimizações)](https://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **OutputFile**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Substitui o nome padrão e o local do programa que o vinculador cria.  
  
   Para obter mais informações, consulte [/out (nome do arquivo de saída)](https://msdn.microsoft.com/library/976210a4-e51f-4cfb-af5e-c16344455834).  
  
- **PerUserRedirection**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true` e Registrar Saída estiverem habilitados, forçará as gravações de Registro para **HKEY_CLASSES_ROOT** a serem redirecionadas para **HKEY_CURRENT_USER**.  
  
- **PreprocessOutput**  
  
   Parâmetro `ITaskItem[]` opcional.  
  
   Define uma matriz de itens de saída do pré-processador que podem ser consumidos e emitidos por tarefas.  
  
- **PreventDllBinding**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, indicará ao Bind.exe que a imagem vinculada não deve ser associada.  
  
   Para obter mais informações, consulte [/ALLOWBIND (impedir Associação de dll)](https://msdn.microsoft.com/library/30e37e24-12e4-407e-988a-39d357403598).  
  
- **Perfil**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, produzirá um arquivo de saída que pode ser usado com o criador de perfil de **Ferramentas de Desempenho**.  
  
   Para obter mais informações, consulte [/Profile (Performance Tools Profiler)](https://msdn.microsoft.com/library/e676baa1-5063-47a3-a357-ba0d1f0d1699).  
  
- **ProfileGuidedDatabase**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica o nome do arquivo .pgd que será usado para armazenar informações sobre o programa em execução  
  
   Para obter mais informações, consulte [/PGD (especificar o banco de dados para otimizações guiadas por perfil)](https://msdn.microsoft.com/library/9f312498-493b-461f-886f-92652257e443).  
  
- **ProgramDatabaseFile**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica um nome para o banco de dados do programa (PDB) que o vinculador cria.  
  
   Para obter mais informações, consulte [/PDB (usar o banco de dados do programa)](https://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d).  
  
- **RandomizedBaseAddress**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, gerará uma imagem executável que pode trocar base aleatoriamente no momento do carregamento usando o recurso *ASLR* (Address Space Layout Randomization) do Windows.  
  
   Para obter mais informações, consulte [/DYNAMICBASE (Usar Aleatorização do Layout de Espaço do Endereço)](https://msdn.microsoft.com/library/6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2).  
  
- **RegisterOutput**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, registrará a saída primária desse build.  
  
- **SectionAlignment**  
  
   Parâmetro opcional de **Inteiro**.  
  
   Especifica o alinhamento de cada seção dentro do espaço de endereço linear do programa. O valor do parâmetro é um número de unidade de bytes e uma potência de dois.  
  
   Para obter mais informações, consulte [/align (alinhamento de seção)](https://msdn.microsoft.com/library/f2f8ac24-e90e-4bea-8205-f2960a3b1740).  
  
- **SetChecksum**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, definirá a soma de verificação no cabeçalho de um arquivo .exe.  
  
   Para obter mais informações, consulte [/Release (definir a soma de verificação)](https://msdn.microsoft.com/library/93bcadf4-29ac-4824-914b-6997e3751d22).  
  
- **Progresso**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica detalhamento de relatórios de progresso da operação de vinculação.  
  
   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
  - **NotSet** - *\<none>*  
  
  - **LinkVerbose**  -  **/Verbose**  
  
  - **LinkVerboseLib**  -  **/Verbose: lib**  
  
  - **LinkVerboseICF**  -  **/verbose: ICF**  
  
  - **LinkVerboseREF**  -  **/verbose: REF**  
  
  - **LinkVerboseSAFESEH**  -  **/verbose: SAFESEH**  
  
  - **LinkVerboseCLR**  -  **/verbose: CLR**  
  
    Para obter mais informações, consulte [/Verbose (mensagens de andamento da impressão)](https://msdn.microsoft.com/library/9c347d98-4c37-4724-a39e-0983934693ab).  
  
- **Fontes**  
  
   Parâmetro `ITaskItem[]` obrigatório.  
  
   Define uma matriz de itens de arquivo de origem do MSBuild que pode ser consumida e emitida por tarefas.  
  
- **SpecifySectionAttributes**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica os atributos de uma seção. Isso substitui os atributos que foram definidos quando o arquivo .obj para a seção foi compilado.  
  
   Para obter mais informações, consulte [/Section (especificar atributos de seção)](https://msdn.microsoft.com/library/92b69d81-e421-462e-b46f-7d0dff9b9d16).  
  
- **StackCommitSize**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica a quantidade de memória física em cada alocação quando mais memória é alocada.  
  
   Para obter mais informações, consulte o `commit` argumento de [/Stack (alocações de pilha)](https://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StackReserveSize**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica o tamanho de alocação de pilha total em memória virtual.  
  
   Para obter mais informações, consulte o `reserve` argumento de [/Stack (alocações de pilha)](https://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StripPrivateSymbols**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Cria um segundo arquivo de banco de dados do programa (PDB) que omite os símbolos que você não deseja distribuir aos seus clientes. Especifique o nome do segundo arquivo PDB.  
  
   Para obter mais informações, consulte [/PDBSTRIPPED (símbolos privados de faixa)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).  
  
- **Subsistema**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica o ambiente para o executável.  
  
   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
  - **NotSet** - *\<none>*  
  
  - **Console** - **/SUBSYSTEM:CONSOLE**  
  
  - **Windows** - **/SUBSYSTEM:WINDOWS**  
  
  - **Nativo** - **/SUBSYSTEM:NATIVE**  
  
  - **Aplicativo EFI** - **/SUBSYSTEM:EFI_APPLICATION**  
  
  - **Driver de Serviço de Inicialização EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
  - **EFI ROM** - **/SUBSYSTEM:EFI_ROM**  
  
  - **Tempo de Execução de EFI** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
  - **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**  
  
  - **POSIX** - **/SUBSYSTEM:POSIX**  
  
    Para obter mais informações, consulte [/Subsystem (especificar subsistema)](https://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b).  
  
- **SupportNobindOfDelayLoadedDLL**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, instruirá o vinculador a não incluir uma IAT (Tabela de Endereços de Importação) associável na imagem final.  
  
   Para obter mais informações, consulte o `NOBIND` argumento de [/Delay (atrasar carregamento de configurações de importação)](https://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SupportUnloadOfDelayLoadedDLL**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, instruirá a função de ajuda de carregamento atrasado a dar suporte ao descarregamento explícito da DLL.  
  
   Para obter mais informações, consulte o `UNLOAD` argumento de [/Delay (atrasar carregamento de configurações de importação)](https://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SuppressStartupBanner**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.  
  
   Para obter mais informações, consulte [/nologo (Suprimir faixa de inicialização) (vinculador)](https://msdn.microsoft.com/library/3b20dddd-eca6-4545-a331-9f70bf720197).  
  
- **SwapRunFromCD**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, instruirá o sistema operacional a copiar a saída do vinculador para um arquivo de permuta e, em seguida, executará a imagem por meio dele.  
  
   Para obter mais informações, consulte o `CD` argumento de [/SWAPRUN (carregar linker saída para arquivo de permuta)](https://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Consulte também o parâmetro **SwapRunFromNET**.  
  
- **SwapRunFromNET**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, instruirá o sistema operacional a copiar a saída do vinculador para um arquivo de permuta e, em seguida, executará a imagem por meio dele.  
  
   Para obter mais informações, consulte o `NET` argumento de [/SWAPRUN (carregar linker saída para arquivo de permuta)](https://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Consulte também o parâmetro **SwapRunFromCD** nesta tabela.  
  
- **TargetMachine**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica a plataforma de destino para o programa ou DLL.  
  
   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
  - **NotSet** - *\<none>*  
  
  - **MachineARM** - **/MACHINE:ARM**  
  
  - **MachineEBC** - **/MACHINE:EBC**  
  
  - **MachineIA64** - **/MACHINE:IA64**  
  
  - **MachineMIPS** - **/MACHINE:MIPS**  
  
  - **MachineMIPS16** - **/MACHINE:MIPS16**  
  
  - **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
  - **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
  - **MachineSH4** - **/MACHINE:SH4**  
  
  - **MachineTHUMB** - **/MACHINE:THUMB**  
  
  - **MachineX64** - **/MACHINE:X64**  
  
  - **MachineX86** - **/MACHINE:X86**  
  
    Para obter mais informações, consulte [/Machine (especificar plataforma de destino)](https://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2).  
  
- **TerminalServerAware**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, definirá um sinalizador no campo IMAGE_OPTIONAL_HEADER DllCharacteristics no cabeçalho opcional da imagem do programa. Quando esse sinalizador estiver definido, o servidor Host da Sessão da Área de Trabalho Remota não fará certas alterações no aplicativo.  
  
   Para obter mais informações, consulte [/TSAWARE (criar Terminal Server aplicativo com reconhecimento)](https://msdn.microsoft.com/library/fe1c1846-de5b-4839-b562-93fbfe36cd29).  
  
- **TrackerLogDirectory**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica o diretório de log de rastreamento.  
  
- **TreatLinkerWarningAsErrors**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, fará com que nenhum arquivo de saída seja gerado caso o vinculador gere um aviso.  
  
   Para obter mais informações, consulte [/WX (tratar avisos do vinculador como erros)](https://msdn.microsoft.com/library/e4ba97c7-93f7-43ae-a4bb-d866790926c9).  
  
- **TurnOffAssemblyGeneration**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, criará uma imagem para o arquivo de saída atual sem um assembly do .NET Framework.  
  
   Para obter mais informações, consulte [/NOASSEMBLY (criar um módulo MSIL)](https://msdn.microsoft.com/library/3cea4e70-f451-4395-a626-1930b1b127fe).  
  
- **TypeLibraryFile**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica o nome de arquivo e a extensão de nome de arquivo .tlb. Especifique um nome de arquivo ou um caminho e nome de arquivo.  
  
   Para obter mais informações, consulte [/TLBOUT (Name. Arquivo TLB)](https://msdn.microsoft.com/library/0df6d078-2e48-46c9-a1a5-02674d85dce8).  
  
- **TypeLibraryResourceID**  
  
   Parâmetro opcional de **Inteiro**.  
  
   Designa um valor especificado pelo usuário para uma biblioteca de tipos criada pelo vinculador. Especifique um valor de 1 a 65535.  
  
   Para obter mais informações, consulte [/TlbId (especificar ID de recurso para TypeLib)](https://msdn.microsoft.com/library/434b28a2-4656-4d52-ac82-8b18bf486fb2).  
  
- **UACExecutionLevel**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Especifica o nível de execução solicitado para o aplicativo quando ele é executado com Controle de Conta de Usuário.  
  
   Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
  - **AsInvoker** - `level='asInvoker'`  
  
  - **HighestAvailable** - `level='highestAvailable'`  
  
  - **RequireAdministrator** - `level='requireAdministrator'`  
  
    Para obter mais informações, consulte o argumento `level` de [/MANIFESTUAC (Insere informações UAC no manifesto)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UACUIAccess**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, o aplicativo ignorará os níveis de proteção da interface do usuário e direcionará a entrada para janelas de permissão superior na área de trabalho; caso contrário, `false`.  
  
   Para obter mais informações, consulte o argumento `uiAccess` de [/MANIFESTUAC (Insere informações UAC no manifesto)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UseLibraryDependencyInputs**  
  
   Parâmetro **booliano** opcional.  
  
   Se `true`, as entradas para a ferramenta de biblioteca serão usadas em vez do próprio arquivo de biblioteca ao vincular saídas de biblioteca de dependências do projeto.  
  
- **Versão**  
  
   Parâmetro de **cadeia de caracteres** opcional.  
  
   Coloque um número de versão no cabeçalho do arquivo .dll ou .exe. Especifique “`major[.minor]`”. Os argumentos `major` e `minor` são números decimais de 0 a 65535.  
  
   Para obter mais informações, consulte [/Version (informações de versão)](https://msdn.microsoft.com/library/b86d0e86-dca6-4316-aee2-d863ccb9f223).  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de tarefa](../msbuild/msbuild-task-reference.md)
