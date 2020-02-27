---
title: Tarefa ResourcesGenerator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b5aba45292aaa55a719eb19d6f0f6f115e8b477
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632505"
---
# <a name="resourcesgenerator-task"></a>Tarefa ResourcesGenerator

A tarefa <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> insere um ou mais recursos ( *. jpg*, *. ico*, *. bmp*, XAML em formato binário e outros tipos de extensão) em um arquivo *. Resources* .

## <a name="task-parameters"></a>Parâmetros de tarefa

|Parâmetro|DESCRIÇÃO|
|---------------|-----------------|
|`OutputPath`|Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> Especifica o caminho do diretório de saída. Se o caminho não for um caminho absoluto, ele será tratado como um caminho relativo ao diretório do projeto raiz.|
|`OutputResourcesFile`|Parâmetro de saída **ITaskItem[]** obrigatório.<br /><br /> Especifica o caminho e o nome dos arquivos *.resource* gerados. Se o caminho não for um caminho absoluto, o arquivo *.resources* será gerado em relação ao diretório raiz do projeto.|
|`ResourcesFiles`|Parâmetro obrigatório **ITaskItem[]** .<br /><br /> Especifica um ou mais recursos para ser inserido no arquivo *.resources* gerado.|

## <a name="example"></a>Exemplo

 O exemplo a seguir gera um arquivo *.resources* com um único recurso *.bmp*. O recurso *.bmp* é gerado para um diretório relativo ao diretório raiz do projeto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="ResourcesGeneratorTask">
    <ResourcesGenerator
      ResourceFiles="Resource1.bmp"
      OutputPath="myresources"
      OutputResourcesFile="myresources\my.resources" />
  </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [Referência do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Compilar um aplicativo WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)