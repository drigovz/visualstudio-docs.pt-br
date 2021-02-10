---
title: exigir-Winget
description: a ferramenta devinit requer-Winget.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 9cc805841f5d89e41b82f899eda1b131f60baee4
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2021
ms.locfileid: "100012353"
---
# <a name="require-winget"></a>exigir-Winget

A `require-winget` ferramenta é usada para instalar o [Winget](https://docs.microsoft.com/windows/package-manager/winget/). 
## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | Não usado.                                                                            |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Não usado.                                                                            |

### <a name="input"></a>Entrada

Não usado.

### <a name="additional-options"></a>Opções adicionais

Não usado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `require-winget` ferramenta é instalar a versão mais recente usando o [ `winget-cli` repositório git](https://github.com/microsoft/winget-cli).

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-6.0",
    "comments": "Example that installs the latest version of winget",
    "run": [
        {
            "tool": "require-winget",
            "comments": "Installs winget",
        }
    ]
}
```
