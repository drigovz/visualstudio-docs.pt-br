---
title: vcpkg-install
description: devinit ferramenta vcpkg-install.
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
ms.openlocfilehash: 6744e8fb3b42f81f6d0814646cab1f2388ebe577
ms.sourcegitcommit: 3e05bd4bfac6f0b8b3534d8c013388f67e288651
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91959755"
---
# <a name="vcpkg-install"></a>vcpkg-install

A `vcpkg-install` ferramenta é usada para adquirir bibliotecas C/C++ (chamadas de portas) usando [vcpkg](https://github.com/microsoft/vcpkg).

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Type   | Obrigatório | Valor                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                   |
| [**entrada**](#input)                              | cadeia de caracteres | Sim      | Os pacotes a serem instalados. Consulte a [entrada](#input) abaixo para obter detalhes.                       |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.                        |

### <a name="input"></a>Entrada

A `input` propriedade deve ser a `name` do a ser `vcpkg` instalada ou uma lista de nomes separados por espaço para instalar vários pacotes. Uma lista de portas disponíveis pode ser encontrada no [repositório GitHub vcpkg](https://github.com/microsoft/vcpkg/tree/master/ports).

### <a name="additional-options"></a>Opções adicionais

Opções adicionais são passadas diretamente para o comando [vcpkg](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) e são documentadas no [repositório GitHub vcpkg](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md).

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `vcpkg-install` ferramenta é erro, conforme `input` necessário.

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the sdl2 port.",
            "tool": "vcpkg-install",
            "input": "sdl2",
        },
        {
            "comments": "Installs the sdl2 and sqlite3 ports.",
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```