---
title: npm-install
description: devinit ferramenta NPM-install.
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
ms.openlocfilehash: 432c2a6c532e95e7d0e3e4cb22c87930031f5907
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400291"
---
# <a name="npm-install"></a>npm-install

A `npm-install` ferramenta pode ser usada para instalar pacotes do [NPM](https://www.npmjs.com/) .

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta não fará nada.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                                          |
| [**entrada**](#input)                              | string | Sim      | O pacote a instalar. Consulte a [entrada](#input) abaixo para obter detalhes.                                                 |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Opções adicionais a serem passadas para a ferramenta. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.       |

### <a name="input"></a>Entrada

A `input` propriedade é usada para especificar o nome do pacote a ser instalado (por exemplo, ' Mongo ').

### <a name="additional-options"></a>Opções adicionais

Opções de configuração adicionais podem ser passadas como um valor de `additionalOptions` . Esses argumentos são passagem direta para os argumentos usados pela [instalação do NPM](https://docs.npmjs.com/cli/install).

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will install the mongo NPM package (https://www.npmjs.com/package/mongo).",
            "tool": "npm-install",
            "input": "mongo",
        }
    ]
}
```
