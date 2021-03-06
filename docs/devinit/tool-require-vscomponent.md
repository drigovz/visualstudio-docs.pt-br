---
title: require-vscomponent
description: a ferramenta devinit requer-vscomponent.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 50172f96a49e2384553a372ded0c889b30a23fff
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2021
ms.locfileid: "100006392"
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

Opções de configuração adicionais podem ser passadas como um valor de `additionalOptions` . 

| Nome                      | Tipo      | Obrigatório | Valor                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --installPath             | Cadeia de caracteres    | No       | O caminho de instalação da instância do Visual Studio que você deseja modificar.                                                                                                                       |

Se nenhum caminho de instalação for especificado, a ferramenta modificará o Visual Studio instalado mais antigo em seu computador se houver várias instâncias em seu computador. 

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

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path-to-the-visual-studio-instance-specified-via-an-install-path"></a>.devinit.js, que importará as configurações de um determinado caminho de arquivo. vsconfig para a instância do Visual Studio especificada por meio de um caminho de instalação:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig",
            "additionalOptions": "--installPath 'C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Enterprise'"
        }
    ]
}
```