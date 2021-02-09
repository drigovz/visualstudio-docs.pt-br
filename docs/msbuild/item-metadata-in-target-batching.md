---
title: Metadados de itens na separação de destinos em lotes | Microsoft Docs
description: Saiba como o MSBuild usa metadados de item no envio em lote de destino para executar a análise de dependência nas entradas e saídas de um destino de compilação.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d3389d24ded805c7b1f8bbb8d31daef0cbef1a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913912"
---
# <a name="item-metadata-in-target-batching"></a>Metadados de item no envio de destinos em lote

O MSBuild tem a capacidade de executar a análise de dependência nas entradas e saídas de um destino de compilação. Se for determinado que as entradas ou as saídas do destino estão atualizadas, o destino será ignorado e o build continuará. Elementos `Target` usam os atributos `Inputs` e `Outputs` para especificar os itens a fim de inspecionar durante a análise de dependência.

Se um destino contiver uma tarefa que usa itens em lote como entradas ou saídas, o `Target` elemento do destino deverá usar o envio em lote em seus `Inputs` `Outputs` atributos ou para permitir que o MSBuild ignore lotes de itens já atualizados.

## <a name="batch-targets"></a>Destinos em lotes

O exemplo a seguir contém uma lista de item nomeada `Res` que é dividida em dois lotes baseados nos metadados de item `Culture`. Cada um desses lotes é passada para a tarefa `AL`, que cria um assembly de saída para cada lote. Usando o envio em lote no `Outputs` atributo do `Target` elemento, o MSBuild pode determinar se cada um dos lotes individuais está atualizado antes de executar o destino. Sem o uso do envio em lote de destino, ambos os lotes de itens seriam executados pela tarefa toda vez que o destino fosse executado.

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
- [Separação em lotes](../msbuild/msbuild-batching.md)
- [Elemento de destino (MSBuild)](../msbuild/target-element-msbuild.md)
- [Metadados de item no envio de tarefas em lote](../msbuild/item-metadata-in-task-batching.md)
