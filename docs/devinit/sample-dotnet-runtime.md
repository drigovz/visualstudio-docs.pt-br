---
title: Runtime do .NET Core
description: Exemplo de personalização usando devinit para o repositório dotnet/tempo de execução.
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
ms.openlocfilehash: b38490217a384e748ae97ec4b808f197b4af3b7b
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005648"
---
# <a name="net-core-runtime"></a>runtime do .NET Core

Este exemplo ilustra como personalizar o [dotnet/tempo](https://github.com/dotnet/runtime) de execução do .NET Core Runtime para ser provisionado automaticamente com o [GitHub Codespaces](https://github.com/features/codespaces).

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Esse script é chamado de _PostCloneSetup.ps1_ e também pode ser executado localmente para configurar o repositório. Esse arquivo precisa estar na mesma pasta que _.devcontainer.jsem_.

```console
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

O arquivo de _packages.config_ é um arquivo de [chocolate](https://chocolatey.org/) que define a lista de pacotes de chocolates a serem instalados. Esse arquivo precisa estar na mesma pasta que _.devcontainer.jsem_.

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>.devinit.json

Conteúdo do [_.devinit.jsno_](devinit-json.md) arquivo. Esse arquivo precisa estar na mesma pasta que _.devcontainer.jsno_ arquivo.

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "choco-install",
            "input": "packages.config"
        },
        {
            "tool": "require-vscomponent"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.jsem

Conteúdo da _.devcontainer.jsno_ arquivo na raiz do repositório.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File PostCloneSetup.ps1"
}
```
