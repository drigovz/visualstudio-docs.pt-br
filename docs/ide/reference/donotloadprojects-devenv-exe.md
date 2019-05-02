---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 03/11/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de757e7022339b11f6d7c04ea7315abf685da24c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428054"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

Abre a solução especificada sem carregar projetos. Confira mais informações em [Soluções filtradas no Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Sintaxe

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Arguments

*SolutionName*

Necessário. O caminho completo e o nome da solução a ser aberta.

## <a name="example"></a>Exemplo

O exemplo abre a solução MySln.sln sem carregar projetos.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Consulte também

- [Soluções filtradas no Visual Studio](../filtered-solutions.md)
- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
