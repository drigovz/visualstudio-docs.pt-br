---
title: Tarefa Erro | Microsoft Docs
description: Use a tarefa de erro do MSBuild para interromper uma compilação e registrar um erro com base em uma instrução condicional avaliada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e4e1a91bc018bdf77671b13994ce57e4e10e694
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877194"
---
# <a name="error-task"></a>tarefa Error

Interrompe um build e registra um erro com base em uma instrução condicional avaliada.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros da tarefa `Error`.

| Parâmetro | Descrição |
|---------------| - |
| `Code` | Parâmetro `String` opcional.<br /><br /> O código de erro a associar ao erro. |
| `File` | Parâmetro `String` opcional.<br /><br /> O nome do arquivo que contém o erro. Se nenhum nome de arquivo for fornecido, o arquivo que contém a tarefa de erro será usado. |
| `HelpKeyword` | Parâmetro `String` opcional.<br /><br /> A palavra-chave Ajuda a ser associada ao erro. |
| `Text` | Parâmetro `String` opcional.<br /><br /> O texto de erro que o MSBuild registra se o `Condition` parâmetro é avaliado como `true` . |

## <a name="remarks"></a>Comentários

A `Error` tarefa permite que os projetos do MSBuild emitam texto de erro para agentes e interrompam a execução da compilação.

Se o parâmetro `Condition` avaliar `true`, o build será interrompido e um erro será registrado. Se um parâmetro `Condition` não existir, o erro será registrado e a execução de build será interrompida. Para obter mais informações sobre o log, confira [Obtendo logs de build](../msbuild/obtaining-build-logs-with-msbuild.md).

Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

O exemplo de código a seguir verifica se todas as propriedades necessárias estão definidas. Se elas não estiverem definidas, o projeto gerará um evento de erro e registrará o valor do parâmetro `Text` da tarefa `Error`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Error
            Text=" The 0 property must be set on the command line."
            Condition="'$(0)' == ''" />
        <Error
            Text="The FREEBUILD property must be set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Obter logs de build](../msbuild/obtaining-build-logs-with-msbuild.md)
