---
title: Tarefa MergeLocalizationDirectives | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c7699afeb09604a437aad091f9aaf9ce624d33e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633493"
---
# <a name="mergelocalizationdirectives-task"></a>Tarefa MergeLocalizationDirectives

A <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> tarefa mescla os atributos de localização e os comentários de um ou mais arquivos de formato binário XAML em um único arquivo para o assembly inteiro.

## <a name="task-parameters"></a>Parâmetros de tarefa

| Parâmetro | Descrição |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Parâmetro **ITaskItem []** necessário.<br /><br /> Especifica a lista de arquivos de diretivas de localização para arquivos individuais no formato binário XAML. |
| `OutputFile` | Parâmetro de saída da **cadeia de caracteres** necessário.<br /><br /> Especifica o caminho de saída do assembly de diretivas de localização compilado. |

## <a name="remarks"></a>Comentários

Você pode adicionar atributos de localização e comentários ao conteúdo XAML. Com o suporte à localização do Windows Presentation Foundation (WPF), você pode distribuir atributos de localização e comentários e colocá-los em um arquivo *. loc* separado do assembly gerado. Você pode fazer isso usando o atributo **LocalizationPropertyStorage**. Para obter mais informações sobre atributos de localização e comentários, bem como sobre **LocalizationPropertyStorage**, confira [Atributos de localização e comentários](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Exemplo

O exemplo a seguir mescla os comentários de localização de vários arquivos de formato binário XAML em um único arquivo *. loc* .

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MergeLocalizationDirectivesTask">
    <MergeLocalizationDirectives
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"
      OutputFile="obj\debug\WPFMSBuildSample.loc" />
  </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [Referência do MSBuild do WPF](../msbuild/wpf-msbuild-reference.md)
- [Referência de tarefas do WPF MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Referência de tarefa do MSBuild](../msbuild/msbuild-task-reference.md)
- [Compilar um aplicativo WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
