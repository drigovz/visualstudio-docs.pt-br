---
title: -DoNotLoadProjects (devenv.exe)
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
ms.openlocfilehash: 51e3341082ff354fc8bc87a89b3d7bc56e4e7887
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569849"
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
