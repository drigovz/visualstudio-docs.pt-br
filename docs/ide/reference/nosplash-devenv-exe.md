---
title: -NoSplash (devenv.exe)
description: Saiba como usar a opção de linha de comando do devenv nosplash para impedir que a tela inicial seja mostrada.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c88d75c0658c861c4631daeeb736ed7cfdb0a487
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967222"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Impede que a tela inicial seja mostrada.

## <a name="syntax"></a>Sintaxe

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Argumentos

- *Arquivo1*

  Opcional. O arquivo a ser aberto em uma instância existente do Visual Studio. Se não existir nenhuma instância do Visual Studio, uma nova instância será criada com um layout de janela simplificado, e a ferramenta abrirá *File1* na nova instância.

- *FileN*

  Opcional. Um ou mais arquivos adicionais a serem abertos na instância existente do Visual Studio.

## <a name="remarks"></a>Comentários

Esta opção oculta a tela inicial. Omitir esta opção faz com que a tela inicial a seja mostrada. Se desejar examinar mais a fundo a tela inicial (por exemplo, para verificar o ícone de produto do VSPackage), use a opção [/Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

A opção `/NoSplash` pode ser combinada com outras opções, como [/Run](run-devenv-exe.md) ou [/DebugExe](debugexe-devenv-exe.md).

## <a name="example"></a>Exemplo

Todos os três exemplos abrem o IDE sem exibir a tela inicial. O segundo exemplo também compila a solução especificada e executa o arquivo executável criado. O terceiro exemplo abre o executável especificado para depuração no IDE.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>Confira também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Opções de linha de comando do Devenv para desenvolvimento de VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
