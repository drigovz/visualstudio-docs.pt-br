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
ms.openlocfilehash: 2febd8a62e041384c8acf5b7b0b5e1c974597c0a
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862250"
---
# <a name="dotnet-restore"></a>dotnet-restore

A `dotnet-restore` ferramenta restaura dependências e ferramentas específicas do projeto que são especificadas no arquivo de projeto. Leia mais sobre dotnet restore [aqui](/dotnet/core/tools/dotnet-restore).

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Type   | Obrigatório | Valor                                                                                |
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that builds the 'kitchen sink'",
    "run": [
        {
            "tool": "dotnet-restore",
            "comments": "Restores the dependencies and tools of a project using dotnet core.",
            "input": "C:\\app1\\app1.csproj"
        }
    ]
}
```