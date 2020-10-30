---
title: Tarefas do MSBuild específicas para C++ | Microsoft Docs
description: Consulte tarefas do MSBuild que estão disponíveis quando o C++ é instalado, que o MSBuild usa ao criar código C++.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b1d1a40c9e173ec6dd7cf07e0af0ca68f58efbb0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049043"
---
# <a name="msbuild-tasks-specific-to-c"></a>Tarefas do MSBuild específicas para C++

Tarefas fornecem o código que é executado durante o processo de build. Quando o C++ é instalado, as seguintes tarefas estão disponíveis, além das instaladas com o MSBuild. Para obter mais informações, consulte [visão geral do MSBuild (C++)](/cpp/build/msbuild-visual-cpp-overview).

 Além dos parâmetros para cada tarefa, todas as tarefas também têm os seguintes parâmetros.

| Parâmetro | Descrição |
|-------------------| - |
| `Condition` | Parâmetro `String` opcional.<br /><br /> Uma `Boolean` expressão que o mecanismo MSBuild usa para determinar se esta tarefa será executada. Para obter informações sobre as condições com suporte pelo MSBuild, consulte [condições](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parâmetro opcional. Pode conter um dos seguintes valores:<br /><br /> -   **WarnAndContinue** ou **true** . Quando uma tarefa falha, as tarefas subsequentes no elemento de [Destino](../msbuild/target-element-msbuild.md) e a compilação continuam em execução, e todos os erros da tarefa são tratados como avisos<br />-   **ErrorAndContinue** . Quando uma tarefa falha, as tarefas subsequentes no elemento de `Target` e o build continuam em execução e todos os erros da tarefa são tratados como erros.<br />-   **ErrorAndStop** ou **false** (padrão). Quando uma tarefa falha, as tarefas restantes do elemento de `Target` e o build não são executadas e todo o elemento `Target` e a compilação são considerados como com falha.<br /><br /> As versões do .NET Framework antes da 4.5 ofereciam suporte somente aos valores `true` e `false`.<br /><br /> Para obter mais informações, consulte [como ignorar erros em tarefas](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Tarefa BscMake](../msbuild/bscmake-task.md)|Encapsula a ferramenta Utilitário de Manutenção de Informações de Procura da Microsoft ( *bscmake.exe* ).|
|[tarefa CL](../msbuild/cl-task.md)|Encapsula a ferramenta de compilador do C++ ( *cl.exe* ).|
|[Tarefa CPPClean](../msbuild/cppclean-task.md)|Exclui os arquivos temporários que o MSBuild cria quando um projeto C++ é compilado.|
|[Tarefa ClangCompile](../msbuild/clangcompile-task.md)|Encapsula a ferramenta de compilador do C++ ( *clang.exe* ).|
|[Tarefa CustomBuild](../msbuild/custombuild-task.md)|Encapsula a ferramenta de compilador do C++ ( *cmd.exe* ).|
|[Tarefa FXC](../msbuild/fxc-task.md)|Use os compiladores de sombreador HLSL no processo de compilação.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Lê tlogs antigos, grava novos tlogs e retorna um conjunto de itens não atualizados. (tarefa auxiliar)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Obtém o nome do arquivo de saída para cl e outras ferramentas, que permitem especificar somente o diretório de saída ou o nome de arquivo completo, ou nada. (tarefa auxiliar)|
|[tarefa LIB](../msbuild/lib-task.md)|Encapsula a ferramenta Microsoft 32-bit Library Manager ( *lib.exe* ).|
|[tarefa de vinculação](../msbuild/link-task.md)|Encapsula a ferramenta do vinculador C++ ( *link.exe* ).|
|[tarefa MIDL](../msbuild/midl-task.md)|Encapsula a ferramenta de compilador de linguagem IDL da Microsoft (MIDL) ( *midl.exe* ).|
|[tarefa MT](../msbuild/mt-task.md)|Encapsula a ferramenta de manifesto da Microsoft ( *mt.exe* ).|
|[Tarefa MultiToolTask](../msbuild/multitooltask-task.md)|Sem descrição.|
|[Tarefa ParallelCustomBuild](../msbuild/parallelcustombuild-task.md)|Executar instâncias paralelas da [tarefa CustomBuild](../msbuild/custombuild-task.md).|
|[tarefa RC](../msbuild/rc-task.md)|Encapsula a ferramenta do compilador de recursos do Microsoft Windows ( *rc.exe* ).|
|[Tarefa SetEnv](../msbuild/setenv-task.md)|Define ou exclui o valor de uma variável de ambiente especificada.|
|[Classe base TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Herda de [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[tarefa VCMessage](../msbuild/vcmessage-task.md)|Logs de mensagens de erro e mensagens de aviso durante uma compilação. (Não pode ser estendida. Somente para uso interno.)|
|[Classe base VCToolTask](../msbuild/vctooltask-base-class.md)|Herda de [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[tarefa XDCMake](../msbuild/xdcmake-task.md)|Encapsula a ferramenta de documentação XML ( *xdcmake.exe* ), que mescla arquivos de comentário de documento XML ( *. xdc* ) em um arquivo *. xml* .|
|[tarefa XSD](../msbuild/xsd-task.md)|Encapsula a ferramenta de definição de esquema XML ( *xsd.exe* ), que gera arquivos de esquema ou classe de uma origem. *Veja a observação abaixo.*|
|[Referência do MSBuild](../msbuild/msbuild-reference.md)|Descreve os elementos do sistema MSBuild.|
|[Tarefas](../msbuild/msbuild-tasks.md)|Descreve tarefas que são unidades de código que podem ser combinadas para produzirem uma compilação.|
|[Produção de tarefas](../msbuild/task-writing.md)|Descreve como criar uma tarefa.|

> [!NOTE]
> A partir do Visual Studio 2017, o suporte a projetos em C++ para *xsd.exe* foi preterido. Você ainda pode usar as APIs **Microsoft.VisualC.CppCodeProvider** manualmente adicionando *CppCodeProvider.dll* ao cache de assembly global.
