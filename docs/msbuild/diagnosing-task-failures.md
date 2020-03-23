---
title: Diagnóstico de falhas de tarefa | Microsoft Docs
ms.date: 09/25/2019
ms.topic: troubleshooting
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89dcb8bddf2c92406ad5eff952d1f4050d7f9262
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593272"
---
# <a name="diagnosing-task-failures"></a>Diagnosticar falhas de tarefas

`MSB6006`é emitido quando <xref:Microsoft.Build.Utilities.ToolTask>uma classe derivada executa um processo de ferramenta que retorna um código de saída não zero se a tarefa não registrar um erro mais específico.

## <a name="identifying-the-failing-task"></a>Identificando a tarefa falha

Quando você encontra um erro de tarefa, o primeiro passo é identificar a tarefa que está falhando.

O texto do erro especifica o nome da ferramenta (um nome amigável <xref:Microsoft.Build.Utilities.ToolTask.ToolName> fornecido pela implementação da tarefa ou o nome do executável) e o código de saída numérico. Por exemplo, no

```text
error MSB6006: "custom tool" exited with code 1.
```

O nome `custom tool` da ferramenta é `1`e o código de saída é .

### <a name="command-line-builds"></a>Compilações de linha de comando

Se a compilação foi configurada para incluir um resumo (o padrão), o resumo ficará assim:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Este resultado indica que o erro ocorreu em uma tarefa `S:\MSB6006_demo\MSB6006_demo.csproj`definida na `InvokeToolTask`linha 19 `S:\MSB6006_demo\MSB6006_demo.csproj`do arquivo , em um alvo nomeado , no projeto .

### <a name="in-visual-studio"></a>No Visual Studio

As mesmas informações estão disponíveis na lista `Project`de `File`erros `Line`do Visual Studio nas colunas e .

## <a name="finding-more-failure-information"></a>Encontrando mais informações de falha

Este erro é emitido quando a tarefa não registra um erro específico. A falha ao registrar um erro é muitas vezes porque a tarefa não está configurada para entender o formato de erro emitido pela ferramenta que ele chama.

Ferramentas bem comportadas geralmente emitem algumas informações contextuais ou de erro para seu fluxo de saída ou erro padrão, e as tarefas capturam e registram essas informações por padrão. Procure nas entradas de registro antes que o erro ocorreu para obter informações adicionais. Reexecutar a compilação com um nível de log mais alto pode ser necessário para preservar essas informações.

## <a name="next-steps"></a>Próximas etapas

Espero que o contexto adicional ou erros identificados no registro revelem a causa raiz do problema.

Se não o fizerem, você pode ter que reduzir as causas potenciais examinando as propriedades e itens que são entradas para a tarefa falha.
