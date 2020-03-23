---
title: Metadados de itens na separação de destinos em lotes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a5d0c9dec280633d0a39573581c083e6ddd4d8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633662"
---
# <a name="item-metadata-in-target-batching"></a>Metadados de item no envio de destinos em lote

O MSBuild tem a capacidade de executar análises de dependência nas entradas e saídas de um alvo de compilação. Se for determinado que as entradas ou as saídas do destino estão atualizadas, o destino será ignorado e o build continuará. Elementos `Target` usam os atributos `Inputs` e `Outputs` para especificar os itens a fim de inspecionar durante a análise de dependência.

Se um destino contiver uma tarefa que use itens em `Target` lote como entradas ou saídas, o elemento do destino deve usar o loteamento em seus `Inputs` ou `Outputs` atributos para permitir que o MSBuild pule lotes de itens que já estão atualizados.

## <a name="batch-targets"></a>Destinos em lotes

O exemplo a seguir contém uma lista de item nomeada `Res` que é dividida em dois lotes baseados nos metadados de item `Culture`. Cada um desses lotes é passada para a tarefa `AL`, que cria um assembly de saída para cada lote. Usando o loteamento `Outputs` no `Target` atributo do elemento, o MSBuild pode determinar se cada um dos lotes individuais está atualizado antes de executar o destino. Sem o uso do envio em lote de destino, ambos os lotes de itens seriam executados pela tarefa toda vez que o destino fosse executado.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Res Include="Strings.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Strings.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.jp.resources">
            <Culture>jp</Culture>
        </Res>
    </ItemGroup>

    <Target Name="Build"
        Inputs="@(Res)"
        Outputs="%(Culture)\MyApp.resources.dll">

        <AL Resources="@(Res)"
            TargetType="library"
            OutputAssembly="%(Culture)\MyApp.resources.dll">

    </Target>

</Project>
```

## <a name="see-also"></a>Confira também

- [Como criar de forma incremental](../msbuild/how-to-build-incrementally.md)
- [Lotes](../msbuild/msbuild-batching.md)
- [Elemento-alvo (MSBuild)](../msbuild/target-element-msbuild.md)
- [Metadados de itens em loteamento de tarefas](../msbuild/item-metadata-in-task-batching.md)
