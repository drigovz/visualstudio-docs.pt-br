---
title: npm-install
description: devinit ferramenta NPM-install.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: c69d9464622e1814f6289c925423a6674f113a2f
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440426"
---
# <a name="npm-install"></a>npm-install

A `npm-install` ferramenta pode ser usada para instalar pacotes do [NPM](https://www.npmjs.com/) .

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta não fará nada.

| Nome                                             | Type   | Obrigatório | Valor                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                                          |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | O pacote a instalar. Consulte a [entrada](#input) abaixo para obter detalhes.                                                 |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Opções adicionais a serem passadas para a ferramenta. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.       |

### <a name="input"></a>Entrada

A `input` propriedade é usada para especificar o nome do pacote a ser instalado (por exemplo, ' Mongo ').

### <a name="additional-options"></a>Opções adicionais

Opções de configuração adicionais podem ser passadas como um valor de `additionalOptions` . Esses argumentos são passagem direta para os argumentos usados pela [instalação do NPM](https://docs.npmjs.com/cli/install).

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `npm-install` ferramenta é executar `npm install` sem argumentos. Consulte [a documentação do NPM](https://docs.npmjs.com/cli/v6/commands/npm-install) para obter uma descrição desse comportamento.

## <a name="example-usage"></a>Exemplo de uso
Veja abaixo um exemplo de como executar `npm-install` o usando um `.devinit.json` .

#### <a name="devinitjson-that-will-install-mongo"></a>.devinit.js, que instalará o Mongo:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "npm-install",
            "input": "mongo",
        }
    ]
}
```
