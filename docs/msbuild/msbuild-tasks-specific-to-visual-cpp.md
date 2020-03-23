---
title: MSBuild Tarefas Específicas para C++ | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 6393e771f9e9ed862d21397dabacdb3f3808c386
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633142"
---
# <a name="msbuild-tasks-specific-to-c"></a>MSBuild tarefas específicas para C++

Tarefas fornecem o código que é executado durante o processo de build. Quando o C++ é instalado, as seguintes tarefas estão disponíveis, além daquelas instaladas com o MSBuild. Para obter mais informações, consulte [a visão geral do MSBuild (C++).](/cpp/build/msbuild-visual-cpp-overview)

 Além dos parâmetros para cada tarefa, todas as tarefas também têm os seguintes parâmetros.

| Parâmetro | Descrição |
|-------------------| - |
| `Condition` | Parâmetro `String` opcional.<br /><br /> Uma `Boolean` expressão que o mecanismo MSBuild usa para determinar se essa tarefa será executada. Para obter informações sobre as condições suportadas pelo MSBuild, consulte [Condições](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parâmetro opcional. Pode conter um dos seguintes valores:<br /><br /> -   **WarnAndContinue** ou **true**. Quando uma tarefa falha, as tarefas subsequentes no elemento de [Destino](../msbuild/target-element-msbuild.md) e a compilação continuam em execução, e todos os erros da tarefa são tratados como avisos<br />-   **ErrorAndContinue**. Quando uma tarefa falha, as tarefas subsequentes no elemento de `Target` e o build continuam em execução e todos os erros da tarefa são tratados como erros.<br />-   **ErrorAndStop** ou **false** (padrão). Quando uma tarefa falha, as tarefas restantes do elemento de `Target` e o build não são executadas e todo o elemento `Target` e a compilação são considerados como com falha.<br /><br /> As versões do .NET Framework antes da 4.5 ofereciam suporte somente aos valores `true` e `false`.<br /><br /> Para obter mais informações, consulte [Como: Ignorar erros nas tarefas](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Tópicos relacionados

|Title|Descrição|
|-----------|-----------------|
|[Tarefa BscMake](../msbuild/bscmake-task.md)|Encapsula a ferramenta Utilitário de Manutenção de Informações de Procura da Microsoft (*bscmake.exe*).|
|[Tarefa cl](../msbuild/cl-task.md)|Envolve a ferramenta de compilador C++*(cl.exe).*|
|[Tarefa CPPClean](../msbuild/cppclean-task.md)|Exclui os arquivos temporários que o MSBuild cria quando um projeto C++ é construído.|
|[Tarefa ClangCompile](../msbuild/clangcompile-task.md)|Envolve a ferramenta do compilador C++*(clang.exe*).|
|[Tarefa CustomBuild](../msbuild/custombuild-task.md)|Envolve a ferramenta do compilador C++*(cmd.exe*).|
|[Tarefa FXC](../msbuild/fxc-task.md)|Use os compiladores de sombreador HLSL no processo de compilação.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Lê tlogs antigos, grava novos tlogs e retorna um conjunto de itens não atualizados. (tarefa auxiliar)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Obtém o nome do arquivo de saída para cl e outras ferramentas, que permitem especificar somente o diretório de saída ou o nome de arquivo completo, ou nada. (tarefa auxiliar)|
|[Tarefa LIB](../msbuild/lib-task.md)|Envolve a ferramenta Microsoft 32-Bit Library Manager *(lib.exe).*|
|[Tarefa de link](../msbuild/link-task.md)|Envolve a ferramenta de linker C++*(link.exe*).|
|[Tarefa MIDL](../msbuild/midl-task.md)|Envolve a ferramenta de compilador Microsoft Interface Definition Language (MIDL)*(midl.exe).*|
|[Tarefa MT](../msbuild/mt-task.md)|Envolve a Ferramenta de Manifesto microsoft *(mt.exe).*|
|[Tarefa MultiToolTask](../msbuild/multitooltask-task.md)|Sem descrição.|
|[Tarefa ParallelCustomBuild](../msbuild/parallelcustombuild-task.md)|Executar instâncias paralelas da [tarefa CustomBuild](../msbuild/custombuild-task.md).|
|[tarefa RC](../msbuild/rc-task.md)|Envolve a ferramenta Microsoft Windows Resource Compiler *(rc.exe).*|
|[Tarefa SetEnv](../msbuild/setenv-task.md)|Define ou exclui o valor de uma variável de ambiente especificada.|
|[Classe base trackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Herda de [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[Tarefa VCMessage](../msbuild/vcmessage-task.md)|Logs de mensagens de erro e mensagens de aviso durante uma compilação. (Não pode ser estendida. Somente para uso interno.)|
|[Classe base VCToolTask](../msbuild/vctooltask-base-class.md)|Herda de [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[Tarefa XDCMake](../msbuild/xdcmake-task.md)|Envolve a ferramenta Documentação XML *(xdcmake.exe),* que mescla arquivos xml de comentário de documento *(.xdc)* em um arquivo *.xml.*|
|[Tarefa XSD](../msbuild/xsd-task.md)|Envolve a ferramenta XML Schema Definition *(xsd.exe),* que gera esquemas ou arquivos de classe a partir de uma fonte. *Veja a nota abaixo.*|
|[Referência do MSBuild](../msbuild/msbuild-reference.md)|Descreve os elementos do sistema MSBuild.|
|[Tarefas](../msbuild/msbuild-tasks.md)|Descreve tarefas que são unidades de código que podem ser combinadas para produzirem uma compilação.|
|[Redação de tarefas](../msbuild/task-writing.md)|Descreve como criar uma tarefa.|

> [!NOTE]
> A partir do Visual Studio 2017, o suporte a projetos em C++ para *xsd.exe* foi preterido. Você ainda pode usar as APIs **Microsoft.VisualC.CppCodeProvider** manualmente adicionando *CppCodeProvider.dll* ao cache de assembly global.
