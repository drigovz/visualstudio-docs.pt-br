---
title: Tarefa GetAssemblyIdentity | Microsoft Docs
description: Use a tarefa do MSBuild GetAssemblyIdentity para recuperar as identidades do assembly dos arquivos especificados e gerar as informações de identidade.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GetAssemblyIdentity task
- GetAssemblyIdentity task [MSBuild]
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 91a155e340f9ab246935f7b8cd6da46f3f364010
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914712"
---
# <a name="getassemblyidentity-task"></a>Tarefa GetAssemblyIdentity

Recupera as identidades do assembly dos arquivos especificados e gera como saída as informações de identidade.

## <a name="task-parameters"></a>Parâmetros de tarefa

A tabela a seguir descreve os parâmetros da tarefa `GetAssemblyIdentity`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`Assemblies`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém as identidades de assembly recuperadas.|
|`AssemblyFiles`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os arquivos dos quais recuperar identidades.|

## <a name="remarks"></a>Comentários

Os itens gerados como saída pelo parâmetro `Assemblies` contêm entradas de metadados do item chamadas `Version`, `PublicKeyToken` e `Culture`.

Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

O exemplo a seguir recupera a identidade dos arquivos especificados no item `MyAssemblies` e, em seguida, os gera como saída no item `MyAssemblyIdentities`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyAssemblies Include="File1.dll;File2.dll" />
    </ItemGroup>
    <Target Name="RetrieveIdentities">
        <GetAssemblyIdentity AssemblyFiles="@(MyAssemblies)">
            <Output TaskParameter="Assemblies" ItemName="MyAssemblyIdentities" />
        </GetAssemblyIdentity>
    </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
