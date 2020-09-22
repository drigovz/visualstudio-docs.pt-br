---
title: choco-upgrade
description: devinit Tool choco-upgrade.
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
ms.openlocfilehash: 5a735b60fd318d86e97dc4db7570e952a0fcdfd8
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006032"
---
# <a name="choco-upgrade"></a>choco-upgrade

A `choco-upgrade` ferramenta pode ser usada para instalar e atualizar pacotes de [Chocolatey](https://chocolatey.org/docs/commandsupgrade) .

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta não fará nada.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                                          |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | O pacote a ser atualizado. Consulte a [entrada](#input) abaixo para obter detalhes.                                                 |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Opções adicionais a serem passadas para a ferramenta. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.       |

### <a name="input"></a>Entrada

A `input` propriedade é usada para especificar o nome do pacote a ser atualizado (por exemplo, ' MongoDB ') ou o caminho para um arquivo de configuração dos seguintes formatos _packages.config_, _. nuspec_e _. nupkg_. O valor de `input` será acrescentado a um `choco upgrade` comando (por exemplo `choco upgrade mongodb` ), juntamente com quaisquer argumentos específicos no [`additionalOptions`](#additional-options) e as `choco` Opções internas (definidas [abaixo](#built-in-options)). Os pacotes podem ser encontrados na [Galeria de pacotes de chocolate](https://chocolatey.org/packages). Ao usar um arquivo de configuração, você pode passar o caminho para esse arquivo na `input` propriedade, por exemplo: `"input":"packages.config"` .

### <a name="additional-options"></a>Opções adicionais

Opções de configuração adicionais podem ser passadas como um valor de `additionalOptions` . Esses argumentos são passagem direta para os argumentos usados pelo [`choco upgrade`](https://chocolatey.org/docs/commands-upgrade) e são definidos na documentação de Chocolatey.

## <a name="built-in-options"></a>Opções internas

A `choco-upgrade` ferramenta define um número de `choco` argumentos de linha de comando para garantir que o `choco` possa ser executado sem periféricos. Esses argumentos estão listados abaixo e a documentação sobre eles pode ser encontrada na [documentação do Chocolatey](https://chocolatey.org/docs/).

| Name                  | Descrição                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Sim**             | Confirmar todos os prompts – escolha a resposta afirmativo em vez de solicitar. Implica `--accept-license` . |
| **--sem progresso**     | Não mostrar o progresso-as porcentagens de progresso não serão mostradas.                                         |
| **--Skip-PowerShell** | Ignorar PowerShell-chocolateyInstall.ps1 não será executado.                                              |

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of upgrading packages listed in a packages.config file.",
            "tool": "choco-upgrade",
            "input": "packages.config",
        },
        {
            "comments": "Example that will upgrade the package 'mongodb'.",
            "tool": "choco-upgrade",
            "input": "mongodb"
        },
        {
            "comments": "Example that will upgrade the '4.2.7' version of 'mongodb'.",
            "tool": "choco-upgrade",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```
