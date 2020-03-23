---
title: Tarefa XmlPeek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5a76bf033fa3eb85f0626478b965285f32e5fb6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094667"
---
# <a name="xmlpeek-task"></a>Tarefa XmlPeek

Retorna os valores conforme especificado por uma consulta de XPath em um arquivo XML.

## <a name="parameters"></a>parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `XmlPeek`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`Namespaces`|Parâmetro `String` opcional.<br /><br /> Especifica os namespaces para prefixos de consulta do XPath.|
|`Query`|Parâmetro `String` opcional.<br /><br /> Especifica a consulta do XPath.|
|`Result`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém os resultados que são retornados por essa tarefa.|
|`XmlContent`|Parâmetro `String` opcional.<br /><br /> Especifica a entrada XML como uma cadeia de caracteres.|
|`XmlInputPath`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica a entrada XML como um caminho de arquivo.|

## <a name="remarks"></a>Comentários

 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).



## <a name="example"></a>Exemplo

Aqui está uma amostra `settings.config` de arquivo XML para ler:

```xml
<appSettings>
  <add key="ProjectFolder" value="S1" />
</appSettings>
```

Neste exemplo, se você `value`quiser ler, use código como o seguinte:

```xml
<Target Name="BeforeBuild">
    <XmlPeek XmlInputPath="settings.config" Query="appSettings/add[@key='ProjectFolder']/@value">
        <Output TaskParameter="Result" ItemName="value" />
    </XmlPeek>
    <Message Text="Using project folder @(value)." Importance="high" />
    <PropertyGroup>
        <ProjectFolder>@(value)</ProjectFolder>
    </PropertyGroup>
    <ItemGroup>
        <Compile Include="Projects\$(ProjectFolder)\Controls\Control1.ascx.cs">
            <SubType>ASPXCodeBehind</SubType>
        </Compile>
    </ItemGroup>
</Target>
```

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
