---
title: windowsfeature-enable
description: ferramenta devinit WindowsFeature – habilitar.
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
ms.openlocfilehash: b24f118613fa1004275702ad27a789ec16e6a347
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874515"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

A `windowsfeature-enable` ferramenta é usada para habilitar recursos do Windows.

## <a name="usage"></a>Uso

| Nome                                             | Type   | Obrigatório | Valor                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                    |
| [**entrada**](#input)                              | string | Sim      | O recurso do Windows a ser instalado. Consulte a [entrada](#input) abaixo para obter detalhes.   |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.         |

### <a name="input"></a>Entrada

A `input` propriedade deve ser a `name` do a `windows feature` ser instalada. Uma lista de recursos disponíveis pode ser encontrada executando o `Get-WindowsFeature` cmd do PowerShell.

### <a name="additional-options"></a>Additional-Options

Nenhum.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `windowsfeature-enable` ferramenta é erro, conforme `input` necessário.

## <a name="example-usage"></a>Exemplo de uso
Abaixo estão exemplos de como executar `windowsfeature-enable` o usando um `.devinit.json` .

#### <a name="devinitjson-that-will-install-iis"></a>.devinit.jsno que irá instalar o IIS:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "web-server",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-net-framework"></a>.devinit.js, que instalará o .NET Framework:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "net-framework-features"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-net-framework-45"></a>.devinit.js, que instalará o .NET Framework 4,5:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "net-framework-45-features"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-windows-subsystem-for-linux-20"></a>.devinit.js, que instalará o subsistema do Windows para Linux 2,0:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "Microsoft-Windows-Subsystem-Linux"
        }
    ]
}
```
