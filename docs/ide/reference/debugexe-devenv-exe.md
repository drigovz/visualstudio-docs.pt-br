---
title: -DebugExe (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aeae28288936b6723b53e826142a4888ad0bc8b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570135"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Abre o arquivo executável especificado a ser depurado.

## <a name="syntax"></a>Sintaxe

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Argumentos

- *ExecutableFile*

  Obrigatórios. O caminho e o nome de um arquivo `.exe`. Se o arquivo `.exe` não for encontrado ou não existir, não será exibido nenhum aviso ou erro, e o Visual Studio iniciará normalmente.

## <a name="remarks"></a>Comentários

Quaisquer cadeias de caracteres após o parâmetro *ExecutableFile* são passadas para esse arquivo como argumentos.

## <a name="example"></a>Exemplo

O exemplo a seguir abre o arquivo `MyApplication.exe` para depuração.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Confira também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
