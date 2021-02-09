---
title: nuget-restore
description: ferramenta devinit NuGet-Restore.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: f805b5c1c7b3b994c984dfdb6ce937f8cd51edf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99848228"
---
# <a name="nuget-restore"></a>nuget-restore

A `nuget-restore` ferramenta restaura dependências e ferramentas específicas do projeto que são especificadas no arquivo de projeto. Leia mais sobre a restauração do NuGet [aqui](/nuget/reference/cli-reference/cli-ref-restore).

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

As opções adicionais são passadas no estado em que se encontram para o comando de restauração do NuGet.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `nuget-restore` ferramenta é executar `NuGet restore` no diretório atual.

## <a name="example-usage"></a>Exemplo de uso
Veja abaixo um exemplo de como executar `nuget-restore` o usando um `.devinit.json` .

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.jsno que irá restaurar as dependências e as ferramentas de um projeto:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "nuget-restore",
            "input": "C:\\nuget\\Nuget.config"
        }
    ]
}
```