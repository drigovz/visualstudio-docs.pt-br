---
title: Copiar tarefa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
- MSBuild.Copy.ExceededRetries
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Copy task
- Copy task [MSBuild]
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28fd0033f5ef6f83ca29432f95d6b635fcd36116
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634364"
---
# <a name="copy-task"></a>tarefa Copy

Copia os arquivos para um novo local no sistema de arquivos.

## <a name="parameters"></a>parâmetros

A tabela a seguir descreve os parâmetros da tarefa `Copy`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`CopiedFiles`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém os itens que foram copiados com sucesso, *incluindo* aqueles que não foram realmente copiados, mas foram ignorados porque já estavam atualizados e `SkipUnchangedFiles` foram `true`.|
|`DestinationFiles`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica a lista de arquivos para a qual os arquivos de origem serão copiados. Essa lista deve ser um mapeamento um-para-um com a lista especificada no parâmetro `SourceFiles`. Ou seja, o primeiro arquivo especificado em `SourceFiles` será copiado para o primeiro local especificado em `DestinationFiles` e assim por diante.|
|`DestinationFolder`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o diretório para o qual você deseja copiar os arquivos. Isso deve ser um diretório, não um arquivo. Se o diretório não existir, ele será criado automaticamente.|
|`OverwriteReadOnlyFiles`|Parâmetro `Boolean` opcional.<br /><br /> Substitua arquivos mesmo se eles estiverem marcados como arquivos somente leitura|
|`Retries`|Parâmetro `Int32` opcional.<br /><br /> Especifica o número de tentativas de cópia, se todas as tentativas anteriores falharam. Usa zero como padrão.<br /><br /> **Observação:** o uso de repetições pode mascarar um problema de sincronização no processo de build.|
|`RetryDelayMilliseconds`|Parâmetro `Int32` opcional.<br /><br /> Especifica o atraso entre as tentativas necessárias. Usa como padrão o argumento RetryDelayMillisecondsDefault, que é passado para o construtor CopyTask.|
|`SkipUnchangedFiles`|Parâmetro `Boolean` opcional.<br /><br /> Se for `true`, ignorará a cópia dos arquivos inalterados entre a origem e o destino. A tarefa `Copy` considera os arquivos como inalterados se eles têm o mesmo tamanho e a mesma hora da última modificação. <br /><br /> **Observação:** se você definir esse parâmetro como `true`, não deverá usar a análise de dependência no destino recipiente, pois isso apenas executará a tarefa se as horas de última modificação dos arquivos de origem forem mais recentes do que as horas de última modificação dos arquivos de destino.|
|`SourceFiles`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os arquivos a serem copiados.|
|`UseHardlinksIfPossible`|Parâmetro `Boolean` opcional.<br /><br /> Se for `true`, criará Links Físicos para os arquivos copiados em vez de copiar os arquivos.|

## <a name="warnings"></a>Warnings

Os avisos são registrados, incluindo:

- `Copy.DestinationIsDirectory`

- `Copy.SourceIsDirectory`

- `Copy.SourceFileNotFound`

- `Copy.CreatesDirectory`

- `Copy.HardLinkComment`

- `Copy.RetryingAsFileCopy`

- `Copy.FileComment`

- `Copy.RemovingReadOnlyAttribute`

## <a name="remarks"></a>Comentários

O parâmetro `DestinationFolder` ou `DestinationFiles` deve ser especificado, mas não ambos. Se os dois forem especificados, a tarefa falhará e um erro será registrado.

Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

O exemplo a seguir copia `MySourceFiles` os itens da coleção de itens na pasta *c:\MyProject\Destination*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="a.cs;b.cs;c.cs"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFolder="c:\MyProject\Destination"
        />
    </Target>

</Project>
```

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra como fazer uma cópia recursiva. Este projeto copia todos os arquivos recursivamente de *c:\MySourceTree* em *c:\MyDestinationTree*, mantendo a estrutura do diretório.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFiles="@(MySourceFiles->'c:\MyDestinationTree\%(RecursiveDir)%(Filename)%(Extension)')"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
