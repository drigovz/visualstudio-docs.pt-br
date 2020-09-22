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
ms.openlocfilehash: 115fda00f880e9c2fa1782735dd471fc3df68936
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005970"
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

### <a name="additional-options"></a>Opções adicionais

nenhuma.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `windowsfeature-enable` ferramenta é erro, conforme `input` necessário.

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
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
