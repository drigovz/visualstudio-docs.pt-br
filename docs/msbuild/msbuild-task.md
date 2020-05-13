---
title: Tarefa do MSBuild | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab54c5c523c833be60ef4b5d5088b6217a3111a5
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072574"
---
# <a name="msbuild-task"></a>tarefa MSBuild

Constrói projetos msbuild a partir de outro projeto MSBuild.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `MSBuild`.

| Parâmetro | Descrição |
|-----------------------------------| - |
| `BuildInParallel` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, os projetos especificados no parâmetro `Projects` serão criados em paralelo, se possível. O padrão é `false`. |
| `Projects` | Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os arquivos de projeto para compilar. |
| `Properties` | Parâmetro `String` opcional.<br /><br /> Uma lista delimitada por ponto-e-vírgula de pares de nome/valor de propriedade para aplicar como propriedades globais para o projeto filho. Quando você especifica este parâmetro, ele é funcionalmente equivalente a configuração de propriedades que têm o switch **-propriedade** quando você constrói com [*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Por exemplo:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Quando você passa propriedades para `Properties` o projeto através do parâmetro, o MSBuild pode criar uma nova instância do projeto, mesmo que o arquivo do projeto já tenha sido carregado. O MSBuild cria uma única instância de projeto para um determinado caminho de projeto e um conjunto único de propriedades globais. Por exemplo, esse comportamento permite criar várias tarefas do MSBuild que chamam *myproject.proj*, com Configuration=Release, e você obtém uma única instância do *myproject.proj* (se não houver propriedades exclusivas especificadas na tarefa). Se você especificar uma propriedade que ainda não foi vista pelo MSBuild, o MSBuild criará uma nova instância do projeto, que pode ser construída paralelamente a outras instâncias do projeto. Por exemplo, uma configuração de versão poderia ser compilada ao mesmo tempo como uma configuração de depuração.|
| `RebaseOutputs` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, os caminhos relativos dos itens de saída de destino de projetos de compilação terão seus caminhos ajustados para serem relativos ao projeto de chamada. O padrão é `false`. |
| `RemoveProperties` | Parâmetro `String` opcional.<br /><br /> Especifica o conjunto de propriedades globais para remover. |
| `RunEachTargetSeparately` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, a tarefa MSBuild invoca cada destino na lista passou para o MSBuild um de cada vez, em vez de ao mesmo tempo. Definir esse parâmetro como `true` garante que os destinos subsequentes sejam chamados mesmo se os destinos chamados anteriormente tiverem falhado. Caso contrário, um erro de build pararia a invocação de todos os destinos subsequentes. O padrão é `false`. |
| `SkipNonexistentProjects` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, os arquivos de projeto que não existem no disco serão ignorados. Caso contrário, esses projetos causarão um erro. |
|`SkipNonexistentTargets`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, arquivos de projeto que `Targets` existem, mas não contêm o nome serão ignorados. Caso contrário, esses projetos causarão um erro. Introduzido no MSBuild 15.5.|
| `StopOnFirstFailure` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, quando um dos projetos falhar em compilar, os projetos não serão mais compilados. Atualmente isso não tem suporte na criação em paralelo (com vários processadores). |
| `TargetAndPropertyListSeparators` | Parâmetro `String[]` opcional.<br /><br /> Especifica uma lista de destinos e de propriedades como metadados de item `Project`). Separadores não serão escapados antes do processamento. Por exemplo, %3B (um escape ';') será tratado como se não fosse escapado ';'. |
| `TargetOutputs` | Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` de saída opcional somente leitura.<br /><br /> Retorna as saídas dos destinos compilados de todos os arquivos de projeto. Somente as saídas de destinos que foram especificados são retornadas, não as saídas que podem existir em destinos dos quais esses destinos dependem.<br /><br /> O parâmetro `TargetOutputs` também contém os metadados a seguir:<br /><br /> -   `MSBuildSourceProjectFile`: O arquivo do projeto MSBuild que contém o destino que define as saídas.<br />-   `MSBuildSourceTargetName`: o destino que define as saídas. **Observação:** para identificar as saídas de cada arquivo de projeto ou destino separadamente, execute a tarefa `MSBuild` separadamente para cada arquivo de projeto ou destino. Se você executar a tarefa `MSBuild` apenas uma vez para compilar todos os arquivos de projeto, as saídas de todos os destinos serão coletadas em uma matriz. |
| `Targets` | Parâmetro `String` opcional.<br /><br /> Especifica o destino ou destinos para build nos arquivos de projeto. Use uma lista separada por ponto-e-vírgula de nomes de destino. Se nenhum destino for especificado na tarefa `MSBuild`, os destinos padrão especificados nos arquivos de projeto serão compilados. **Observação:** os destinos devem ocorrer em todos os arquivos de projeto. Caso contrário, ocorrerá um erro de build. |
| `ToolsVersion` | Parâmetro `String` opcional.<br /><br /> Especifica o `ToolsVersion` a ser usado ao compilar projetos passados para essa tarefa.<br /><br /> Habilita uma tarefa MSBuild para construir um projeto que visa uma versão diferente do .NET Framework do que o especificado no projeto. Os valores válidos são `2.0`, `3.0` e `3.5`. O valor padrão é `3.5`. |

## <a name="remarks"></a>Comentários

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

 Ao contrário de usar a [tarefa Exec](../msbuild/exec-task.md) para iniciar *o MSBuild.exe,* essa tarefa usa o mesmo processo mSBuild para construir os projetos filho. A lista de destinos já compilados que pode ser ignorada é compartilhada entre as compilações pai e filho. Essa tarefa também é mais rápida porque nenhum novo processo do MSBuild é criado.

 Essa tarefa pode processar não somente arquivos de projeto, mas também arquivos de solução.

 Qualquer configuração necessária pelo MSBuild para permitir que os projetos sejam construídos ao mesmo tempo, mesmo que a configuração envolva infra-estrutura remota (por exemplo, portas, protocolos, tempoouts, repetições e assim por diante), deve ser configurada usando um arquivo de configuração. Quando possível, itens de configuração deverão ser capazes de ser especificados como parâmetros de tarefa na tarefa `MSBuild`.

 A partir do MSBuild 3.5, os projetos de solução agora superam as Saídas de Destino de todos os subprojetos que ele constrói.

## <a name="pass-properties-to-projects"></a>Passar propriedades para projetos

 Nas versões do MSBuild antes do MSBuild 3.5, passar diferentes conjuntos de propriedades para diferentes projetos listados no item MSBuild foi um desafio. Se você usou o atributo Propriedades da [tarefa MSBuild,](../msbuild/msbuild-task.md)então sua configuração foi aplicada a todos os projetos que estão sendo construídos, a menos que você tenha substituído a [tarefa MSBuild](../msbuild/msbuild-task.md) e fornecido condicionalmente propriedades diferentes para cada projeto na lista de itens.

 O MSBuild 3.5, no entanto, fornece dois novos itens de metadados reservados, Propriedades e Propriedades Adicionais, que fornecem uma maneira flexível de passar diferentes propriedades para diferentes projetos que estão sendo construídos usando a [tarefa MSBuild](../msbuild/msbuild-task.md).

> [!NOTE]
> Esses novos itens de metadados são aplicáveis apenas aos itens aprovados no atributo Projetos da [tarefa MSBuild](../msbuild/msbuild-task.md).

## <a name="multi-processor-build-benefits"></a>Benefícios da compilação multiprocessador

 Um dos principais benefícios de usar esses novos metadados ocorre quando você compila seus projetos em paralelo em um sistema com vários processadores. Os metadados permitem consolidar todos os projetos em uma única chamada [de tarefa do MSBuild](../msbuild/msbuild-task.md) sem ter que executar nenhuma tarefa de loteamento ou MSBuild condicional. E quando você chama apenas uma única [tarefa de MSBuild,](../msbuild/msbuild-task.md)todos os projetos listados no atributo Projetos serão construídos em paralelo. (Somente, no entanto, se o atributo `BuildInParallel=true` estiver presente na tarefa [MSBuild](../msbuild/msbuild-task.md).) Para obter mais informações, consulte [Construir vários projetos em paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Metadados de propriedades

 Quando especificados, os metadados de propriedades substituem o parâmetro Propriedades da tarefa, enquanto os metadados de [AdditionalProperties](#additionalproperties-metadata) são acrescentados às definições do parâmetro.

 Um cenário comum é quando você está construindo vários arquivos de solução usando a [tarefa MSBuild,](../msbuild/msbuild-task.md)usando apenas diferentes configurações de compilação. Você pode querer compilar a solução a1 usando a configuração de depuração e compilar a solução a2 usando a configuração de versão. No MSBuild 2.0, este arquivo de projeto se pareceria com o seguinte:

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

 Usando os metadados Propriedades, no entanto, você pode simplificar isso para usar uma única [tarefa mSBuild,](../msbuild/msbuild-task.md)como mostrado pelo seguinte:

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

 Considere o seguinte cenário onde você está construindo dois arquivos de solução usando a [tarefa MSBuild,](../msbuild/msbuild-task.md)ambos usando a configuração De suma, mas um usando a arquitetura x86 e o outro usando a arquitetura ia64. No MSBuild 2.0, você precisaria criar várias instâncias da [tarefa MSBuild](../msbuild/msbuild-task.md): uma para construir o projeto usando a configuração De versão com a arquitetura x86, a outra usando a configuração De sumar com a arquitetura ia64. Seu arquivo de projeto seria semelhante ao seguinte:

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

 Usando os metadados AdditionalProperties, você pode simplificar isso para usar uma única [tarefa do MSBuild](../msbuild/msbuild-task.md) usando o seguinte:

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
