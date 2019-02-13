---
title: Metadados de itens na separação de destinos em lotes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eca5fc85f4a1bcd26c2c4c73ec39fbe855f77add
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769364"
---
# <a name="item-metadata-in-target-batching"></a>Metadados de itens na separação de destinos em lotes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] tem a capacidade de executar a análise de dependência em entradas e saídas de um destino de build. Se for determinado que as entradas ou saídas do destino estão atualizadas, o destino será ignorado e o build continuará. Elementos `Target` usam os atributos `Inputs` e `Outputs` para especificar os itens a fim de inspecionar durante a análise de dependência.  
  
 Se um destino contiver uma tarefa que usa itens em lotes como entradas ou saídas, o elemento `Target` do destino deve usar o envio em lote nos aributos `Inputs` ou `Outputs` para habilitar [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] a ignorar lotes de itens que já estão atualizados.  
  
## <a name="batching-targets"></a>Envio em lote de destinos  
 O exemplo a seguir contém uma lista de item nomeada `Res` que é dividida em dois lotes baseados nos metadados de item `Culture`. Cada um desses lotes é passada para a tarefa `AL`, que cria um assembly de saída para cada lote. Ao usar o envio em lote no atributo `Outputs` do elemento `Target`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pode determinar se cada um dos lotes individuais está atualizado antes de executar o destino. Sem o uso do envio em lote de destino, ambos os lotes de itens seriam executados pela tarefa toda vez que o destino fosse executado.  
  
```  
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
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como compilar incrementalmente](../msbuild/how-to-build-incrementally.md)   
 [Envio em lote](../msbuild/msbuild-batching.md)   
 [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Metadados de itens na separação de tarefas em lotes](../msbuild/item-metadata-in-task-batching.md)
