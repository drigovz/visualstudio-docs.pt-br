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
ms.openlocfilehash: 8a649cec23a8f0090500a493fe577b3ba41788f9
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005977"
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

### <a name="additional-options"></a>Opções adicionais

nenhuma.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `windowsfeature-disable` ferramenta é erro, conforme `input` necessário.

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs IIS.",
            "tool": "require-windowsfeature",
            "input": "web-server",
        }
    ]
}
```
