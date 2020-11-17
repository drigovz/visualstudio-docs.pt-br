---
title: choco-install
description: devinit ferramenta choco-instale para instalar pacotes de Chocolatey.
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
ms.openlocfilehash: 82c1bfbaed4a8ae5540447991f1a097760ade0bd
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671936"
---
# <a name="choco-install"></a>choco-install

A `choco-install` ferramenta pode ser usada para instalar e atualizar pacotes de [Chocolatey](https://chocolatey.org/) .

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta não fará nada.

| Nome                                             | Tipo   | Obrigatório | Valor                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                                          |
| [**entrada**](#input)                              | Cadeia de caracteres | No       | O pacote a instalar. Consulte a [entrada](#input) abaixo para obter detalhes.                                                 |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Opções adicionais a serem passadas para a ferramenta. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.       |

### <a name="input"></a>Entrada

A `input` propriedade é usada para especificar o nome do pacote a ser instalado (por exemplo, ' MongoDB ') ou o caminho para um arquivo de configuração dos seguintes formatos _packages.config_, _. nuspec_ e _. nupkg_. O valor de `input` será acrescentado a um `choco install` comando (por exemplo `choco install mongodb` ), juntamente com quaisquer argumentos específicos no [`additionalOptions`](#additional-options) e as `choco` Opções internas (definidas [abaixo](#built-in-options)). Os pacotes podem ser encontrados na [Galeria de pacotes de chocolate](https://chocolatey.org/packages). Ao usar um arquivo de configuração, você pode passar o caminho para esse arquivo na `input` propriedade, por exemplo `"input":"packages.config"` .

### <a name="additional-options"></a>Opções adicionais

Opções de configuração adicionais podem ser passadas como um valor de `additionalOptions` . Esses argumentos são passagem direta para os argumentos usados pelo [`choco install`](https://chocolatey.org/docs/commands-install) e são definidos na documentação de Chocolatey.

### <a name="built-in-options"></a>Opções internas

A `choco-install` ferramenta define um número de `choco` argumentos de linha de comando para garantir que o `choco` possa ser executado sem periféricos. Esses argumentos estão listados abaixo e a documentação sobre eles pode ser encontrada na [documentação do Chocolatey](https://chocolatey.org/docs/).

| Name                  | Descrição                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Sim**             | Confirmar todos os prompts – escolha a resposta afirmativo em vez de solicitar. Requer `--accept-license.` |
| **--sem progresso**     | Não mostrar o progresso-as porcentagens de progresso não serão mostradas.                                         |
| **--Skip-PowerShell** | Ignorar PowerShell-chocolateyInstall.ps1 não será executado.                                              |

## <a name="example-usage"></a>Exemplo de uso
Abaixo estão exemplos de como executar `choco-install` o usando um `.devinit.json` . 

#### <a name="devinitjson-that-will-install-packages-listed-in-packagesconfig"></a>.devinit.jsno que instalarão os pacotes listados em packages.config:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-mongodb"></a>.devinit.js, que instalará o MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-mongodb"></a>.devinit.js, que instalará uma versão específica do MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```