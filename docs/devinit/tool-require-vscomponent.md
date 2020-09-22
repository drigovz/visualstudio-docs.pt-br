---
title: require-vscomponent
description: a ferramenta devinit requer-vscomponent.
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
ms.openlocfilehash: 7c47c219fa0c0ef32946d6e0500bc37ce9aec0ff
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005033"
---
# <a name="require-vscomponent"></a>require-vscomponent

A `require-vscomponent` ferramenta é usada para importar configurações do Visual Studio para o Visual Studio existente. Leia mais sobre `.vsconfig` [aqui](https://docs.microsoft.com/visualstudio/install/import-export-installation-configurations).

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                     | Tipo   | Obrigatório | Valor                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **feitos**                             | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                |
| [**entrada**](#input)                      | Cadeia de caracteres | No       | O caminho completo de `.vsconfig` . Consulte a [entrada](#input) abaixo para obter detalhes. |
| [additionalOptions](#additional-options) | Cadeia de caracteres | No       | Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.     |

### <a name="input"></a>Entrada

A `input` propriedade é usada para especificar o caminho completo do `.vsconfig` arquivo. Se não for mencionado, a ferramenta pesquisará um `.vsconfig` no diretório atual e passará o valor para o instalador do Visual Studio.

### <a name="additional-options"></a>Opções adicionais

Não usado.

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `require-vscomponent` ferramenta é procurar um `.vsconfig` arquivo no diretório atual e executar o instalador do Visual Studio com esses detalhes no modo silencioso. `require-vscomponent` o só dá suporte à modificação de uma instalação existente do Visual Studio.

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "comments": "Imports .vsconfig file which is passed as input to Visual Studio.",
            "input": "C:\\.vsconfig"
        }
    ]
}
```
