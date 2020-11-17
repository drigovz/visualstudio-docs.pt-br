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
ms.openlocfilehash: e9d2f546e99f83b4c53d0b76abfdaf8ec91868ac
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672107"
---
# <a name="require-vscomponent"></a>require-vscomponent

A `require-vscomponent` ferramenta é usada para importar configurações do Visual Studio para o Visual Studio existente. Leia mais sobre `.vsconfig` [aqui](../install/import-export-installation-configurations.md).

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
Veja abaixo um exemplo de como executar `require-vscomponent` o usando um `.devinit.json` . 

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path"></a>.devinit.js, que importará as configurações de um determinado caminho de arquivo. vsconfig:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig"
        }
    ]
}
```