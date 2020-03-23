---
title: Tarefas do MSBuild | Microsoft Docs
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
ms.openlocfilehash: b065ea8cdaea2e2b39aa78a666ea0348f7b254ae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633129"
---
# <a name="msbuild-tasks"></a>tarefas MSBuild

Uma plataforma de build precisa de capacidade para executar qualquer número de ações durante o processo de build. O MSBuild usa *tarefas* para executar essas ações. Uma tarefa é uma unidade de código executável usada pelo MSBuild para executar operações de construção atômica.

## <a name="task-logic"></a>Lógica da tarefa

 O formato de arquivo de projeto MSBuild XML não pode executar totalmente as operações de construção por conta própria, portanto, a lógica da tarefa deve ser implementada fora do arquivo do projeto.

 A lógica de execução de uma tarefa é implementada como uma classe do .NET que implementa a interface <xref:Microsoft.Build.Framework.ITask>, que é definida no namespace <xref:Microsoft.Build.Framework>.

 A classe de tarefa também define os parâmetros de entrada e saída disponíveis para a tarefa no arquivo de projeto. Todas as propriedades não-abstratas estáticas definidas pelo público expostas pela classe de tarefas podem receber valores no arquivo do projeto, colocando um atributo correspondente com o mesmo nome no elemento [Tarefa](../msbuild/task-element-msbuild.md) e definindo seu valor como mostrado nos exemplos posteriores deste artigo.

 Você pode escrever sua própria tarefa por meio da criação de uma classe gerenciada que implementa a interface <xref:Microsoft.Build.Framework.ITask>. Para obter mais informações, consulte [Redação de tarefas](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Executar uma tarefa de um arquivo de projeto

 Antes de executar uma tarefa no seu arquivo de projeto, primeiro você deve mapear o tipo no assembly que implementa a tarefa para o nome da tarefa com o elemento [UsingTask](../msbuild/usingtask-element-msbuild.md). Isso permite que o MSBuild saiba onde procurar a lógica de execução da sua tarefa quando encontrá-la no arquivo do projeto.

 Para executar uma tarefa em um arquivo de projeto MSBuild, crie um `Target` elemento com o nome da tarefa como filho de um elemento. Se uma tarefa aceita parâmetros, eles são passados como atributos do elemento.

 Listas de itens do MSBuild e propriedades podem ser usadas como parâmetros. Por exemplo, o código `MakeDir` a seguir chama `Directories` a tarefa `MakeDir` e define o `BuildDir` valor da propriedade do objeto igual ao valor da propriedade:

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

 O MSBuild vem com muitas tarefas, como [copy](../msbuild/copy-task.md), que copia arquivos, [MakeDir](../msbuild/makedir-task.md), que cria diretórios, e [CSC](../msbuild/csc-task.md), que compila arquivos de código fonte C#. Para obter uma lista completa de tarefas e informações de uso disponíveis, consulte [Referência tarefa](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Tarefas substituídas

 O MSBuild procura tarefas em vários locais. O primeiro local está em arquivos com a extensão *. SubstituiçãoTarefas* armazenadas nos diretórios framework .NET. As tarefas nesses arquivos substituem quaisquer outras tarefas com os mesmos nomes, incluindo tarefas no arquivo de projeto. O segundo local está nos arquivos com a extensão *.Tasks* nos diretórios do .NET Framework. Se a tarefa não for encontrada em um desses locais, a tarefa no arquivo de projeto será usada.

## <a name="see-also"></a>Confira também

- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Redação de tarefas](../msbuild/task-writing.md)
- [Tarefas inline](../msbuild/msbuild-inline-tasks.md)
