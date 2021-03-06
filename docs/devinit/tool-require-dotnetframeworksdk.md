---
title: require-dotnetframeworksdk
description: a ferramenta devinit requer-dotnetframeworksdk.
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
ms.openlocfilehash: 5a4d68119ceb21553d7db1f6384904579003ce92
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937147"
---
# <a name="require-dotnetframeworksdk"></a>require-dotnetframeworksdk

A `require-dotnetframeworksdk` ferramenta é usada para instalar o [SDK do .NET Framework](https://dotnet.microsoft.com/) por meio dos [instaladores fornecidos](https://dotnet.microsoft.com/download/visual-studio-sdks).

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório  | Valor                                                                                    |
|--------------------------------------------------|--------|-----------|------------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No        | Propriedade de comentários opcional. Não usado.                                                    |
| [**entrada**](#input)                              | Cadeia de caracteres | No        | A versão do SDK do .NET Framework para instalar. Consulte a [entrada](#input) abaixo para obter detalhes. |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No        | Não usado. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.               |

### <a name="input"></a>Entrada

A `input` propriedade é usada para especificar a versão .NET Framework SDK a ser instalada. Uma lista de versões pode ser encontrada no [site DOTNET-Framework](https://dotnet.microsoft.com/download/visual-studio-sdks).

### <a name="additional-options"></a>Opções adicionais

Não usado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `require-dotnetframeworksdk` ferramenta é instalar a versão mais recente. Consulte os [instaladores fornecidos](https://dotnet.microsoft.com/download/visual-studio-sdks) para obter a versão mais recente.

## <a name="example-usage"></a>Exemplo de uso
Abaixo estão exemplos de como executar `require-dotnetframeworksdk` o usando um `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-latest-net-framework"></a>.devinit.jsque instalará o .NET Framework mais recente:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetframeworksdk"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-the-net-framework"></a>.devinit.js, que instalará uma versão específica do .NET Framework:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetframeworksdk",
            "input": "4.8.0"
        }
    ]
}
```