---
title: Tarefa VerifyFileHash | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3acdaabffc35122616cced4113abbc5a43beb9a1
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481971"
---
# <a name="verifyfilehash-task"></a>Tarefa VerifyFileHash

Verifica se um arquivo corresponde ao hash do arquivo esperado.

Essa tarefa foi adicionada no 15.8, mas requer uma [solução alternativa](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) a ser usada para as versões do MSBuild inferiores a 16.0.

## <a name="task-parameters"></a>Parâmetros de tarefa

 A tabela a seguir descreve os parâmetros da tarefa `VerifyFileHash`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`File`|Parâmetro `String` obrigatório.<br /><br />O arquivo com hash e validação.|
|`Hash`|Parâmetro `String` obrigatório.<br /><br />O hash esperado do arquivo.|
|`Algorithm`|Parâmetro `String` opcional.<br /><br />O algoritmo. Valores permitidos: `SHA256`, `SHA384`, `SHA512`. Padrão = `SHA256`.|
|`HashEncoding`|Parâmetro `String` opcional.<br /><br />A codificação usada para hashes gerados. Assume o padrão de `hex`. Valores permitidos = `hex`, `base64`.|

## <a name="example"></a>Exemplo

O exemplo a seguir usa a tarefa `VerifyFileHash` para verificar sua própria soma de verificação.

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

## <a name="see-also"></a>Consulte também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)