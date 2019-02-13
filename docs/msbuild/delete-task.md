---
title: Tarefa Delete | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0893ded1cd2eb40cc6004f90e29e0765ff48ca6a
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853791"
---
# <a name="delete-task"></a>tarefa Delete
Exclui os arquivos especificados.

## <a name="parameters"></a>Parâmetros
A tabela a seguir descreve os parâmetros da tarefa `Delete`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`DeletedFiles`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica os arquivos que foram excluídos com êxito.|
|`Files`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os arquivos a serem excluídos.|
|`TreatErrorsAsWarnings`|Parâmetro opcional `Boolean`<br /><br /> Se `true`, os erros são registrados como avisos. O valor padrão é `false`.|

## <a name="remarks"></a>Comentários
Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo
O exemplo a seguir exclui o arquivo *MyApp.pdb*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <AppName>MyApp</AppName>
    </PropertyGroup>

    <Target Name="DeleteFiles">
        <Delete Files="$(AppName).pdb" />
    </Target>
</Project>
```

## <a name="see-also"></a>Consulte também
[Tarefas](../msbuild/msbuild-tasks.md)  
[Referência de tarefas](../msbuild/msbuild-task-reference.md)
