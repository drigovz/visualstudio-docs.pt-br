---
title: require-nodejs
description: a ferramenta devinit requer-NodeJS.
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
ms.openlocfilehash: ca1d5e48ab61926336aecebb1a2a4b794c704482
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842669"
---
# <a name="require-nodejs"></a>require-nodejs

A `require-nodejs` ferramenta é usada para instalar o [Node.js](https://nodejs.org/) por meio de um MSI distribuído pela organização do Node.js.

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Type   | Obrigatório | Valor                                                                     |
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
Abaixo estão exemplos de como executar `require-nodejs` o usando um `.devinit.json` . 

#### <a name="devinitjson-that-will-install-the-lts-of-nodejs"></a>.devinit.js, que instalará o LTS de Node.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-nodejs"></a>.devinit.js, que instalará uma versão específica do Node.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
