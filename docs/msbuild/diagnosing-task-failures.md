---
title: Diagnosticando falhas de tarefas | Microsoft Docs
description: Saiba como diagnosticar falhas de tarefas do MSBuild identificando a tarefa com falha, o nome da ferramenta e outras informações.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: eaf55cc529be8fc61e05d1a76096e26d965aa136
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796466"
---
# <a name="diagnosing-task-failures"></a>Diagnosticar falhas de tarefas

`MSB6006` é emitido quando uma <xref:Microsoft.Build.Utilities.ToolTask> classe derivada – executa um processo de ferramenta que retorna um código de saída diferente de zero se a tarefa não registrou um erro mais específico.

## <a name="identifying-the-failing-task"></a>Identificando a tarefa com falha

Quando você encontrar um erro de tarefa, a primeira etapa é identificar a tarefa que está falhando.

O texto do erro especifica o nome da ferramenta (um nome amigável fornecido pela implementação da tarefa <xref:Microsoft.Build.Utilities.ToolTask.ToolName> ou o nome do executável) e o código de saída numérico. Por exemplo, no

```text
error MSB6006: "custom tool" exited with code 1.
```

O nome da ferramenta é `custom tool` e o código de saída é `1` .

### <a name="command-line-builds"></a>Compilações de linha de comando

Se a compilação tiver sido configurada para incluir um resumo (o padrão), o resumo terá a seguinte aparência:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Esse resultado indica que o erro ocorreu em uma tarefa definida na linha 19 do arquivo `S:\MSB6006_demo\MSB6006_demo.csproj` , em um destino chamado `InvokeToolTask` , no projeto `S:\MSB6006_demo\MSB6006_demo.csproj` .

### <a name="in-visual-studio"></a>No Visual Studio

As mesmas informações estão disponíveis na lista de erros do Visual Studio nas colunas `Project` , `File` e `Line` .

## <a name="finding-more-failure-information"></a>Encontrando mais informações sobre a falha

Esse erro é emitido quando a tarefa não registrou um erro específico. A falha em registrar um erro geralmente ocorre porque a tarefa não está configurada para entender o formato de erro emitido pela ferramenta que ele chama.

Ferramentas bem comportadas geralmente emitem algumas informações contextuais ou de erro para sua saída padrão ou fluxo de erro, e as tarefas capturam e registram essas informações por padrão. Examine as entradas de log antes que o erro tenha ocorrido para obter informações adicionais. A execução da compilação com um nível de log superior pode ser necessária para preservar essas informações.

## <a name="next-steps"></a>Próximas etapas

Espero que o contexto adicional ou os erros identificados no log revelem a causa raiz do problema.

Se não tiverem, talvez você precise restringir as possíveis causas examinando as propriedades e os itens que são entradas para a tarefa com falha.
