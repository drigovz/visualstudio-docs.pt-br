---
title: Tarefa GetFileHash | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFileHash task [MSBuild]
- MSBuild, GetFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab5da58b125f86627d54547bd9f6f7cddc16c4de
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977497"
---
# <a name="getfilehash-task"></a>Tarefa GetFileHash

Calcula as somas de verificação do conteúdo de um arquivo ou conjunto de arquivos.

Essa tarefa foi adicionada no 15.8, mas requer uma [solução alternativa](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) a ser usada para as versões do MSBuild inferiores a 16.0.

## <a name="task-parameters"></a>Parâmetros de tarefa

 A tabela a seguir descreve os parâmetros da tarefa `GetFileHash`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`Files`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br />Os arquivos destinados a sofrer hashing.|
|`Items`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />A entrada `Files` com metadados adicionais definidos como o hash do arquivo.|
|`Hash`|Parâmetro de saída `String`.<br /><br />O hash do arquivo. Essa saída é definida somente se exatamente um item foi passado.|
|`Algorithm`|Parâmetro `String` opcional.<br /><br />O algoritmo. Valores permitidos: `SHA256`, `SHA384`, `SHA512`. Padrão = `SHA256`.|
|`MetadataName`|Parâmetro `String` opcional.<br /><br />O nome de metadados em que o hash é armazenado em cada item. Assume o padrão de `FileHash`.|
|`HashEncoding`|Parâmetro `String` opcional.<br /><br />A codificação usada para hashes gerados. Assume o padrão de `hex`. Valores permitidos = `hex`, `base64`.|

## <a name="example"></a>Exemplo

O exemplo a seguir usa a tarefa `GetFileHash` para determinar e imprimir a soma de verificação dos `FilesToHash` itens.

```xml
<Project>
  <ItemGroup>
    <FilesToHash Include="$(MSBuildThisFileDirectory)\*" />
  </ItemGroup>
  <Target Name="GetHash">
    <GetFileHash Files="@(FilesToHash)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />
  </Target>
</Project>
```

## <a name="see-also"></a>Consulte também

- [Tarefas](../msbuild/msbuild-tasks.md)

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)