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
ms.openlocfilehash: 73060a6314bb1d89a51df98ac9d06d8e1f1be90e
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005641"
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

Conteúdo do [_.devinit.jsno_](devinit-json.md) arquivo. Esse arquivo precisa estar na mesma pasta que _.devcontainer.jsem_.

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
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File PostCloneSetup.ps1"
}
```
