---
title: -UseEnv (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b597eae42eb36c8d034ca9a4038b6823c1121349
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846328"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Inicia o Visual Studio e carrega variáveis de ambiente para a caixa de diálogo **Diretórios do VC++**.

> [!NOTE]
> Essa opção é instalada com a carga de trabalho de **Desenvolvimento para desktop com C++**.

## <a name="syntax"></a>Sintaxe

```shell
Devenv /useenv
```

## <a name="example"></a>Exemplo

O exemplo a seguir inicia o Visual Studio e carrega variáveis de ambiente para a caixa de diálogo **Diretórios do VC++**.

```shell
Devenv.exe /useenv
```

## <a name="see-also"></a>Consulte também

* [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)