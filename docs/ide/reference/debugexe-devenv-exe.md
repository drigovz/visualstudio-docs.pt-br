---
title: -DebugExe (devenv.exe)
description: Saiba como usar a opção de linha de comando DebugExe devenv para abrir um arquivo executável especificado a ser depurado.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6e60c3fb8a72caa44bcf70ac36850748ce240d42
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039465"
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
