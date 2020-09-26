---
title: require-dotnetcoresdk
description: a ferramenta devinit requer-dotnetcoresdk.
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
ms.openlocfilehash: c632378ff15e9b52e7145821f2e16d782b0326ac
ms.sourcegitcommit: 13cf7569f62c746708a6ced1187d8173eda7397c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352290"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

A `require-dotnetcoresdk` ferramenta é usada para instalar o [SDK do .NET Core](https://dotnet.microsoft.com/) e o tempo de execução compartilhado por meio do script [dotnet-install](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) .

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Type   | Obrigatório | Valor                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                               |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | A versão do SDK do .NET Core a ser instalada. Consulte a [entrada](#input) abaixo para obter detalhes. |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.                    |

### <a name="input"></a>Entrada

A `input` propriedade é usada para especificar a versão de SDK do .NET Core a ser instalada. Uma lista de versões pode ser encontrada no [site dotnet-Core](https://dotnet.microsoft.com/download/dotnet-core).

### <a name="additional-options"></a>Opções adicionais

Opções de configuração adicionais podem ser passadas como um valor de `additionalOptions` . Esses argumentos são uma passagem direta para os argumentos usados no script [dotnet-install](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) . Para obter mais informações sobre os parâmetros disponíveis, consulte a [documentação](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) do script [dotnet-install](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) . Ao usar `additionalOptions` o, certifique-se de usar os nomes e o formato do argumento do PowerShell.

> [!NOTE]
> Qualquer valor adicional para um argumento que inclua um espaço deve incluir um par adicional de aspas de escape (usando barra invertida). Um exemplo pode ser visto no [uso de exemplo](#example-usage) usando `-InstallDir` .

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `require-dotnetcoresdk` ferramenta é instalar a versão do SDK do .NET Core especificado em um `global.json` arquivo [(documentação)](https://docs.microsoft.com/dotnet/core/tools/global-json?tabs=netcore3x) no diretório de trabalho atual. Se nenhum `global.json` arquivo for encontrado, `require-dotnetcoresdk` o instalará a versão atual mais recente do SDK do .NET Core e o tempo de execução compartilhado.

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest or, if present, the SDK version from a global.json file.",
            "tool": "require-dotnetcoresdk"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        },
        {
            "comments": "Example that will install a specific version and the aspnetcore runtime.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        },
        {
            "comments": "Example that will install in a specific directory.",
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\\Program Files\\dotnet\""
        }
    ]
}
```
