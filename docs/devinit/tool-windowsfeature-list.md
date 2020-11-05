---
title: windowsfeature-list
description: ferramenta devinit WindowsFeature-lista.
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
ms.openlocfilehash: 3030ddaaa3cc19b8719b067d9bd5e3572957b84f
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400194"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

A `windowsfeature-list` ferramenta é usada para listar o estado de Habilitação/desabilitação de todos os recursos do Windows.

| Nome                                             | Tipo   | Obrigatório | Valor                                      |
|--------------------------------------------------|--------|----------|--------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.      |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | Não usado. Ignorado.                         |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Não usado. Ignorado.                         |

### <a name="input"></a>Entrada

Não usado. Ignorado.

#### <a name="additional-options"></a>Opções adicionais

Não usado. Ignorado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `windowsfeature-list` ferramenta é listar o estado de Habilitação/desabilitação de todos os recursos do Windows.

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "comments": "Lists the state of all Windows features.",
            "tool": "windowsfeature-list"
        }
    ]
}
```
