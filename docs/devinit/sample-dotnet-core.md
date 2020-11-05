---
title: Aplicativo do .NET Core
description: Repositório de exemplo que usa devinit para instalar um SDK do .NET Core específico.
ms.date: 11/04/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 26386631946bd37920ba89490a6210031ef945a6
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398338"
---
# <a name="net-core-app"></a>Aplicativo do .NET Core

Consulte o repositório [devinit-example-dotnet-Core](https://github.com/microsoft/devinit-example-dotnet-core) para obter um exemplo completo de como usar devinit para instalar a versão necessária do SDK do .NET Core no Codespaces.

## <a name="devinitjson"></a>.devinit.json

Conteúdo da _.devinit.jsno_ arquivo na raiz do repositório.

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
