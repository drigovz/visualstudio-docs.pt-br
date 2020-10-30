---
title: Tarefas do MSBuild | Microsoft Docs
description: Saiba como o MSBuild usa tarefas ou unidades de código executável que executam operações de compilação atômicas, durante o processo de compilação.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76b359eebe0f4a22bef3ff6c6742a5134aa4520c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049045"
---
# <a name="msbuild-tasks"></a>tarefas MSBuild

Uma plataforma de build precisa de capacidade para executar qualquer número de ações durante o processo de build. O MSBuild usa *tarefas* para executar essas ações. Uma tarefa é uma unidade de código executável usada pelo MSBuild para executar operações de compilação atômica.

## <a name="task-logic"></a>Lógica da tarefa

 O formato de arquivo de projeto XML do MSBuild não pode executar operações de compilação por conta própria, portanto, a lógica de tarefa deve ser implementada fora do arquivo de projeto.

 A lógica de execução de uma tarefa é implementada como uma classe do .NET que implementa a interface <xref:Microsoft.Build.Framework.ITask>, que é definida no namespace <xref:Microsoft.Build.Framework>.

 A classe de tarefa também define os parâmetros de entrada e saída disponíveis para a tarefa no arquivo de projeto. Todas as propriedades não-abstratas não estáticas de tabela pública expostas pela classe Task podem receber valores no arquivo de projeto colocando um atributo correspondente com o mesmo nome no elemento [Task](../msbuild/task-element-msbuild.md) e definindo seu valor, conforme mostrado nos exemplos mais adiante neste artigo.

 Você pode escrever sua própria tarefa por meio da criação de uma classe gerenciada que implementa a interface <xref:Microsoft.Build.Framework.ITask>. Para obter mais informações, consulte [gravação de tarefas](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Executar uma tarefa de um arquivo de projeto

 Antes de executar uma tarefa no seu arquivo de projeto, primeiro você deve mapear o tipo no assembly que implementa a tarefa para o nome da tarefa com o elemento [UsingTask](../msbuild/usingtask-element-msbuild.md). Isso permite que o MSBuild saiba onde procurar a lógica de execução da sua tarefa ao encontrá-la em seu arquivo de projeto.

 Para executar uma tarefa em um arquivo de projeto do MSBuild, crie um elemento com o nome da tarefa como um filho de um `Target` elemento. Se uma tarefa aceita parâmetros, eles são passados como atributos do elemento.

 As listas e propriedades de item do MSBuild podem ser usadas como parâmetros. Por exemplo, o código a seguir chama a `MakeDir` tarefa e define o valor da `Directories` Propriedade do `MakeDir` objeto igual ao valor da `BuildDir` Propriedade:

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 As tarefas também podem retornar informações para o arquivo de projeto, que pode ser armazenado em itens ou propriedades para uso posterior. Por exemplo, o código a seguir chama a tarefa `Copy` e armazena as informações da propriedade de saída `CopiedFiles` na lista de itens `SuccessfullyCopiedFiles`.

```xml
<Target Name="CopyFiles">
    <Copy
        SourceFiles="@(MySourceFiles)"
        DestinationFolder="@(MyDestFolder)">
        <Output
            TaskParameter="CopiedFiles"
            ItemName="SuccessfullyCopiedFiles"/>
     </Copy>
</Target>
```

## <a name="included-tasks"></a>Tarefas incluídas

 O MSBuild é fornecido com muitas tarefas, como [Copy](../msbuild/copy-task.md), que copia arquivos, [MakeDir](../msbuild/makedir-task.md), que cria diretórios e [CSC](../msbuild/csc-task.md), que compila arquivos de código-fonte C#. Para obter uma lista completa de tarefas disponíveis e informações de uso, consulte [referência de tarefas](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Tarefas substituídas

 O MSBuild procura tarefas em vários locais. O primeiro local está em arquivos com a extensão *. OverrideTasks* armazenados nos diretórios .NET Framework. As tarefas nesses arquivos substituem quaisquer outras tarefas com os mesmos nomes, incluindo tarefas no arquivo de projeto. O segundo local está nos arquivos com a extensão *.Tasks* nos diretórios do .NET Framework. Se a tarefa não for encontrada em um desses locais, a tarefa no arquivo de projeto será usada.

## <a name="see-also"></a>Veja também

- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Produção de tarefas](../msbuild/task-writing.md)
- [Tarefas embutidas](../msbuild/msbuild-inline-tasks.md)
