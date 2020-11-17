---
title: windowsfeature-disable
description: ferramenta devinit WindowsFeature-desabilitar.
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
ms.openlocfilehash: 1f06f89a61b77bd4c323303ca796252d4874b3cc
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671728"
---
# <a name="windowsfeature-disable"></a>windowsfeature-disable

A `windowsfeature-disable` ferramenta é usada para adquirir recursos do Windows.

## <a name="usage"></a>Uso

| Nome                                             | Tipo   | Obrigatório | Valor                                                                  |
|--------------------------------------------------|--------|----------|------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                  |
| [**entrada**](#input)                              | string | Sim      | O recurso do Windows a ser instalado. Consulte a [entrada](#input) abaixo para obter detalhes. |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.       |

### <a name="input"></a>Entrada

A `input` propriedade deve ser a `name` do a `windows feature` ser desabilitada.

### <a name="additional-options"></a>Additional-Options

nenhuma.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `windowsfeature-disable` ferramenta é erro, conforme `input` necessário.

## <a name="example-usage"></a>Exemplo de uso
Veja abaixo um exemplo de como executar `windowsfeature-disable` o usando um `.devinit.json` . 

#### <a name="devinitjson-that-will-disable-a-specified-feature"></a>.devinit.js, que desabilitará um recurso especificado:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-windowsfeature",
            "input": "web-server",
        }
    ]
}
```
