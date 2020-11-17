---
title: dotnet-toolinstall
description: ferramenta devinit dotnet-toolinstall.
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
ms.openlocfilehash: 85a8beafdc9b19a807becabb459baa5de88169e2
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672215"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

A `dotnet-toolinstall` ferramenta é usada para instalar as [Ferramentas do .NET Core](https://dotnet.microsoft.com/) por meio do `dotnet tool update` comando.

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                 |
| [**entrada**](#input)                              | string | Sim      | A ferramenta .NET Core a ser instalada. Consulte a [entrada](#input) abaixo para obter detalhes. |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.      |

### <a name="input"></a>Entrada

A `input` propriedade é usada para especificar a ferramenta do .NET Core a ser instalada. Há uma lista não oficial de ferramentas em [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) .

### <a name="additional-options"></a>Opções adicionais

Opções de configuração adicionais podem ser passadas como um valor de `additionalOptions` . Esses argumentos são uma passagem direta para os argumentos usados pelo [`dotnet tool update`](/dotnet/core/tools/global-tools#update-a-tool) comando. 

O `dotnet tool update` comando é usado para lidar com segurança com o caso em que uma ferramenta já está instalada.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `dotnet-toolinstall` ferramenta é erro, conforme `input` necessário.

## <a name="example-usage"></a>Exemplo de uso
Abaixo estão exemplos de como executar `dotnet-toolinstall` o usando um `.devinit.json` . 

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool"></a>.devinit.js, que instalará a ferramenta dotnet-Trace:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool-as-a-global-tool"></a>.devinit.js, que instalará a ferramenta dotnet-Trace como uma ferramenta global:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace",
            "additionalOptions": "--global"
        }
    ]
}
```