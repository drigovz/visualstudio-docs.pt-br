---
title: Aplicativo do .NET Core
description: Repositório de exemplo que usa devinit para instalar um SDK do .NET Core específico.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 35971ac1fde5fc272f22579cc6640cbea6724db5
ms.sourcegitcommit: e132a870ec198fdcec289227f1a0c1c48fef070c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344514"
---
# <a name="net-core-app"></a>Aplicativo do .NET Core

Consulte o repositório [DotnetCoreDevinitExample](https://github.com/microsoft/DotnetCoreDevinitExample) para obter um exemplo completo de como usar o devinit para instalar a versão necessária do SDK do .NET Core no Codespaces.

## <a name="devinitjson"></a>.devinit.json

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Installs the .NET Core SDK specified in the global.json file.",
      "tool": "require-dotnetcoresdk"
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

## <a name="globaljson"></a>global.json

Conteúdo da _global.jsno_ arquivo na raiz do repositório.

```json
{
  "sdk": {
    "version": "3.1.302"
  }
}
```
