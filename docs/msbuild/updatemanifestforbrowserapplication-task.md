---
title: Tarefa UpdateManifestForBrowserApplication | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 079eecd6751f168a7beba32eda6d15eda712bd7f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631322"
---
# <a name="updatemanifestforbrowserapplication-task"></a>Tarefa UpdateManifestForBrowserApplication

A tarefa de <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> é executada para adicionar o elemento **\<HostInBrowser/>** ao manifesto do aplicativo ( *\<ProjectName >. exe. manifest*) quando um projeto do XBAP (aplicativo de navegador XAML) é compilado.

## <a name="task-parameters"></a>Parâmetros de tarefa

|Parâmetro|DESCRIÇÃO|
|---------------|-----------------|
|`ApplicationManifest`|Parâmetro obrigatório **ITaskItem[]** .<br /><br /> Especifica o caminho e o nome do arquivo de manifesto do aplicativo ao qual você deseja adicionar o elemento `<hostInBrowser />`.|
|`HostInBrowser`|Parâmetro **Booliano** opcional.<br /><br /> Especifica se deseja ou não modificar o manifesto do aplicativo para incluir o elemento **\<hostInBrowser />** . Se for **true**, um novo elemento **\<hostInBrowser />** será incluído no elemento **\<entryPoint />** . A inclusão do elemento é cumulativa: se um elemento **\<hostInBrowser />** já existe, ele não é removido nem substituído. Em vez disso, um elemento **\<hostInBrowser />** adicional é criado. Se for **false**, o manifesto do aplicativo não será modificado.|

## <a name="remarks"></a>Comentários

 XBAPs são executados usando a implantação do ClickOnce, portanto, eles devem ser publicados com suporte à implantação e aos manifestos do aplicativo. O MSBuild usa a tarefa [GenerateApplicationManifest](generateapplicationmanifest-task.md) para gerar um manifesto do aplicativo.

 Em seguida, para configurar um aplicativo para ser hospedado de um navegador, um elemento adicional, **\<hostInBrowser />** , deve ser adicionado ao manifesto do aplicativo, conforme mostrado no exemplo a seguir:

```xml
<!--MyXBAPApplication.exe.manifest-->
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly ... >
    <asmv1:assemblyIdentity ... />
    <application />
    <entryPoint>
      ...
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />
    </entryPoint>
  ...
/>
```

 A tarefa de <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> é executada quando um projeto XBAP é compilado para adicionar o elemento `<hostInBrowser />`.

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra como garantir que o elemento `<hostInBrowser />` seja incluído em um arquivo de manifesto do aplicativo.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UpdateManifestForBrowserApplicationTask">
    <UpdateManifestForBrowserApplication
      ApplicationManifest="MyXBAPApplication.exe.manifest"
      HostInBrowser="true" />
  </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [Referência do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Compilar um aplicativo WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Visão geral dos aplicativos de navegador XAML do WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)