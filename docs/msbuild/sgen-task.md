---
title: Tarefa SGen | Microsoft Docs
description: Saiba como o MSBuild usa a tarefa SGen para criar um assembly de serialização XML para tipos, encapsulando a ferramenta gerador de serializador XML Sgen.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de2437306dba50a1f93b0b94d86af6351b17c0b6
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048343"
---
# <a name="sgen-task"></a>tarefa SGen

Cria um assembly de serialização de XML para tipos no assembly especificado. Essa tarefa encapsula a ferramenta gerador de serializador XML ( *Sgen.exe* ). Para saber mais, confira [Ferramenta geradora de serializador de XML (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `SGen`.

| Parâmetro | Descrição |
|-----------------------------| - |
| `BuildAssemblyName` | Parâmetro `String` obrigatório.<br /><br /> Defina o assembly para o qual gerar código de serialização. |
| `BuildAssemblyPath` | Parâmetro `String` obrigatório.<br /><br /> O caminho para o assembly para o qual gerar código de serialização. |
| `DelaySign` | Parâmetro `Boolean` opcional.<br /><br /> Se for `true`, especificará que você apenas deseja colocar a chave pública no assembly. Se for `false`, especificará que você deseja um assembly totalmente com sinal.<br /><br /> Esse parâmetro não terá nenhum efeito a menos que seja usado com o parâmetro `KeyFile` ou `KeyContainer`. |
| `KeyContainer` | Parâmetro `String` opcional.<br /><br /> Especifica um contêiner que mantém um par de chaves. Isso assinará o assembly inserindo uma chave pública no manifesto do assembly. A tarefa assinará então o assembly final com a chave privada. |
| `KeyFile` | Parâmetro `String` opcional.<br /><br /> Especifica um par de chaves ou uma chave pública a usar para assinar um assembly. O compilador insere a chave pública no manifesto do assembly e, em seguida, assina o assembly final com a chave privada. |
| `Platform` | Parâmetro `String` opcional.<br /><br /> Obtém ou define a plataforma do compilador usado para gerar o assembly de saída. Esse parâmetro pode ter um valor igual a `x86`, `x64` ou `anycpu`. O padrão é `anycpu`. |
| `References` | Parâmetro `String[]` opcional.<br /><br /> Especifica os assemblies que são referenciados pelos tipos que exigem a serialização de XML. |
| `SdkToolsPath` | Parâmetro `String` opcional.<br /><br /> Especifica o caminho para as ferramentas do SDK, como *resgen.exe* . |
| `SerializationAssembly` | Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém o assembly de serialização gerado. |
| `SerializationAssemblyName` | Parâmetro `String` opcional.<br /><br /> Especifica o nome do assembly de serialização gerado. |
| `ShouldGenerateSerializer` | Parâmetro `Boolean` obrigatório.<br /><br /> Se `true`, a tarefa SGen deve gerar um assembly de serialização. |
| `Timeout` | Parâmetro `Int32` opcional.<br /><br /> Especifica a quantidade de tempo em milissegundos após o qual o executável da tarefa é encerrado. O valor padrão é `Int.MaxValue`, indicando que não há período de tempo limite. |
| `ToolPath` | Parâmetro `String` opcional.<br /><br /> Especifica o local de onde a tarefa carregará o arquivo executável subjacente ( *sgen.exe* ). Se esse parâmetro não for especificado, a tarefa usará o caminho de instalação do SDK correspondente à versão do Framework que está executando o MSBuild. |
| `Types` | Parâmetro `String[]` opcional.<br /><br /> Obtém ou define uma lista de tipos específicos para os quais gerar código de serialização. O SGen gerará o código de serialização somente para esses tipos. |
| `UseProxyTypes` | Parâmetro `Boolean` obrigatório.<br /><br /> Se `true`, a tarefa SGen gera o código de serialização somente para os tipos de proxy de serviço Web XML. |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="see-also"></a>Veja também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Tarefas](../msbuild/msbuild-tasks.md)
- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
