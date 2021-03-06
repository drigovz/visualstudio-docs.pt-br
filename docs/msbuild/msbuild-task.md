---
title: Tarefa do MSBuild | Microsoft Docs
description: Saiba como a tarefa do MSBuild usa o mesmo processo do MSBuild para criar projetos filho de outro projeto do MSBuild.
ms.custom: SEO-VS-2020
ms.date: 07/30/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f8241188b484447f94c60aa0e0c9bf05e477dd39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878273"
---
# <a name="msbuild-task"></a>tarefa MSBuild

Cria projetos do MSBuild de outro projeto do MSBuild.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `MSBuild`.

| Parâmetro | Descrição |
|-----------------------------------| - |
| `BuildInParallel` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, os projetos especificados no parâmetro `Projects` serão criados em paralelo, se possível. O padrão é `false`. |
| `Projects` | Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os arquivos de projeto para compilar. |
| `Properties` | Parâmetro `String` opcional.<br /><br /> Uma lista delimitada por ponto-e-vírgula de pares de nome/valor de propriedade para aplicar como propriedades globais para o projeto filho. Quando você especifica esse parâmetro, é funcionalmente equivalente a definir propriedades que têm a opção **-Property** quando você cria com [*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Por exemplo:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Quando você passa Propriedades para o projeto por meio do `Properties` parâmetro, o MSBuild pode criar uma nova instância do projeto, mesmo que o arquivo de projeto já tenha sido carregado. O MSBuild cria uma única instância de projeto para um determinado caminho de projeto e um conjunto exclusivo de propriedades globais. Por exemplo, esse comportamento permite criar várias tarefas do MSBuild que chamam *myproject.proj*, com Configuration=Release, e você obtém uma única instância do *myproject.proj* (se não houver propriedades exclusivas especificadas na tarefa). Se você especificar uma propriedade que ainda não foi vista pelo MSBuild, o MSBuild criará uma nova instância do projeto, que pode ser criada em paralelo a outras instâncias do projeto. Por exemplo, uma configuração de versão poderia ser compilada ao mesmo tempo como uma configuração de depuração.|
| `RebaseOutputs` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, os caminhos relativos dos itens de saída de destino de projetos de compilação terão seus caminhos ajustados para serem relativos ao projeto de chamada. O padrão é `false`. |
| `RemoveProperties` | Parâmetro `String` opcional.<br /><br /> Especifica o conjunto de propriedades globais para remover. |
| `RunEachTargetSeparately` | Parâmetro `Boolean` opcional.<br /><br /> Se `true` , a tarefa do MSBuild invocará cada destino na lista passada para o MSBuild, um de cada vez, em vez de ao mesmo tempo. Definir esse parâmetro como `true` garante que os destinos subsequentes sejam chamados mesmo se os destinos chamados anteriormente tiverem falhado. Caso contrário, um erro de build pararia a invocação de todos os destinos subsequentes. O padrão é `false`. |
| `SkipNonexistentProjects` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, os arquivos de projeto que não existem no disco serão ignorados. Caso contrário, esses projetos causarão um erro. |
|`SkipNonexistentTargets`|Parâmetro `Boolean` opcional.<br /><br /> Se `true` , arquivos de projeto existentes, mas não contiverem o nome, `Targets` serão ignorados. Caso contrário, esses projetos causarão um erro. Introduzido no MSBuild 15,5.|
| `StopOnFirstFailure` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, quando um dos projetos falhar em compilar, os projetos não serão mais compilados. Atualmente isso não tem suporte na criação em paralelo (com vários processadores). |
| `TargetAndPropertyListSeparators` | Parâmetro `String[]` opcional.<br /><br /> Especifica uma lista de destinos e de propriedades como metadados de item `Project`). Separadores não serão escapados antes do processamento. Por exemplo, %3B (um escape ';') será tratado como se não fosse escapado ';'. |
| `TargetOutputs` | Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` de saída opcional somente leitura.<br /><br /> Retorna as saídas dos destinos compilados de todos os arquivos de projeto. Somente as saídas de destinos que foram especificados são retornadas, não as saídas que podem existir em destinos dos quais esses destinos dependem.<br /><br /> O parâmetro `TargetOutputs` também contém os metadados a seguir:<br /><br /> -   `MSBuildSourceProjectFile`: O arquivo de projeto do MSBuild que contém o destino que define as saídas.<br />-   `MSBuildSourceTargetName`: o destino que define as saídas. **Observação:** para identificar as saídas de cada arquivo de projeto ou destino separadamente, execute a tarefa `MSBuild` separadamente para cada arquivo de projeto ou destino. Se você executar a tarefa `MSBuild` apenas uma vez para compilar todos os arquivos de projeto, as saídas de todos os destinos serão coletadas em uma matriz. |
| `Targets` | Parâmetro `String` opcional.<br /><br /> Especifica o destino ou destinos para build nos arquivos de projeto. Use uma lista separada por ponto-e-vírgula de nomes de destino. Se nenhum destino for especificado na tarefa `MSBuild`, os destinos padrão especificados nos arquivos de projeto serão compilados. **Observação:** os destinos devem ocorrer em todos os arquivos de projeto. Caso contrário, ocorrerá um erro de build. |
| `ToolsVersion` | Parâmetro `String` opcional.<br /><br /> Especifica o `ToolsVersion` a ser usado ao compilar projetos passados para essa tarefa.<br /><br /> Permite que uma tarefa do MSBuild crie um projeto que se destina a uma versão diferente da .NET Framework do que aquela especificada no projeto. Os valores válidos são `2.0`, `3.0` e `3.5`. O valor padrão é `3.5`. |

## <a name="remarks"></a>Comentários

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

 Ao contrário do uso da [tarefa Exec](../msbuild/exec-task.md) para iniciar *MSBuild.exe*, essa tarefa usa o mesmo processo do MSBuild para criar os projetos filho. A lista de destinos já compilados que pode ser ignorada é compartilhada entre as compilações pai e filho. Essa tarefa também é mais rápida porque nenhum novo processo do MSBuild é criado.

 Essa tarefa pode processar não somente arquivos de projeto, mas também arquivos de solução.

 Qualquer configuração exigida pelo MSBuild para permitir que projetos sejam compilados ao mesmo tempo, mesmo se a configuração envolver a infraestrutura remota (por exemplo, portas, protocolos, tempos limite, repetições e assim por diante), deve ser configurável usando um arquivo de configuração. Quando possível, itens de configuração deverão ser capazes de ser especificados como parâmetros de tarefa na tarefa `MSBuild`.

 A partir do MSBuild 3,5, os projetos de solução agora TargetOutputsm de todos os subprojetos que ele cria.

## <a name="pass-properties-to-projects"></a>Passar propriedades para projetos

 Em versões do MSBuild anteriores ao MSBuild 3,5, passar diferentes conjuntos de propriedades para diferentes projetos listados no item do MSBuild era desafiador. Se você usou o atributo Properties da [tarefa MSBuild](../msbuild/msbuild-task.md), sua configuração foi aplicada a todos os projetos que estão sendo compilados, a menos que você tenha feito o lote da [tarefa MSBuild](../msbuild/msbuild-task.md) e tenha fornecido condicionalmente propriedades diferentes para cada projeto na lista de itens.

 O MSBuild 3,5, no entanto, fornece dois novos itens de metadados reservados, propriedades e adicionais, que fornecem uma maneira flexível de passar propriedades diferentes para projetos diferentes que estão sendo compilados usando a [tarefa do MSBuild](../msbuild/msbuild-task.md).

> [!NOTE]
> Esses novos itens de metadados são aplicáveis somente aos itens passados no atributo Projects da [tarefa MSBuild](../msbuild/msbuild-task.md).

## <a name="multi-processor-build-benefits"></a>Benefícios da compilação multiprocessador

 Um dos principais benefícios de usar esses novos metadados ocorre quando você compila seus projetos em paralelo em um sistema com vários processadores. Os metadados permitem consolidar todos os projetos em uma única chamada de [tarefa do MSBuild](../msbuild/msbuild-task.md) sem ter que executar nenhuma tarefa de envio em lote ou de MSBuild condicional. E quando você chamar apenas uma única [tarefa do MSBuild](../msbuild/msbuild-task.md), todos os projetos listados no atributo Projects serão criados em paralelo. (No entanto, somente se o `BuildInParallel=true` atributo estiver presente na [tarefa do MSBuild](../msbuild/msbuild-task.md).) Para obter mais informações, consulte [criar vários projetos em paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Metadados de propriedades

 Quando especificados, os metadados de propriedades substituem o parâmetro Propriedades da tarefa, enquanto os metadados de [AdditionalProperties](#additionalproperties-metadata) são acrescentados às definições do parâmetro.

 Um cenário comum é quando você está criando vários arquivos de solução usando a [tarefa do MSBuild](../msbuild/msbuild-task.md), usando apenas configurações de compilação diferentes. Você pode querer compilar a solução a1 usando a configuração de depuração e compilar a solução a2 usando a configuração de versão. No MSBuild 2,0, esse arquivo de projeto seria semelhante ao seguinte:

> [!NOTE]
> No exemplo a seguir, "…" representa arquivos adicionais da solução.

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>
    </Target>
</Project>
```

 No entanto, usando os metadados de propriedades, você pode simplificar isso para usar uma única [tarefa do MSBuild](../msbuild/msbuild-task.md), conforme mostrado a seguir:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <Properties>Configuration=Debug</Properties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"/>
    </Target>
