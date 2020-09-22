---
title: devinit e GitHub Codespaces
description: Saiba como personalizar um codespace para o Visual Studio usando o devinit.
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
ms.openlocfilehash: a622bf3a10b47ab535a02deac35e3ed2c2b8aa4c
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808698"
---
# <a name="devinit-and-github-codespaces"></a>devinit e GitHub Codespaces

devinit é um ótimo complemento para o [GitHub Codespaces](https://github.com/features/codespaces) e o devinit pode ser usado para obter uma configuração de codespace para que os colaboradores possam criar, executar e depurar imediatamente.

Para integrar com o GitHub Codespaces, `devinit` é necessário chamar a partir do `postCreateCommand` definido em um `.devcontainer.json` arquivo colocado na raiz do repositório. As cadeias de caracteres em `postCreateCommand` são executadas no shell padrão, depois que o repositório é clonado no codespace. Você pode ler mais sobre `postCreateCommand` na [documentação de personalização](https://docs.GitHub.com/en/GitHub/developing-online-with-codespaces/configuring-codespaces-for-your-project)do GitHub Codespaces. Para adicionar o `devinit` comando, você pode adicionar `devinit init` ao `postCreateCommand` conforme mostrado nos exemplos abaixo.

Você também pode executar `devinit init -f <path to .devinit.json>` a partir do terminal integrado do Visual Studio uma vez conectado ao seu codespace.

## <a name="examples"></a>Exemplos

### <a name="with-a-devinitjson-file"></a>Com um .devinit.jsno arquivo
Neste exemplo, o _.devcontainer.jsno_ arquivo abaixo é colocado na raiz do repositório junto com o _.devinit.jsno_ arquivo. Os arquivos também podem ser colocados em um diretório _. devcontainer_ .

```json
{
  "postCreateCommand": "devinit init"
}
```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

### <a name="as-commands"></a>Comandos do as
Neste exemplo _.devcontainer.jsno_ arquivo abaixo é colocado na raiz do repositório e `devinit run` está sendo chamado programaticamente para executar uma ferramenta  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>De um prompt de terminal

Quando o diretório de trabalho atual contém um _.devinit.jsno_ arquivo.

```batch
> devinit init
```

Quando o _.devinit.jsem_ está em outro diretório.

```batch
> devinit init -f path/to/.devinit.json
```
