---
title: WindowsFeature-lista
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
ms.openlocfilehash: 6c4c20fb92e0d854eb7745a598efabd7ac426bfc
ms.sourcegitcommit: 417ea66a8b07ec102ece2fa00e07b88edc404c00
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91127820"
---
# <a name="windowsfeature-list"></a>WindowsFeature-lista

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
    "$schema": "./devinit.schema-2.0.json",
    "run": [
        {
            "comments": "Lists the state of all Windows features.",
            "tool": "windowsfeature-list"
        }
    ]
}
```
