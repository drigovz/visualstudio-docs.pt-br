---
title: Separação em lotes no MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d96330c01ab340d4db67694f358717a2dae0bce3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838419"
---
# <a name="msbuild-batching"></a>Separação em lotes no MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] tem a capacidade de dividir as listas de itens em categorias diferentes ou lotes com base nos metadados do item, além de executar um destino ou uma tarefa uma vez com cada lote.  
  
## <a name="task-batching"></a>Lote de tarefas  
 O lote de tarefas permite que você simplifique os arquivos de projeto ao fornecer uma maneira de dividir as listas de itens em lotes diferentes e passar cada um desses lotes para uma tarefa separadamente. Isso significa que um arquivo de projeto só precisa ter a tarefa e seus atributos declarados uma vez, mesmo que seja executado várias vezes.  
  
 Você especifica que deseja [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] executar o envio em lote com uma tarefa usando a notação%(de*mymetadataname*) em um dos atributos da tarefa. O exemplo a seguir divide a lista de itens `Example` em lotes com base no valor do item de metadados `Color` e passa cada um dos lotes para a tarefa `MyTask` separadamente.  
  
> [!NOTE]
> Se você não fizer referência à lista de itens em outro lugar nos atributos da tarefa, ou se o nome dos metadados puder ser ambíguo, você poderá usar a notação%(*ItemCollection. Item de metadadosname*para qualificar totalmente o valor de metadados do item a ser usado para envio em lote.  
  
```  
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
  
 Para obter exemplos de envio em lote mais específicos, consulte [metadados do item em lote de tarefas](../msbuild/item-metadata-in-task-batching.md).  
  
## <a name="target-batching"></a>Lote de destino  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] verifica se as entradas e saídas de um destino estão atualizadas antes de executar o destino. Se as entradas e saídas estiverem atualizadas, o destino será ignorado. Se uma tarefa dentro de um destino usar processamento em lote, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] precisa determinar se as entradas e saídas para cada lote de itens estão atualizadas. Caso contrário, o destino será executado sempre que for atingido.  
  
 O exemplo a seguir mostra um `Target` elemento que contém um `Outputs` atributo com a notação%(de itens de*metadados*. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vai dividir a lista de itens `Example` em lotes com base nos metadados do item `Color` e analisar os carimbos de data/hora dos arquivos de saída para cada lote. Se as saídas de um lote não estiverem atualizadas, o destino é executado. Caso contrário, o destino será ignorado.  
  
```  
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
  
 Para obter outro exemplo de envio em lote de destino, consulte [metadados de item no envio em lote de destino](../msbuild/item-metadata-in-target-batching.md).  
  
## <a name="property-functions-using-metadata"></a>Funções de propriedade usando metadados  
 O envio em lote pode ser controlado por funções de propriedade que incluem metadados. Por exemplo,  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 usa <xref:System.IO.Path.Combine%2A> para combinar um caminho de pasta raiz com um caminho do item de compilação.  
  
 Funções de propriedade podem não aparecer em valores de metadados.  Por exemplo,  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 não é permitido.  
  
 Para obter mais informações sobre funções de propriedade, consulte [funções de propriedade](../msbuild/property-functions.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)
