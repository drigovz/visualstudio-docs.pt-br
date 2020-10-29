---
title: Aplicativo do .NET Core
description: Repositório de exemplo que usa devinit para instalar um SDK do .NET Core específico.
ms.date: 10/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ce94dc9cf4b6368a96cc027e1a9fc14e0d7e0650
ms.sourcegitcommit: 7915cedf2f5988db25cb90042aa8466a1d3cee7f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2020
ms.locfileid: "93028140"
---
# <a name="net-core-app"></a>Aplicativo do .NET Core

Consulte o repositório [DevinitExample](https://github.com/microsoft/DevinitExample) para obter um exemplo completo de como usar o devinit para instalar a versão necessária do SDK do .NET Core no Codespaces.

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