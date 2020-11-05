---
title: windowsfeature-enable
description: ferramenta devinit WindowsFeature – habilitar.
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
ms.openlocfilehash: 6e3d2fdaf6be019cae504d4f71258d410d232ff5
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400201"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

A `windowsfeature-enable` ferramenta é usada para habilitar recursos do Windows.

## <a name="usage"></a>Uso

| Nome                                             | Tipo   | Obrigatório | Valor                                                                    |
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Installs IIS.",
            "tool": "windowsfeature-enable",
            "input": "web-server",
        },
        {
            "comments": "Installs the .NET Framework 3.5.",
            "tool": "windowsfeature-enable",
            "input": "net-framework-features"
        },
        {
            "comments": "Installs the .NET Framework 4.5.",
            "tool": "windowsfeature-enable",
            "input": "net-framework-45-features"
        },
        {
            "comments": "Installs Windows Subsystem for Linux 2.0.",
            "tool": "windowsfeature-enable",
            "input": "Microsoft-Windows-Subsystem-Linux"
        }
    ]
}
```
