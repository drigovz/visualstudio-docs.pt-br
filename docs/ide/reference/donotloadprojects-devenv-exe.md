---
title: -DoNotLoadProjects (devenv.exe)
description: Saiba como usar a opção de linha de comando DoNotLoadProjects devenv para abrir a solução especificada sem carregar nenhum projeto.
ms.custom: SEO-VS-2020
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef3502a2180f7ae7ed5963deb14844b46f3dbff9
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040622"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Novidades no Visual Studio 2019 versão 16.1**

Abre a solução especificada sem carregar projetos. Confira mais informações em [Soluções filtradas no Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Sintaxe

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Argumentos

*SolutionName*

Obrigatórios. O caminho completo e o nome da solução a ser aberta.

## <a name="example"></a>Exemplo

O exemplo abre a solução MySln.sln sem carregar projetos.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Confira também

- [Soluções filtradas no Visual Studio](../filtered-solutions.md)
- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
