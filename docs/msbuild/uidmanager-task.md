---
title: Tarefa UidManager | Microsoft Docs
description: Saiba como a tarefa MSBuild UidManager verifica, atualiza ou remove identificadores exclusivos (UIDs) para localizar todos os elementos XAML nos arquivos XAML de origem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 852b910de742676e1fe7dd0c85129640eb37a9ae
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046936"
---
# <a name="uidmanager-task"></a>Tarefa UidManager

A <xref:Microsoft.Build.Tasks.Windows.UidManager> tarefa verifica, atualiza ou remove os UIDs (identificadores exclusivos), a fim de localizar todos os elementos XAML incluídos nos arquivos XAML de origem.

## <a name="task-parameters"></a>Parâmetros de tarefa

| Parâmetro | Descrição |
|-------------------------| - |
| `IntermediateDirectory` | Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o diretório que é usado para fazer backup dos arquivos XAML de origem que são especificados pelo parâmetro **MarkupFiles** . |
| `MarkupFiles` | Parâmetro **ITaskItem []** necessário.<br /><br /> Especifica os arquivos XAML de origem a serem incluídos para verificação, atualização ou remoção de UID. |
| `Task` | Parâmetro obrigatório **String** .<br /><br /> Especifica a tarefa de gerenciamento de UID que você deseja executar. As opções válidas são **Verificar** , **Atualizar** ou **Remover** . |

## <a name="example"></a>Exemplo

 O exemplo a seguir usa a <xref:Microsoft.Build.Tasks.Windows.UidManager> tarefa para verificar se os arquivos XAML de origem especificados contêm elementos XAML que têm UIDs apropriados.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UidManagerTask">
    <UidManager
      Task="Check"
      MarkupFiles="Page1.xaml;Page2.xaml"
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />
  </Target>
</Project>
```

## <a name="see-also"></a>Veja também

- [Referência do MSBuild do WPF](../msbuild/wpf-msbuild-reference.md)
- [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Compilar um aplicativo WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Como localizar um aplicativo](/dotnet/framework/wpf/advanced/how-to-localize-an-application)