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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53819a642edcdf0419dd445ac32dbde8d14ffb22
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77579526"
---
# <a name="verifyfilehash-task"></a>Tarefa VerifyFileHash

Verifica se um arquivo corresponde ao hash do arquivo esperado. Se o hash não corresponder, a tarefa falha.

Essa tarefa foi adicionada no 15.8, mas requer uma [solução alternativa](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) a ser usada para as versões do MSBuild inferiores a 16.0.

## <a name="task-parameters"></a>Parâmetros de tarefa

 A tabela a seguir descreve os parâmetros da tarefa `VerifyFileHash`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`File`|Parâmetro `String` obrigatório.<br /><br />O arquivo a ser hashed e validado.|
|`Hash`|Parâmetro `String` obrigatório.<br /><br />O hash esperado do arquivo.|
|`Algorithm`|Parâmetro `String` opcional.<br /><br />O algoritmo. Valores permitidos: `SHA256`, `SHA384`, `SHA512`. Padrão = `SHA256`.|
|`HashEncoding`|Parâmetro `String` opcional.<br /><br />A codificação usada para hashes gerados. Usa `hex` como padrão. Valores permitidos = `hex`, `base64`.|

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

No MSBuild 16.5 e posterior, se você não quiser que a compilação falhe quando o hash não corresponder, como se você estiver usando a comparação de hash como condição para o fluxo de controle, você pode rebaixar o aviso para uma mensagem usando o seguinte código:

```xml
  <PropertyGroup>
    <MSBuildWarningsAsMessages>$(MSBuildWarningsAsMessages);MSB3952</MSBuildWarningsAsMessages>
  </PropertyGroup>

  <Target Name="DemoVerifyCheck">
    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="1"
                    ContinueOnError="WarnAndContinue" />

    <PropertyGroup>
      <HashMatched>$(MSBuildLastTaskResult)</HashMatched>
    </PropertyGroup>

    <Message Condition=" '$(HashMatched)' != 'true'"
             Text="The hash didn't match" />

    <Message Condition=" '$(HashMatched)' == 'true'"
             Text="The hash did match" />
  </Target>
```

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
