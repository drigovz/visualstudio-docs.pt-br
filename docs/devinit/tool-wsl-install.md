---
title: wsl-install
description: devinit ferramenta WSL-install.
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
ms.openlocfilehash: 950ca7f1e9c43123b206893dbc6a07da7c3743ec
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862859"
---
# <a name="wsl-install"></a>wsl-install

A `wsl-install` ferramenta é usada para instalar o Linux distribuições para o [subsistema do Windows para Linux](/windows/wsl/) (WSL).

A `wsl-install` ferramenta requer que o WSL 2 já esteja habilitado no Windows. Se, por algum motivo, o WSL2 não estiver habilitado, você poderá habilitar o WSL2 usando a ferramenta de [habilitação de WindowsFeature](tool-windowsfeature-enable.md) e o nome do recurso `Microsoft-Windows-Subsystem-Linux` .

## <a name="usage"></a>Uso

Se as `input` Propriedades e `additionalOptions` forem omitidas ou vazias, a ferramenta seguirá o comportamento [padrão](#default-behavior) detalhado abaixo.

| Nome                                             | Type   | Obrigatório | Valor                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **feitos**                                     | Cadeia de caracteres | No       | Propriedade de comentários opcional. Não usado.                             |
| [**entrada**](#input)                              | string | Sim      | O distribuição a ser instalado. Consulte a [entrada](#input) abaixo para obter detalhes.     |
| [**additionalOptions**](#additional-options)     | Cadeia de caracteres | No       | Consulte [as opções adicionais](#additional-options) abaixo para obter detalhes.  |

### <a name="input"></a>Entrada

O URI para o pacote de distribuição de aplicativo AppX ( `.appx` ) que contém o distribuição a ser implantado. O URI deve apontar para um `.appx` arquivo que contém um único `install.tar.gz` na raiz do arquivo ou dentro de um arquivo interno `.appx` . Exemplos de distribuições com suporte incluem:

| Distribuição                          | Uri                                                           |
|---------------------------------|---------------------------------------------------------------|
| Ubuntu 20.04                    | https://aka.ms/wslubuntu2004                                  |
| Ubuntu 18.04                    | https://aka.ms/wsl-ubuntu-1804                                |
| Ubuntu 16.04                    | https://aka.ms/wsl-ubuntu-1604                                |
| Debian GNU/Linux                | https://aka.ms/wsl-debian-gnulinux                            |
| Kali Linux                      | https://aka.ms/wsl-kali-linux-new                             |
| OpenSUSE Leap 42                | https://aka.ms/wsl-opensuse-42                                |
| SUSE Linux Enterprise Server 12 | https://aka.ms/wsl-sles-12                                    |

> [!NOTE]
> No momento, não há suporte para distribuições do ARM Linux no Codespaces do GitHub.

### <a name="additional-options"></a>Opções adicionais

Há suporte para várias opções adicionais:

| Nome                      | Type      | Obrigatório | Valor                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --WSL-versão             | Cadeia de caracteres    | No       | Versão do WSL a ser usada. O valor padrão é 2.                                                                                                                                  |
| --pós-criação-comando     | Cadeia de caracteres    | No       | O comando a ser executado dentro do distribuição do Linux quando a instalação for concluída. O comando deve ser formatado como uma única palavra ou encapsulado entre aspas. O padrão é nenhum comando.  |

### <a name="default-behavior"></a>Comportamento padrão

O comportamento padrão da `wsl-install` ferramenta é erro como a `input` propriedade, o distribuição a ser instalado, é necessário.

## <a name="example-usage"></a>Exemplo de uso

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        },
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and echo 'Hello from Ubuntu!' after installing.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        },
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```