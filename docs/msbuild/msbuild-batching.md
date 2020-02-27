---
title: Separação em lotes no MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78aeef8ea651aac1fe2a780207474399f4bbcf09
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633428"
---
# <a name="msbuild-batching"></a>Envio em lote do MSBuild

O MSBuild tem a capacidade de dividir listas de itens em diferentes categorias, ou em lotes, com base nos metadados do item, e executar um destino ou uma tarefa uma vez com cada lote.

## <a name="task-batching"></a>Envio de tarefas em lote

O lote de tarefas permite que você simplifique os arquivos de projeto ao fornecer uma maneira de dividir as listas de itens em lotes diferentes e passar cada um desses lotes para uma tarefa separadamente. Isso significa que um arquivo de projeto só precisa ter a tarefa e seus atributos declarados uma vez, mesmo que seja executado várias vezes.

Você especifica que deseja que o MSBuild execute o envio em lote com uma tarefa usando a notação%(\<mymetadataname >) em um dos atributos da tarefa. O exemplo a seguir divide a lista de itens `Example` em lotes com base no valor do item de metadados `Color` e passa cada um dos lotes para a tarefa `MyTask` separadamente.

> [!NOTE]
> Se você não referenciar a lista de itens em outro lugar nos atributos de tarefa ou se o nome dos metadados for ambíguo, use a notação %(\<ItemCollection.ItemMetaDataName>) para qualificar totalmente o valor do metadados de item a ser usado para o envio em lote.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Para obter exemplos mais específicos do envio em lote, confira [Metadados de item no envio de tarefas em lote](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Envio em lote de destinos

O MSBuild verifica se as entradas e saídas de um destino estão atualizadas antes de executar o destino. Se as entradas e saídas estiverem atualizadas, o destino será ignorado. Se uma tarefa dentro de um destino usar o envio em lote, o MSBuild precisará determinar se as entradas e saídas de cada lote de itens estão atualizadas. Caso contrário, o destino será executado sempre que for atingido.

O exemplo a seguir mostra um elemento `Target` que contém um atributo `Outputs` com a notação %(\<ItemMetaDataName>). O MSBuild dividirá a lista de itens de `Example` em lotes com base nos metadados do item de `Color` e analisará os carimbos de data/hora dos arquivos de saída para cada lote. Se as saídas de um lote não estiverem atualizadas, o destino é executado. Caso contrário, o destino será ignorado.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Para obter outro exemplo de envio de destinos em lote, confira [Metadados de item no envio de destinos em lote](../msbuild/item-metadata-in-target-batching.md).

## <a name="property-functions-using-metadata"></a>Funções de propriedade usando metadados

O envio em lote pode ser controlado por funções de propriedade que incluem metadados. Por exemplo,

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

usa <xref:System.IO.Path.Combine%2A> para combinar um caminho de pasta raiz com um caminho do item de compilação.

Funções de propriedade podem não aparecer em valores de metadados. Por exemplo,

`%(Compile.FullPath.Substring(0,3))`

não é permitido.

Para obter mais informações sobre funções de propriedade, confira [Funções de propriedade](../msbuild/property-functions.md).

## <a name="see-also"></a>Confira também

- [Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)
