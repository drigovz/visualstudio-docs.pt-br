---
title: Estender o processo de build
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6a465a752282f4a0dc00f3fb294ade4169bb19b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093944"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Como estender o processo de build do Visual Studio

O processo de compilação do Visual Studio é definido por uma série de arquivos MSBuild *.targets* que são importados para o arquivo do projeto. Um desses arquivos *importados, Microsoft.Common.targets,* pode ser estendido para permitir que você execute tarefas personalizadas em vários pontos do processo de compilação. Este artigo explica dois métodos que você pode usar para estender o processo de compilação do Visual Studio:

- Sobrepondo metas predefinidas específicas definidas nos alvos comuns (*Microsoft.Common.targets* ou os arquivos que importa).

- Substituindo as propriedades "DependsOn" definidas nos alvos comuns.

## <a name="override-predefined-targets"></a>Substituir destinos predefinidos

Os alvos comuns contêm um conjunto de alvos vazios predefinidos que é chamado antes e depois de alguns dos principais alvos no processo de construção. Por exemplo, o MSBuild `BeforeBuild` chama `CoreBuild` o `AfterBuild` alvo antes `CoreBuild` do alvo principal e do alvo após o alvo. Por padrão, os alvos vazios nos alvos comuns não fazem nada, mas você pode substituir seu comportamento padrão definindo os alvos que deseja em um arquivo de projeto que importa os alvos comuns. Ao sobrepor os alvos predefinidos, você pode usar tarefas do MSBuild para lhe dar mais controle sobre o processo de compilação.
Os alvos comuns contêm um conjunto de alvos vazios predefinidos que é chamado antes e depois de alguns dos principais alvos no processo de construção. Por exemplo, o MSBuild `BeforeBuild` chama `CoreBuild` o `AfterBuild` alvo antes `CoreBuild` do alvo principal e do alvo após o alvo. Por padrão, os alvos vazios nos alvos comuns não fazem nada, mas você pode substituir seu comportamento padrão definindo os alvos que deseja em um arquivo de projeto que importa os alvos comuns. Ao sobrepor os alvos predefinidos, você pode usar tarefas do MSBuild para lhe dar mais controle sobre o processo de compilação.

