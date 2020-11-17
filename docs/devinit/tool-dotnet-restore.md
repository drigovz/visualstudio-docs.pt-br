---
title: dotnet-restore
description: ferramenta devinit dotnet – restaurar.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 51c6ed6576fefe3853bca7f4250c1884bd364f64
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671929"
---
# <a name="dotnet-restore"></a>dotnet-restore

A `dotnet-restore` ferramenta restaura dependências e ferramentas específicas do projeto que são especificadas no arquivo de projeto. Leia mais sobre dotnet restore [aqui](/dotnet/core/tools/dotnet-restore).

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | Caminho para o arquivo de projeto/solução a ser restaurado. Consulte a [entrada](#input) abaixo para obter detalhes. |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.                     |

### <a name="input"></a>Entrada

Caminho para o arquivo de projeto/solução a ser restaurado.

### <a name="additional-options"></a>Opções adicionais

As opções adicionais são passadas como estão para o comando dotnet restore.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `dotnet-restore` ferramenta é executar ' dotnet Restore ' no diretório atual.

## <a name="example-usage"></a>Exemplo de uso
Veja abaixo um exemplo de como executar `dotnet-restore` o usando um `.devinit.json` . 

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.jsno que irá restaurar as dependências e as ferramentas de um projeto:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-restore",
            "input": "C:\\app1\\app1.csproj"
        }
    ]
}
```