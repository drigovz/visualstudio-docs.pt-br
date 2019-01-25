---
title: -NoSplash (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 794934ab0bddcc90a36accf639b26e5ecc6bab30
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54233137"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Impede que a tela inicial seja mostrada.

## <a name="syntax"></a>Sintaxe

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Arguments

- *File1*

  Opcional. O arquivo a ser aberto em uma instância existente do Visual Studio. Se não existir nenhuma instância do Visual Studio, uma nova instância será criada com um layout de janela simplificado, e a ferramenta abrirá o *File1* na nova instância.

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

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Opções de linha de comando do Devenv para desenvolvimento de VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)