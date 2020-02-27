---
title: Tarefa UidManager | Microsoft Docs
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
ms.openlocfilehash: 37692c541fb2a6e9b2ccf61083dd383e56a79766
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631517"
---
# <a name="uidmanager-task"></a>Tarefa UidManager

A tarefa <xref:Microsoft.Build.Tasks.Windows.UidManager> verifica, atualiza ou remove identificadores exclusivos (UIDs), a fim de localizar todos os elementos XAML incluídos nos arquivos XAML de origem.

## <a name="task-parameters"></a>Parâmetros de tarefa

| Parâmetro | DESCRIÇÃO |
|-------------------------| - |
| `IntermediateDirectory` | Parâmetro **String** opcional.<br /><br /> Especifica o diretório que é usado para fazer backup dos arquivos XAML de origem que são especificados pelo parâmetro **MarkupFiles** . |
| `MarkupFiles` | Parâmetro obrigatório **ITaskItem[]** .<br /><br /> Especifica os arquivos XAML de origem a serem incluídos para verificação, atualização ou remoção de UID. |
| `Task` | Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> Especifica a tarefa de gerenciamento de UID que você deseja executar. As opções válidas são **Verificar**, **Atualizar** ou **Remover**. |

## <a name="example"></a>Exemplo

 O exemplo a seguir usa a tarefa <xref:Microsoft.Build.Tasks.Windows.UidManager> para verificar se os arquivos XAML de origem especificados contêm elementos XAML que têm UIDs apropriados.

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

## <a name="see-also"></a>Confira também

- [Referência do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Compilar um aplicativo WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Como localizar um aplicativo](/dotnet/framework/wpf/advanced/how-to-localize-an-application)