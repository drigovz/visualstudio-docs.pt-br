---
title: -DebugExe (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a93a582af62ed0eac8cdc0f5da55ac7bda555152
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008966"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Abre o arquivo executável especificado a ser depurado.

## <a name="syntax"></a>Sintaxe

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Arguments

- *ExecutableFile*

  Necessário. O caminho e o nome de um arquivo `.exe`. Se o arquivo `.exe` não for encontrado ou não existir, não será exibido nenhum aviso ou erro, e o Visual Studio iniciará normalmente.

## <a name="remarks"></a>Comentários

Quaisquer cadeias de caracteres após o parâmetro *ExecutableFile* são passadas para esse arquivo como argumentos.

## <a name="example"></a>Exemplo

O exemplo a seguir abre o arquivo `MyApplication.exe` para depuração.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)