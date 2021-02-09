---
title: -Out (devenv.exe)
description: Saiba como usar a opção de linha de comando devenv de saída para especificar um arquivo para armazenar e exibir erros ao executar, executar e sair, atualizar, compilar, recompilar, limpar ou implantar uma solução.
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: db5a67031d48c55a4bd9c668335360897bcca62b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932183"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Especifica um arquivo para armazenar e exibir erros ao [executar](run-devenv-exe.md), [executar e fechar](runexit-devenv-exe.md), [atualizar](upgrade-devenv-exe.md), [compilar](build-devenv-exe.md), [recompilar](rebuild-devenv-exe.md), [limpar](clean-devenv-exe.md) ou [implantar](deploy-devenv-exe.md) uma solução.

## <a name="syntax"></a>Sintaxe

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Argumentos

- *FileName*

  Obrigatório. O caminho e nome do arquivo para receber a saída ao compilar um arquivo executável.

## <a name="remarks"></a>Comentários

Se for especificado um nome de arquivo inexistente, o arquivo será criado automaticamente. Caso contrário, o arquivo já existe e os resultados serão anexados ao conteúdo existente do arquivo.

Erros de build de linha de comando são exibidos na janela **Comando** e no modo de exibição Construtor de Soluções da janela **Saída**. Esta opção é útil para exibir resultados de compilações autônomas.

## <a name="example"></a>Exemplo

Este exemplo executa `MySolution` e grava os erros no arquivo `MyErrorLog.txt`.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Confira também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
