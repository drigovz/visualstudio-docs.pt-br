---
title: -Out (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /Out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /Out Devenv switch
- Out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a073b4815a01696c546dc2a9dd1132e3605281e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655783"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Especifica um arquivo para armazenar e exibir erros ao [executar](run-devenv-exe.md), [executar e fechar](runexit-devenv-exe.md), [atualizar](upgrade-devenv-exe.md), [compilar](build-devenv-exe.md), [recompilar](rebuild-devenv-exe.md), [limpar](clean-devenv-exe.md) ou [implantar](deploy-devenv-exe.md) uma solução.

## <a name="syntax"></a>Sintaxe

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Arguments

- *FileName*

  Necessário. O caminho e nome do arquivo para receber a saída ao compilar um arquivo executável.

## <a name="remarks"></a>Comentários

Se for especificado um nome de arquivo inexistente, o arquivo será criado automaticamente. Caso contrário, o arquivo já existe e os resultados serão anexados ao conteúdo existente do arquivo.

Erros de build de linha de comando são exibidos na janela **Comando** e no modo de exibição Construtor de Soluções da janela **Saída**. Esta opção é útil para exibir resultados de compilações autônomas.

## <a name="example"></a>Exemplo

Este exemplo executa `MySolution` e grava os erros no arquivo `MyErrorLog.txt`.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)