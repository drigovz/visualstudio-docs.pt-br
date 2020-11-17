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
ms.openlocfilehash: b521009affbc1db81676481e33640a69e619aaf3
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671708"
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
