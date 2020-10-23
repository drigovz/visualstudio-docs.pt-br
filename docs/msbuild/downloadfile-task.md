---
title: Tarefa DownloadFile | Microsoft Docs
description: Saiba mais sobre os parâmetros da tarefa de DownloadFile do MSBuild, que baixa os arquivos especificados usando HTTP.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fda3edcd1c8bf173e1b70d8bf2d76d58f6e10d8d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436652"
---
# <a name="downloadfile-task"></a>Tarefa DownloadFile

Baixa os arquivos especificados usando o protocolo HTTP.

>[!NOTE]
>A tarefa DownloadFile está disponível somente no MSBuild 15.8 e superior.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros da tarefa `DownloadFile`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`DestinationFileName`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> O nome a ser usado para o arquivo baixado.  Por padrão, o nome de arquivo é derivado da `SourceUrl` ou do servidor remoto.|
|`DestinationFolder`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica a pasta de destino na qual baixar o arquivo.  Se a pasta será criada, caso ela não exista.|
|`DownloadedFile`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o arquivo baixado.|
|`Retries`|Parâmetro `Int32` opcional.<br /><br /> Especifica o número de tentativas de download, se todas as tentativas anteriores falharam. Usa zero como padrão.|
|`RetryDelayMilliseconds`|Parâmetro `Int32` opcional.<br /><br /> Especifica o atraso em milissegundos entre as repetições necessárias. Usa 5.000 como padrão.|
|`SkipUnchangedFiles`|Parâmetro `Boolean` opcional.<br /><br /> Se ele for `true`, ignorará o download de arquivos inalterados. Assume o padrão de `true`. A tarefa `DownloadFile` considera os arquivos como inalterados se eles têm o mesmo tamanho e a mesma hora da última modificação, de acordo com o servidor remoto. <br /><br />**Observação:** nem todos os servidores HTTP indicam que a data da última modificação dos arquivos fará com que o arquivo seja baixado novamente.|
|`SourceUrl`|Parâmetro `String` obrigatório.<br /><br /> Especifica a URL a ser baixada.|

## <a name="remarks"></a>Comentários

Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

O exemplo a seguir baixa um arquivo e inclui-o nos itens `Content` antes de compilar o projeto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
