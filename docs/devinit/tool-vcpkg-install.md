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
ms.openlocfilehash: 6e10887e09c329a241aab7f18c6170c873705fbf
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672048"
---
# <a name="vcpkg-install"></a>vcpkg-install

A `vcpkg-install` ferramenta é usada para adquirir bibliotecas C/C++ (chamadas de portas) usando [vcpkg](https://github.com/microsoft/vcpkg).

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                   |
| [**entrada**](#input)                              | string | Sim      | Os pacotes a serem instalados. Consulte a [entrada](#input) abaixo para obter detalhes.                       |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.                        |

### <a name="input"></a>Entrada

A `input` propriedade deve ser a `name` do a ser `vcpkg` instalada ou uma lista de nomes separados por espaço para instalar vários pacotes. Uma lista de portas disponíveis pode ser encontrada no [repositório GitHub vcpkg](https://github.com/microsoft/vcpkg/tree/master/ports).

### <a name="additional-options"></a>Opções adicionais

Opções adicionais são passadas diretamente para o comando [vcpkg](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) e são documentadas no [repositório GitHub vcpkg](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md).

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `vcpkg-install` ferramenta é erro, conforme `input` necessário.

## <a name="example-usage"></a>Exemplo de uso
Abaixo estão exemplos de como executar `vcpkg-install` o usando um `.devinit.json` . 

#### <a name="devinitjson-that-will-install-the-sdl2-port"></a>.devinit.js, que instalará a porta sdl2:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "vcpkg-install",
            "input": "sdl2",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-multiple-ports"></a>.devinit.jsno que instalará várias portas:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [

        {
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```