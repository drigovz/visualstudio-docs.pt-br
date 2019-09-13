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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba701d123e739bc2dfa24ff798aef5338c51f532
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913176"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Como: Estender o processo de build do Visual Studio
O processo de build do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é definido por uma série de arquivos *.targets* do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que são importados para o arquivo de projeto. Um desses arquivos importados, *Microsoft.Common.targets*, pode ser estendido para permitir a execução de tarefas personalizadas em vários pontos no processo de build. Este artigo explica os dois métodos que você pode usar para estender o processo de build do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:

- Substituir destinos predefinidos específicos definidos nos destinos comuns (*Microsoft. Common. targets* ou os arquivos que ele importa).

- Substituindo as propriedades "depends" definidas nos destinos comuns.

## <a name="override-predefined-targets"></a>Substituir destinos predefinidos
Os destinos comuns contêm um conjunto de destinos vazios predefinidos que é chamado antes e depois de alguns dos principais destinos no processo de compilação. Por exemplo, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] chama o destino `BeforeBuild` antes do destino `CoreBuild` principal e o destino `AfterBuild` após o destino `CoreBuild`. Por padrão, os destinos vazios nos destinos comuns não fazem nada, mas você pode substituir seu comportamento padrão definindo os destinos desejados em um arquivo de projeto que importe os destinos comuns. Substituindo destinos predefinidos, você pode usar tarefas do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para obter mais controle sobre o processo de build.

> [!NOTE]
> Projetos no estilo SDK têm uma importação implícita de destinos *após a última linha do arquivo de projeto*. Isso significa que não é possível substituir destinos padrão, a menos que você especifique suas importações [manualmente, conforme descrito em como: Use SDKs](how-to-use-project-sdk.md)de projeto do MSBuild.

#### <a name="to-override-a-predefined-target"></a>Para substituir um destino predefinido

1. Identifique um destino predefinido nos destinos comuns que você deseja substituir. Consulte a tabela abaixo para obter uma lista completa de destinos que você pode substituir com segurança.

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

A tabela a seguir mostra todos os destinos nos destinos comuns que você pode substituir com segurança.

|Nome de destino|Descrição|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|As tarefas inseridas em um desses destinos são executadas antes ou após a conclusão da compilação principal. A maioria das personalizações é realizada em um desses dois destinos.|
|`BeforeBuild`, `AfterBuild`|As tarefas inseridas em um desses destinos serão executadas antes ou depois de todo o resto no build. **Observação:**  Os destinos `BeforeBuild` e `AfterBuild` já estão definidos nos comentários ao final da maioria dos arquivos de projeto, permitindo que você adicione com facilidade eventos de pré e pós-build ao arquivo de projeto.|
|`BeforeRebuild`, `AfterRebuild`|As tarefas inseridas em um desses destinos são executadas antes ou após a invocação da funcionalidade de recompilação principal. A ordem de execução de destino em *Microsoft.Common.targets* é: `BeforeRebuild`, `Clean`, `Build` e, em seguida, `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|As tarefas inseridas em um desses destinos são executadas antes ou após a invocação da funcionalidade de limpeza principal.|
|`BeforePublish`, `AfterPublish`|As tarefas inseridas em um desses destinos são executadas antes ou após a invocação da funcionalidade de publicação principal.|
|`BeforeResolveReferences`, `AfterResolveReferences`|As tarefas inseridas em um desses destinos são executadas antes ou após a resolução das referências de assembly.|
|`BeforeResGen`, `AfterResGen`|As tarefas inseridas em um desses destinos são executadas antes ou após a geração de recursos.|

## <a name="override-dependson-properties"></a>Substituir propriedades DependsOn
Substituir destinos predefinidos é uma maneira fácil de estender o processo de build, mas, como [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] avalia a definição de destinos sequencialmente, não há nenhuma maneira de impedir que outro projeto que importa seu projeto substitua os destinos que você já substituiu. Dessa forma, por exemplo, o último destino `AfterBuild` no arquivo de projeto, depois que todos os outros projetos foram importados, será aquele usado durante o build.

Você pode se proteger contra substituições indesejadas de destinos substituindo as propriedades dependentes que `DependsOnTargets` são usadas em atributos em todos os destinos comuns. Por exemplo, o destino `Build` contém um valor de atributo `DependsOnTargets` de `"$(BuildDependsOn)"`. Considere:

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

1. Identifique uma propriedade dependente predefinida nos destinos comuns que você deseja substituir. Confira a tabela abaixo para obter uma lista das propriedades DependsOn geralmente substituídas.

2. Defina outra instância da propriedade ou propriedades no final do seu arquivo de projeto. Inclua a propriedade original, por exemplo `$(BuildDependsOn)`, na nova propriedade.

3. Defina seus destinos personalizados antes ou após a definição da propriedade.

4. Compile o arquivo de projeto.

### <a name="commonly-overridden-dependson-properties"></a>Propriedades DependsOn geralmente substituídas

|Nome da propriedade|Descrição|
|-------------------|-----------------|
|`BuildDependsOn`|A propriedade a ser substituída se você quiser inserir destinos personalizados antes ou após o processo inteiro de build.|
|`CleanDependsOn`|A propriedade a ser substituída você quiser limpar a saída do seu processo de build personalizado.|
|`CompileDependsOn`|A propriedade a ser substituída se você quiser inserir processos personalizados antes ou após a etapa de compilação.|

## <a name="see-also"></a>Consulte também
- [Integração com o Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
- [Arquivos .targets](../msbuild/msbuild-dot-targets-files.md)
