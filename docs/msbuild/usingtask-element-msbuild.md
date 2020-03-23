---
title: Elemento UsingTask (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22d61fe30e9eb68697f073ca0bcfbcc515e513dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79431443"
---
# <a name="usingtask-element-msbuild"></a>Elemento UsingTask (MSBuild)

Mapeia a tarefa que é referenciada em um elemento [Tarefa](../msbuild/task-element-msbuild.md) para o assembly que contém a implementação de tarefas.

 \<Project> \<UsingTask>

## <a name="syntax"></a>Sintaxe

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> Ao contrário das propriedades *first* `UsingTask` e itens, o `TaskName` primeiro elemento que se aplica a um será usado; para substituir tarefas que `UsingTask` você deve definir um novo *antes* do existente.

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`AssemblyName`|O atributo `AssemblyName` ou o `AssemblyFile` é necessário.<br /><br /> O nome do assembly a ser carregado. O atributo `AssemblyName` aceita os assemblies de nomes fortes, embora não seja necessário com nomes fortes. Usar esse atributo é equivalente a carregar um assembly usando o método <xref:System.Reflection.Assembly.Load%2A> no .NET.<br /><br /> Você não poderá usar esse atributo se o atributo `AssemblyFile` for usado.|
|`AssemblyFile`|O atributo `AssemblyName` ou `AssemblyFile` é necessário.<br /><br /> O caminho do arquivo do assembly. Esse atributo aceita caminhos completos ou caminhos relativos. Caminhos relativos são relativos ao diretório do arquivo de projeto ou arquivo de destino no qual o elemento `UsingTask` é declarado. Usar esse atributo é equivalente a carregar um assembly usando o método <xref:System.Reflection.Assembly.LoadFrom%2A> no .NET.<br /><br /> Você não poderá usar esse atributo se o atributo `AssemblyName` for usado.|
|`TaskFactory`|Atributo opcional.<br /><br /> Especifica a classe no assembly que é responsável por gerar instâncias do nome `Task` especificado.  O usuário também pode especificar um `Task` como um elemento filho que a fábrica de tarefa recebe e usa para gerar a tarefa. O conteúdo de `Task` é específico para a fábrica da tarefa.|
|`TaskName`|Atributo obrigatório.<br /><br /> O nome da tarefa para referência de um assembly. Se for possível usar ambiguidades, esse atributo sempre deverá especificar namespaces completos. Se houver ambiguidades, o MSBuild escolherá uma correspondência arbitrária, que poderá produzir resultados inesperados.|
|`Condition`|Atributo opcional.<br /><br /> A condição que será avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|O conjunto de parâmetros que aparecem na tarefa que é gerada pelo `TaskFactory` especificado.|
|[Tarefa](../msbuild/task-element-msbuild.md)|Os dados que são passados para o `TaskFactory` para gerar uma instância da tarefa.|

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Elemento raiz necessário de um arquivo de projeto MSBuild. |

## <a name="remarks"></a>Comentários

 Variáveis de ambiente, propriedades de linha de comando, propriedades no nível do projeto e itens no nível do projeto podem ser referenciadas no elemento `UsingTask` incluído no arquivo de projeto, explicitamente ou por meio de um arquivo de projeto importado. Para obter mais informações, consulte [Tarefas](../msbuild/msbuild-tasks.md).

> [!NOTE]
> Propriedades e itens em nível de projeto `UsingTask` não têm significado se o elemento vem de um dos arquivos *.tasks* que estão registrados globalmente no mecanismo MSBuild. Valores no nível do projeto não são globais ao MSBuild.

 No MSBuild 4.0, o uso de tarefas pode ser carregado a partir de arquivos *de .overridetask.*

O conjunto que contém a tarefa `Task` personalizada é carregado quando o primeiro é usado.

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra como usar o elemento `UsingTask` com um atributo `AssemblyName`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task>
      ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra como usar o elemento `UsingTask` com um atributo `AssemblyFile`.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
