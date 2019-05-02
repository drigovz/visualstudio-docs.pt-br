---
title: Tarefa FXC | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.fxc
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), FXC task
- FXC task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 65819f1625477effab024055828301b26ab5804a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931475"
---
# <a name="fxc-task"></a>Tarefa FXC

Use os compiladores de sombreador HLSL no processo de compilação.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros da tarefa **FXC**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Parâmetro opcional **String[]**.<br/><br/>Especifica um ou mais diretórios a serem adicionados ao caminho de inclusão, separados por ponto e vírgula no caso de mais de um.<br/><br/>Use `/I[path]`.|
|**AdditionalOptions**|Parâmetro opcional **string**.|
|**AllResourcesBound**|Parâmetro opcional **bool**.<br/><br/>O compilador presumirá que todos os recursos aos quais um sombreador pode fazer referência estão associados e em bom estado para toda a execução do sombreador. Disponível para Shader Model 5.1 e posterior.<br/><br/>Use `/all_resources_bound`.|
|**AssemblerOutput**|Parâmetro opcional **string**.<br/><br/>Especifica o conteúdo do arquivo de saída de linguagem assembly.<br/><br/>Use `/Fc, /Fx`.<br/><br/>**NoListing**<br/>**AssemblyCode**, use `Fc`.<br/>**AssemblyCodeAndHex**, use `Fx`.|
|**AssemblerOutputFile**|Parâmetro opcional **string**.<br/><br/>Especifica o nome do arquivo para arquivo de listagem de código assembly.|
|**CompileD2DCustomEffect**|Parâmetro opcional **bool**.<br/><br/>Compile um efeito personalizado Direct2D que contém sombreadores de pixel. Não use um vértice ou efeito personalizado de computação.|
|**ConsumeExportFile**|Parâmetro opcional **string**.|
|**DisableOptimizations**|Parâmetro opcional **bool**.<br/><br/>Desabilitar otimizações.<br/><br/>`/Od` implica `/Gfp` mesmo que a saída não seja idêntica a `/Od /Gfp`.|
|**EnableDebuggingInformation**|Parâmetro opcional **bool**.<br/><br/>Habilitar informações de depuração.|
|**EnableUnboundedDescriptorTables**|Parâmetro opcional **bool**.<br/><br/>Informe ao compilador que um sombreador pode conter uma declaração de uma matriz de recursos com intervalo não associado. Disponível para Shader Model 5.1 e posterior.<br/><br/>Use `/enable_unbounded_descriptor_tables`.|
|**EntryPointName**|Parâmetro opcional **string**.<br/><br/>Especifica o nome do ponto de entrada para o sombreador.<br/><br/>Use `/E[name]`.|
|**GenerateExportFile**|Parâmetro opcional **string**.|
|**GenerateExportShaderProfile**|Parâmetro opcional **string**.|
|**HeaderFileOutput**|Parâmetro opcional **string**.<br/><br/>Especifica um nome para um arquivo de cabeçalho que contém código objeto.<br/><br/>Use `/Fh [name]`.|
|**ObjectFileOutput**|Parâmetro opcional **string**.<br/><br/>Especifica um nome para o arquivo-objeto.<br/><br/>Use `/Fo [name]`.|
|**PreprocessorDefinitions**|Parâmetro opcional **String[]**.<br/><br/>Define os símbolos de pré-processamento para o arquivo de origem.|
|**SetRootSignature**|Parâmetro opcional **string**.<br/><br/>Anexe a assinatura raiz ao código de bytes do sombreador. Disponível para Shader Model 5.0 e posterior.<br/><br/>Use `/setrootsignature`.|
|**ShaderModel**|Parâmetro opcional **string**.<br/><br/>Especifica o modelo de sombreador. Alguns tipos de sombreador podem ser usados apenas com modelos de sombreador recentes.<br/><br/>Use `/T [type]_[model]`.|
|**ShaderType**|Parâmetro opcional **string**.<br/><br/>Especifica o tipo de sombreador.<br/><br/>Use `/T [type]_[model]`.<br/><br/>**Effect**, use `fx`.<br/>**Vertex**, use `vs`.<br/>**Pixel**, use `ps`.<br/>**Geometry**, use `gs`.<br/>**Hull**, use `hs`.<br/>**Domain**, use `ds`.<br/>**Compute**, use `cs`.<br/>**Library**, use `lib`.<br/>**RootSignature**, gere o Objeto de Assinatura Raiz.|
|**Source**|Parâmetro obrigatório **ITaskItem**.|
|**SuppressStartupBanner**|Parâmetro opcional **bool**.<br/><br/>Suprime a exibição da faixa de inicialização e das mensagens informativas.<br/><br/>Use `/nologo`.|
|**TrackerLogDirectory**|Parâmetro opcional **string**.|
|**TreatWarningAsError**|Parâmetro opcional **bool**.<br/><br/>Trata todos os avisos do compilador como erros.<br/><br/>Para um novo projeto, talvez seja melhor usar `/WX` em todas as compilações. Resolver todos os avisos assegurará o menor número possível de defeitos de código difíceis de localizar.|
|**VariableName**|Parâmetro opcional **string**.<br/><br/>Especifica um nome para o nome de variável no arquivo de cabeçalho.<br/><br/>Use `/Vn [name]`.|

## <a name="see-also"></a>Consulte também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)