---
title: require-azurecli
description: a ferramenta devinit requer-azurecli.
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
ms.openlocfilehash: da6ce656e552a7df0b02fd4a0df3a1fb78871607
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672142"
---
# <a name="require-azurecli"></a>require-azurecli

A `require-azurecli` ferramenta é usada para instalar o [CLI do Azure](/cli/azure/?view=azure-cli-latest&preserve-view=true) por meio do MSI CLI do Azure.

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                          |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | Não usado. Consulte a [entrada](#input) abaixo para obter detalhes.                               |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Não usado. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.     |

### <a name="input"></a>Entrada

Não usado.

### <a name="additional-options"></a>Opções adicionais

Não usado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `require-azurecli` ferramenta é instalar a versão mais recente do CLI do Azure e adicioná-la ao caminho (somente Windows).

## <a name="example-usage"></a>Exemplo de uso
Veja abaixo um exemplo de como executar `require-azurecli` o usando um `.devinit.json` . 

#### <a name="devinitjson-that-will-install-the-azure-cli"></a>.devinit.js, que instalará o CLI do Azure:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azurecli"
        }
    ]
}
```