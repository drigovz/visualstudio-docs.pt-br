---
title: OpenCV
description: Exemplo de personalização usando devinit para o repositório OpenCV/OpenCV.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: dd8a17635b70d0f9f49852d09d8f1b9a6864e26e
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809093"
---
# <a name="opencv"></a>OpenCV

Este exemplo ilustra as personalizações necessárias para o [OpenCV](https://github.com/opencv/opencv) ser automaticamente provisionado com [GitHub Codespaces] https://github.com/features/codespaces) .

## <a name="devinitjson"></a>.devinit.jsem

Conteúdo do [_.devinit.jsno_](devinit-json.md) arquivo. Esse arquivo precisa estar na mesma pasta que _.devcontainer.jsem_.

```json
{
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.jsem

Conteúdo da _.devcontainer.jsno_ arquivo na raiz do repositório.

```json
{
  "postCreateCommand": "devinit init"
}
```