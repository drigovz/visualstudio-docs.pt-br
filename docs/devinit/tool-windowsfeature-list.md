---
title: windowsfeature-list
description: ferramenta devinit WindowsFeature-lista.
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
ms.openlocfilehash: 43370389aaffdb4395248fed6ec83de39f16c86d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874501"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

A `windowsfeature-list` ferramenta é usada para listar o estado de Habilitação/desabilitação de todos os recursos do Windows.

| Nome                                             | Type   | Obrigatório | Valor                                      |
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
Veja abaixo um exemplo de como executar `windowsfeature-list` o usando um `.devinit.json` .

#### <a name="devinitjson-that-will-list-the-state-of-all-windows-features"></a>.devinit.js, que listará o estado de todos os recursos do Windows:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "windowsfeature-list"
        }
    ]
}
```
