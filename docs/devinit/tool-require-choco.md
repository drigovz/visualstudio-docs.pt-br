---
title: require-choco
description: a ferramenta devinit requer-Choco.
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
ms.openlocfilehash: d9ecd12a36621ab2a21f94014d6a0fd13568609b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671875"
---
# <a name="require-choco"></a>require-choco

A `require-choco` ferramenta pode ser usada para instalar o [Chocolatey](https://chocolatey.org/).

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                      |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                      |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | Não usado. Consulte a [entrada](#input) abaixo para obter detalhes.                           |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Não usado. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes. |

### <a name="input"></a>Entrada

Não usado.

### <a name="additional-options"></a>Opções adicionais

Não usado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `require-choco` ferramenta é instalar o Chocolatey e adicioná-lo ao caminho (somente Windows).

## <a name="example-usage"></a>Exemplo de uso
Veja abaixo um exemplo de como executar `require-choco` o usando um `.devinit.json` . 

#### <a name="devinitjson-that-will-install-chocolatey"></a>.devinit.jsno que instalará o Chocolatey:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-choco"
        }
    ]
}
```