</Project>
```

 \- ou –

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln..."/>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Debug"/>
    </Target>
</Project>
```

## <a name="additionalproperties-metadata"></a>Metadados de AdditionalProperties

 Considere o cenário a seguir em que você está criando dois arquivos de solução usando a [tarefa MSBuild](../msbuild/msbuild-task.md), usando a configuração de versão, mas uma usando a arquitetura x86 e a outra usando a arquitetura IA64. No MSBuild 2,0, você precisaria criar várias instâncias da [tarefa MSBuild](../msbuild/msbuild-task.md): uma para compilar o projeto usando a configuração de versão com a arquitetura x86, a outra usando a configuração de versão com a arquitetura IA64. Seu arquivo de projeto seria semelhante ao seguinte:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Release;
          Architecture=x86"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;
          Architecture=ia64"/>
    </Target>
</Project>
```

 Usando os metadados adicionais DoProperties, você pode simplificar isso para usar uma única [tarefa do MSBuild](../msbuild/msbuild-task.md) usando o seguinte:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <AdditionalProperties>Architecture=x86
              </AdditionalProperties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <AdditionalProperties>Architecture=ia64
              </AdditionalProperties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Release"/>
    </Target>
</Project>
```

## <a name="example"></a>Exemplo

 O exemplo a seguir usa a tarefa `MSBuild` para compilar projetos especificados pela coleção de itens `ProjectReferences`. As saídas de destino resultantes são armazenadas na coleção de itens `AssembliesBuiltByChildProjects`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ProjectReferences Include="*.*proj" />
    </ItemGroup>

    <Target Name="BuildOtherProjects">
        <MSBuild
            Projects="@(ProjectReferences)"
            Targets="Build">
            <Output
                TaskParameter="TargetOutputs"
                ItemName="AssembliesBuiltByChildProjects" />
        </MSBuild>
    </Target>

</Project>
```

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
