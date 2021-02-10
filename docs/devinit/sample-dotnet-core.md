---
title: Aplicativo do .NET Core
description: Repositório de exemplo que usa devinit para instalar um SDK do .NET Core específico.
ms.date: 11/04/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 364b3fbb0739891d1ce0f6341bb11af7f0ff76f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943581"
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
