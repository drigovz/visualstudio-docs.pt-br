---
title: OpenCV
description: Exemplo de personalização usando o devinit para o Linux e o Windows para o repositório OpenCV.
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
ms.openlocfilehash: a2f284e1e464ab41391f60c546ce01d418ff377b
ms.sourcegitcommit: 8efe6b45d65f9db23f5575c15155fe363fa12cdb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92750122"
---
# <a name="opencv"></a>OpenCV

Este exemplo ilustra como personalizar o [GitHub Codespaces](https://github.com/features/codespaces) para desenvolver com projetos de várias plataformas, como [OpenCV/OpenCV](https://github.com/opencv/opencv).

As personalizações a seguir já estão aplicadas na bifurcação [Microsoft/OpenCV](https://github.com/microsoft/opencv) e permitem criar o direcionamento para o Windows e o Ubuntu.

## <a name="customization-with-devcontainerjson-and-devinitjson"></a>Personalização com devcontainer.jse devinit.jsem

O `.devcontainer` diretório precisa conter os seguintes arquivos:

* devcontainer.jsem
* devinit.jsem

### <a name="devcontainerjson"></a>devcontainer.jsem

Veja a seguir o conteúdo do _devcontainer.jsno_ arquivo.

```json
{
  "postCreateCommand": "devinit init"
}
```

O `postCreateCommand` inicia a ferramenta  [devinit](devinit-and-codespaces.md) , que consome _devinit.jsem_ .

### <a name="devinitjson"></a>devinit.jsem

Veja a seguir o conteúdo do [_devinit.jsno_](devinit-json.md) arquivo.

```json
{
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages useful for C++ development.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```

O _devinit.jsno_ é o arquivo consumido pela ferramenta [devinit](devinit-and-codespaces.md) e deve estar no mesmo diretório de _devcontainer.jsem_ .

Neste exemplo, a ferramenta [WSL-install](tool-wsl-install.md) é usada para criar uma instância WSL que executa o Ubuntu 20, 4 e o provisionamento com ferramentas essenciais de desenvolvimento em C++.
## <a name="targeting-windows-or-linux"></a>Direcionamento para Windows ou Linux

Uma configuração de compilação padrão direcionada ao Windows sempre é criada com o nome `x64-Debug` .

Ao adicionar os arquivos mencionados acima, na criação da instância do codespace, o Visual Studio provisiona uma nova conexão SSH no [Gerenciador de conexões](/cpp/linux/connect-to-your-remote-linux-computer)e cria uma nova configuração no seletor de configuração que tem como alvo a instância do Ubuntu por meio da conexão SSH.

![Configuração de direcionamento para Ubuntu](media/wsl-ssh-linux-configuration.png).

Ao selecionar a configuração realçada que se destina a WSL, é possível criar e depurar os destinos de compilação do OpenCV.
