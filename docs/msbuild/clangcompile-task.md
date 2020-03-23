---
title: Tarefa ClangCompile | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.clangcompile
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ClangCompile task
- ClangCompile task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: c1526fbd3c2c0822781f0e011999ddcb9c679170
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275469"
---
# <a name="clangcompile-task"></a>Tarefa ClangCompile

Envolve a ferramenta de compilador Microsoft C++, clang.exe.

## <a name="parameters"></a>parâmetros

A tabela a seguir descreve os parâmetros da tarefa **ClangCompile**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Parâmetro opcional **de string[].**<br/><br/>Especifica um ou mais diretórios a serem adicionados ao caminho de inclusão, separados por ponto e vírgula no caso de mais de um.<br/><br/>Use `-I[path]`.|
|**AdditionalOptions**|Parâmetro opcional **de string.**|
|**BufferSecurityCheck**|Parâmetro opcional **de string.**<br/><br/>A Verificação de Segurança ajuda a detectar saturações de buffer de pilha, uma tentativa de ataque comum à segurança de um programa. <br/><br/>Use `fstack-protector`.|
|**BuildingInIde**|Parâmetro opcional **bool**.|
|**CLanguageStandard**|Parâmetro opcional **de string.**<br/><br/>Determina o padrão de linguagem C.<br/><br/>Use `std=[value]` com o valor de **c89**, **c99**, **c11**, **gnu99** ou **gnu11**.|
|**ClangVersion**|Parâmetro opcional **de string.**|
|**CompileAs**|Parâmetro opcional **de string.**<br/><br/>Selecione a opção de linguagem de compilação para arquivos .c e .cpp. Padrão detectará com base na extensão .c ou .cpp.<br/><br/>Use `-x c`, `-x c++`.|
|**CppLanguageStandard**|Parâmetro opcional **de string.**<br/><br/>Determina o padrão de linguagem C++.<br/><br/>Use `std=[value]` com o valor de **c++98**, **c++11**, **c++1y**, **gnu++98**, **gnu++11** ou **gnu++1y**.|
|**DataLevelLinking**|Parâmetro opcional **bool**.<br/><br/>Habilita as otimizações do vinculador para remover dados não utilizados ao emitir cada item de dados em uma seção separada.|
|**DebugInformationFormat**|Parâmetro opcional **de string.**<br/><br/>Especifica o tipo de informações de depuração geradas pelo compilador.<br/><br/>**Nenhum**, não produz informação de depuração; portanto, a compilação pode ser mais rápida (use `g0`).<br/>**FullDebug**, gere informações de depuração DWARF2 (use `g2 -gdwarf-2`).<br/>**LineNumber**, gere somente informações de Número de Linha (use `gline-tables-only`).|
|**EnableNeonCodegen**|Parâmetro opcional **bool**.<br/><br/>Habilita a geração de código para hardware de ponto flutuante NEON. Somente se aplica a arquiteturas arm.|
|**ExceptionHandling**|Parâmetro opcional **de string.**<br/><br/>Especifica o modelo de tratamento de exceções a ser utilizado pelo compilador.<br/><br/>**Desabilitado**, desabilite o tratamento de exceções (use `fno-exceptions`).<br/>**Habilitado**, habilite o tratamento de exceções (use `fexceptions`).<br/>**UnwindTables**, gera todos os dados estáticos necessários, mas não afeta o código gerado (use `funwind-tables`).|
|**FloatABI**|Parâmetro opcional **de string.**<br/><br/>Opção de seleção para escolher o ABI de ponto flutuante.<br/><br/>**soft**, faz com que o compilador gere saídas contendo chamadas da biblioteca para operações de ponto flutuante (use `mfloat-abi=soft`).<br/>**softfp**, permite a geração de código usando instruções de ponto flutuante de hardware, mas ainda usa as convenções de chamada de flutuação suave (use `mfloat-abi=softfp`).<br/>**hard**, permite a geração de instruções de ponto flutuante e usa convenções de chamada específicas de FPU (use `mfloat-abi=hard`).|
|**ForcedIncludeFiles**|Parâmetro opcional **de string[].**<br/><br/>Um ou mais arquivos de inclusão forçados.<br/><br/>Use `-include [name]`.|
|**FunctionLevelLinking**|Parâmetro opcional **bool**.<br/><br/>Permite que o compilador empacote funções individuais no formato de funções empacotadas (COMDATs). Necessário para editar e continuar a trabalhar.<br/><br/>Use `ffunction-sections`.|
|**GccToolChain**|Parâmetro opcional **de string.**<br/><br/>Caminho da pasta para Cadeia de Ferramenta Gcc.|
|**GNUMode**|Parâmetro opcional **bool**.<br/><br/>|
|**MSCompatibility**|Parâmetro opcional **bool**.<br/><br/>Habilite a compatibilidade completa do Microsoft C++.|
|**MSCompatibilityVersion**|Parâmetro opcional **de string.**<br/><br/>O valor separado por ponto que representa o número de versão do compilador da Microsoft a relatar em _MSC_VER (0 = não definir (padrão)).|
|**MSExtensions**|Parâmetro opcional **bool**.<br/><br/>Aceite alguns construtos não padrão para os quais o compilador da Microsoft dá suporte.|
|**MSCompilerVersion**|Parâmetro opcional **de string.**<br/><br/>O número de versão do compilador da Microsoft para relatar no _MSC_VER (0 = não definir (padrão)).|
|**MSVCErrorReport**|Parâmetro opcional **bool**.<br/><br/>Relate erros que o Visual Studio pode usar para analisar informações sobre arquivos e linhas.|
|**ObjectFileName**|Parâmetro opcional **de string.**<br/><br/>Especifica um nome para substituir o nome do arquivo-objeto padrão. Pode ser um nome de arquivo ou de diretório.<br/><br/>Use `/Fo[name]`.|
|**OmitFramePointers**|Parâmetro opcional **bool**.<br/><br/>Inibe a criação de ponteiros de quadros na pilha de chamadas.|
|**Otimização**|Parâmetro opcional **de string.**<br/><br/>Especifica o nível de otimização para o aplicativo.<br/><br/>**Personalizar**, personalizar a otimização.<br/>**Desabilitado**, desabilitar a otimização (use `O0`).<br/>**MinSize**, otimizar o tamanho (use `Os`).<br/>**MaxSpeed**, otimizar para velocidade (use `O2`).<br/>**Full**, otimizações dispendiosas (use `O3`).|
|**PositionIndependentCode**|Parâmetro opcional **bool**.<br/><br/>Gere um código independente da posição (PIC) para ser usado em uma biblioteca compartilhada.|
|**PrecompiledHeader**|Parâmetro opcional **de string.**<br/><br/>Habilita a criação ou o uso de um cabeçalho pré-compilado durante o build.|
|**PrecompiledHeaderFile**|Parâmetro opcional **de string.**<br/><br/>Especifica o nome do arquivo de cabeçalho a ser usado para o arquivo de cabeçalho pré-compilado. Esse arquivo também será adicionado a **Arquivos de Inclusão Forçados** durante o build.|
|**PrecompiledHeaderOutputFileDirectory**|Parâmetro opcional **de string.**<br/><br/>Especifica o diretório para o cabeçalho pré-compilado gerado. Este diretório também será adicionado aos **Diretórios adicionais de incluir** durante a compilação.|
|**PrecompiledHeaderCompileAs**|Parâmetro opcional **de string.**<br/><br/>Selecione a opção de linguagem de compilação para o arquivo de cabeçalho pré-compilado.<br/><br/>Use `-x c-header`, `-x c++-header`.|
|**PreprocessorDefinitions**|Parâmetro opcional **de string[].**<br/><br/>Define símbolos de pré-processamento para o arquivo de origem.<br/><br/>Use `-D`.|
|**RuntimeLibrary**|Parâmetro opcional **de string.**<br/><br/>Especifique a biblioteca de runtime para vinculação.<br/><br/>Use as opções `MSVC /MT`, `/MTd`, `/MD`, `/MDd`.<br/><br/>**MultiThreaded**, faz com que seu aplicativo utilize a versão multithread e estática da biblioteca em tempo de execução.<br/>**MultiThreadedDebug**, define _DEBUG e _MT. Essa opção também faz com que o compilador coloque o nome da biblioteca LIBCMTD.lib no arquivo .obj para que o vinculador use LIBCMTD.lib para resolver símbolos externos.<br/>**MultiThreadedDLL**, faz com que o aplicativo use a versão específica de multithread e a versão específica de DLL da biblioteca em tempo de execução. Define _MT e _DLL e faz com que o compilador coloque o nome da biblioteca MSVCRT.lib no arquivo .obj.<br/>**MultiThreadedDebugDLL**, define _DEBUG, _MT e _DLL e faz com que o aplicativo use a versão específica de multithread e a versão específica de DLL da biblioteca em tempo de execução. Também faz com que o compilador coloque o nome da biblioteca MSVCRTD.lib no arquivo .obj.|
|**RuntimeTypeInfo**|Parâmetro opcional **bool**.<br/><br/>Adiciona um código para verificar os tipos de objeto C++ no runtime (informações de tipo de runtime).<br/><br/>Use `frtti`, `fno-rtti`.|
|**ShowIncludes**|Parâmetro opcional **bool**.<br/><br/>Gera uma lista de arquivos de inclusão com a saída do compilador.<br/><br/>Use `-H`.|
|**Fontes**|Parâmetro **ITaskItem necessário[].**|
|**StrictAliasing**|Parâmetro opcional **bool**.<br/><br/>Considere as regras de alias mais rígidas. Um objeto de um tipo nunca será considerado como residente do mesmo endereço que um objeto de um tipo diferente.|
|**Sysroot**|Parâmetro opcional **de string.**<br/><br/>Caminho da pasta para o diretório raiz para cabeçalhos e bibliotecas.|
|**TargetArch**|Parâmetro opcional **de string.**<br/><br/>Arquitetura de Destino.|
|**ThumbMode**|Parâmetro opcional **de string.**<br/><br/>Gerar um código que pode ser executado em microarquiteturas thumb. Somente se aplica a arquiteturas arm.<br/><br/>**Thumb**, gere código Thumb (use `mthumb`).<br/>**ARM**, gere código Arm (use `marm`).<br/>**Desabilitado**, opção não aplicável à plataforma escolhida.|
|**TrackerLogDirectory**|Parâmetro opcional **de string.**<br/><br/>Diretório de Log do Rastreador.|
|**TreatWarningAsError**|Parâmetro opcional **bool**.<br/><br/>Trata todos os avisos do compilador como erros.<br/><br/>Para um novo projeto, talvez seja melhor usar `/WX` em todas as compilações. Resolver todos os avisos assegurará o menor número possível de defeitos de código difíceis de localizar.|
|**UndefinePreprocessorDefinitions**|Parâmetro opcional **de string[].**<br/><br/>Especifica uma ou mais exclusões de definição do pré-processador.<br/><br/>Use `-U [macro]`.|
|**UndefineAllPreprocessorDefinitions**|Parâmetro opcional **bool**.<br/><br/>Exclua as definições de todos os valores do pré-processador definidos anteriormente.<br/><br/>Use `-undef`.|
|**UseMultiToolTask**|Parâmetro opcional **bool**.<br/><br/>Compilação de multiprocessador.|
|**UseShortEnums**|Parâmetro opcional **bool**.<br/><br/>O tipo enum usa somente o número de bytes exigido pelo conjunto de entrada de valores possíveis.|
|**Verbose**|Parâmetro opcional **bool**.<br/><br/>Mostrar os comandos a serem executados e usar a saída detalhada.|
|**WarningLevel**|Parâmetro opcional **de string.**<br/><br/>Selecione o rigor que você deseja que o compilador aplique aos erros de código. Outras bandeiras devem ser adicionadas `/Weverything`diretamente às **Opções Adicionais** (se `/w`, ).<br/><br/>**TurnOffAllWarnings**, desabilita todos os avisos do compilador (use `w`).<br/>**EnableAllWarnings**, habilita todos os avisos, incluindo os que estão desabilitados por padrão (use `Wall`).|

## <a name="see-also"></a>Confira também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)