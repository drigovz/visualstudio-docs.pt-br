---
title: eShopOnWeb
description: Exemplo de personalização usando devinit para o repositório dotnet-arquitetura/eShopOnWeb.
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
ms.openlocfilehash: b981b9bb066057228fed07aa7ea26aeab4670ae4
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438211"
---
# <a name="eshoponweb"></a>eShopOnWeb

Este exemplo ilustra como personalizar o exemplo de arquitetura dotnet [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) para ser automaticamente provisionado com o [GitHub Codespaces](https://github.com/features/codespaces).

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Esse script é chamado de _PostCloneSetup.ps1_ e também pode ser executado localmente para configurar o repositório. Esse arquivo precisa estar na mesma pasta que _.devcontainer.jsem_.

```console
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

## <a name="devinitjson"></a>.devinit.json

Conteúdo do [`.devinit.json`](devinit-json.md) arquivo. Esse arquivo precisa estar na mesma pasta que _.devcontainer.jsem_.

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.jsem

Conteúdo da _.devcontainer.jsno_ arquivo na raiz do repositório.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