> [!NOTE]
> Os projetos no estilo SDK têm uma importação implícita de alvos *após a última linha do arquivo do projeto*. Isso significa que você não pode substituir alvos padrão a menos que você especifique suas importações manualmente conforme descrito em [Como: Usar SDKs do projeto MSBuild](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Para substituir um destino predefinido

1. Identifique um alvo predefinido nos alvos comuns que você deseja substituir. Consulte a tabela abaixo para obter uma lista completa de destinos que você pode substituir com segurança.

2. Defina o destino ou destinos no final do arquivo de projeto, imediatamente antes da marca `</Project>`. Por exemplo: 

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. Compile o arquivo de projeto.

A tabela a seguir mostra todos os alvos nos alvos comuns que você pode substituir com segurança.

|Nome de destino|Descrição|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|As tarefas inseridas em um desses destinos são executadas antes ou após a conclusão da compilação principal. A maioria das personalizações é realizada em um desses dois destinos.|
|`BeforeBuild`, `AfterBuild`|As tarefas inseridas em um desses destinos serão executadas antes ou depois de todo o resto no build. **Observação:** os destinos `BeforeBuild` e `AfterBuild` já estão definidos nos comentários ao final da maioria dos arquivos de projeto, permitindo que você adicione com facilidade eventos de pré e pós-build ao arquivo de projeto.|
|`BeforeRebuild`, `AfterRebuild`|As tarefas inseridas em um desses destinos são executadas antes ou após a invocação da funcionalidade de recompilação principal. A ordem de execução de alvos no `BeforeRebuild` `Clean` *Microsoft.Common.targets* é: , , `Build`e depois `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|As tarefas inseridas em um desses destinos são executadas antes ou após a invocação da funcionalidade de limpeza principal.|
|`BeforePublish`, `AfterPublish`|As tarefas inseridas em um desses destinos são executadas antes ou após a invocação da funcionalidade de publicação principal.|
|`BeforeResolveReferences`, `AfterResolveReferences`|As tarefas inseridas em um desses destinos são executadas antes ou após a resolução das referências de assembly.|
|`BeforeResGen`, `AfterResGen`|As tarefas inseridas em um desses destinos são executadas antes ou após a geração de recursos.|

## <a name="example-aftertargets-and-beforetargets"></a>Exemplo: AfterTargets e BeforeTargets

O exemplo a seguir `AfterTargets` mostra como usar o atributo para adicionar um alvo personalizado que faz algo com os arquivos de saída. Neste caso, ele copia os arquivos de saída para uma nova pasta *CustomOutput*.  O exemplo também mostra como limpar os arquivos criados `CustomClean` pela operação `BeforeTargets` de compilação personalizada com um alvo `CoreClean` usando um atributo e especificando que a operação de limpeza personalizada é executada antes do alvo.

```xml
<Project Sdk="Microsoft.NET.Sdk">

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
   <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
</PropertyGroup>

<Target Name="CustomAfterBuild" AfterTargets="Build">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean" BeforeTargets="CoreClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

> [!WARNING]
> Certifique-se de usar nomes diferentes dos alvos predefinidos listados na tabela na seção `CustomAfterBuild`anterior `AfterBuild`(por exemplo, nomeamos o alvo de compilação personalizada aqui , não ), uma vez que esses alvos predefinidos são substituídos pela importação de SDK que também os define. Você não vê a importação do arquivo de destino que substitui esses alvos, mas é implicitamente `Sdk` adicionado ao final do arquivo do projeto quando você usa o método de atributo de referenciar um SDK.

## <a name="override-dependson-properties"></a>Substituir propriedades DependsOn

A substituição de metas predefinidas é uma maneira fácil de estender o processo de construção, mas, como o MSBuild avalia a definição de metas sequencialmente, não há como impedir que outro projeto que importa seu projeto sobrepor as metas que você já tem Substituído. Dessa forma, por exemplo, o último destino `AfterBuild` no arquivo de projeto, depois que todos os outros projetos foram importados, será aquele usado durante o build.

Você pode se proteger contra substituições não intencionais de alvos substituindo as propriedades DependsOn que são usadas em `DependsOnTargets` atributos em todos os alvos comuns. Por exemplo, o destino `Build` contém um valor de atributo `DependsOnTargets` de `"$(BuildDependsOn)"`. Considerar:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Este trecho de XML indica que, antes de poder executar o destino `Build`, todos os destinos especificados na propriedade `BuildDependsOn` devem ser executados primeiro. A propriedade `BuildDependsOn` está definida como:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Você pode substituir esse valor da propriedade declarando outra propriedade denominada `BuildDependsOn` no final do seu arquivo de projeto. Incluindo a propriedade `BuildDependsOn` anterior na nova propriedade, você pode adicionar novos destinos no início e fim da lista de destinos. Por exemplo: 

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

Projetos que importam seus arquivos de projeto podem substituir essas propriedades sem substituir as personalizações que você fez.

#### <a name="to-override-a-dependson-property"></a>Para substituir uma propriedade DependsOn

1. Identifique uma propriedade dependson predefinida nos alvos comuns que você deseja substituir. Confira a tabela abaixo para obter uma lista das propriedades DependsOn geralmente substituídas.

2. Defina outra instância da propriedade ou propriedades no final do seu arquivo de projeto. Inclua a propriedade original, por exemplo `$(BuildDependsOn)`, na nova propriedade.

3. Defina seus destinos personalizados antes ou após a definição da propriedade.

4. Compile o arquivo de projeto.

### <a name="commonly-overridden-dependson-properties"></a>Propriedades DependsOn geralmente substituídas

|Nome da propriedade|Descrição|
|-------------------|-----------------|
|`BuildDependsOn`|A propriedade a ser substituída se você quiser inserir destinos personalizados antes ou após o processo inteiro de build.|
|`CleanDependsOn`|A propriedade a ser substituída você quiser limpar a saída do seu processo de build personalizado.|
|`CompileDependsOn`|A propriedade a ser substituída se você quiser inserir processos personalizados antes ou após a etapa de compilação.|

## <a name="example-builddependson-and-cleandependson"></a>Exemplo: BuildDependsOn e CleanDependsOn

O exemplo a seguir `BeforeTargets` `AfterTargets` é semelhante ao exemplo, mas mostra como alcançar funcionalidadesemelhante. Ele amplia a `BuildDependsOn` compilação usando `CustomAfterBuild` para adicionar sua própria tarefa que copia `CustomClean` os arquivos `CleanDependsOn`de saída após a compilação e também adiciona a tarefa correspondente usando .  

Neste exemplo, este é um projeto no estilo SDK. Como mencionado na nota sobre projetos no estilo SDK no início deste `Sdk` artigo, você deve usar o método de importação manual em vez do atributo que o Visual Studio usa quando gera arquivos de projeto.

```xml
<Project>
<Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>

<Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <BuildDependsOn>
      $(BuildDependsOn);CustomAfterBuild
    </BuildDependsOn>

    <CleanDependsOn>
      $(CleanDependsOn);CustomClean
    </CleanDependsOn>

    <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

<Target Name="CustomAfterBuild">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

A ordem dos elementos é importante. Os `BuildDependsOn` `CleanDependsOn` elementos devem aparecer após a importação do arquivo de alvos SDK padrão.

## <a name="see-also"></a>Confira também

- [Integração visual studio](../msbuild/visual-studio-integration-msbuild.md)
- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
- [.targets arquivos](../msbuild/msbuild-dot-targets-files.md)
