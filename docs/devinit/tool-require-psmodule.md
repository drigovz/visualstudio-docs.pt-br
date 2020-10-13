---
title: require-psmodule
description: a ferramenta devinit requer-PSModule.
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
ms.openlocfilehash: b855d8f3e9827d7b88f6d95bdf426cfb470b2bda
ms.sourcegitcommit: 3e05bd4bfac6f0b8b3534d8c013388f67e288651
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91959782"
---
# <a name="require-psmodule"></a>require-psmodule

A `require-psmodule` ferramenta é usada para instalar um [módulo do PowerShell](/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true) do [Galeria do PowerShell](https://www.powershellgallery.com/) por meio do [install-Module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true), para que ele possa ser usado em scripts do PowerShell.

> [!TIP]
> Depois que um módulo é instalado, ele ainda precisará ser importado em um script usando [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true).

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Type   | Obrigatório | Valor                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                                                   |
| [**entrada**](#input)                              | cadeia de caracteres | Sim      | Os pacotes a serem instalados. Consulte a [entrada](#input) abaixo para obter detalhes.                       |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Não usado. Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.              |

### <a name="input"></a>Entrada

A `input` propriedade deve ser o `Name` do módulo do PowerShell a ser instalado. Uma lista de módulos do PowerShell disponíveis pode ser encontrada pesquisando o [Galeria do PowerShell](https://www.powershellgallery.com/).

### <a name="additional-options"></a>Opções adicionais

As opções adicionais são passadas diretamente para o comando [install-Module](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7) e são documentadas em [Microsoft docs](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7).

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `require-psmodule` ferramenta é erro, conforme `input` necessário.

## <a name="builtin-options"></a>Opções internas

A `require-psmodule` ferramenta define um número de `Install-Module` argumentos de linha de comando para garantir que o `Install-Module` possa ser executado sem periféricos. Esses argumentos são listados abaixo e a documentação sobre eles pode ser encontrada no [install-Module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true).

| Nome         | Descrição                                                                                                                                                                                                                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **-Force**   | Instala um módulo e substitui mensagens de aviso sobre conflitos de instalação de módulo. Se um módulo com o mesmo nome já existir no computador, Force permitirá que várias versões sejam instaladas. O substituirá o módulo se existir um módulo existente com o mesmo nome e versão. Force e AllowClobber podem ser usados juntos em um comando Install-Module. |
| **-WhatIf**  | -O sinalizador WhatIf é adicionado quando a execução seca é passada para o `devinit` comando.                                                                                                                                                                                                                                                                                                       |
| **-Detalhado** | -O sinalizador detalhado é adicionado quando detalhado é passado para o `devinit` comando.                                                                                                                                                                                                                                                                                                      |


## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the PowerShellGet module.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
        },
        {
            "comments": "Installs the PowerShellGet module from a specific repository.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
            "additionalOptions": "-Repository PSGallery"
        }
    ]
}
```