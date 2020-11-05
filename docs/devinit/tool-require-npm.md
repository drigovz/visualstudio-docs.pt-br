---
title: require-npm
description: a ferramenta devinit requer-NPM.
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
ms.openlocfilehash: 87938b05b860921ee81cb2ca9191ad58fa85dd7a
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399588"
---
# <a name="require-npm"></a>require-npm

A `require-npm` ferramenta é usada para instalar o [NPM](https://www.npmjs.com/).

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                                       |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                       |
| [**entrada**](#input)                              | string | Sim      | Especifica a versão do NPM. Consulte a [entrada](#input) abaixo para obter detalhes.                           |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Não usado. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.                  |

### <a name="input"></a>Entrada

A `input` propriedade é usada para especificar a versão NPM.

### <a name="additional-options"></a>Opções adicionais

Não utilizado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `require-nodejs` ferramenta é instalar a versão mais recente do LTS do NPM.

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest LTS of NPM.",
            "tool": "require-npm"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-npm",
            "input": "6.14.6"
        }
    ]
}
```
