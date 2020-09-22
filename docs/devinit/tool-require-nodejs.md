---
title: require-nodejs
description: a ferramenta devinit requer-NodeJS.
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
ms.openlocfilehash: ce4a156a313e3d8d0afc82ababd49d0528b315f5
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005773"
---
# <a name="require-nodejs"></a>require-nodejs

A `require-nodejs` ferramenta é usada para instalar o [Node.js](https://nodejs.org/) por meio de um MSI distribuído pela organização do Node.js.

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                     |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                     |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | A versão do Node.JS a ser instalada. Consulte a [entrada](#input) abaixo para obter detalhes. |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.          |

### <a name="input"></a>Entrada

A `input` propriedade é usada para especificar a versão de Node.js. Uma lista de versões pode ser encontrada na [ página de downloadNode.js](https://nodejs.org/en/download/). O número de versão completo é obrigatório. Minor. caminho (por exemplo 14.4.0) se algum for omitido, a instalação falhará.

### <a name="additional-options"></a>Opções adicionais

Opções de configuração adicionais podem ser passadas como um valor de `additionalOptions` . Esses argumentos são passagem direta para o instalador MSI para Node.js.  

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `require-nodejs` ferramenta é instalar a versão mais recente do LTS do nó, conforme detalhado no [site](https://nodejs.org/en/download/)Node.JS.

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest LTS of Node.JS.",
            "tool": "require-nodejs"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
