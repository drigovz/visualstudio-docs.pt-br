---
title: -RunExit (devenv.exe)
description: Saiba como usar a opção de linha de comando RunExit devenv para compilar e executar o projeto ou a solução especificada e, em seguida, feche o IDE.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a1e0af28e8a96860039381b958d63e161a24936
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039844"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

Compila e executa a solução ou o projeto especificado e, em seguida, fecha o IDE (ambiente de desenvolvimento integrado).

## <a name="syntax"></a>Sintaxe

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Argumentos

- *SolutionName*

  O caminho completo e o nome de um arquivo de solução.

- *ProjectName*

  O caminho completo e o nome de um arquivo de projeto.

- `/Out`*NomeDoArquivoDeSaída*

  Opcional. O nome de um arquivo para o qual você deseja enviar a saída da ferramenta. Se o arquivo já existir, a ferramenta anexará a saída ao final do arquivo.

## <a name="remarks"></a>Comentários

Compila e executa o projeto ou a solução especificada de acordo com as configurações especificadas para a configuração da solução ativa. Essa opção minimiza o IDE durante a execução do projeto ou da solução. Fecha o IDE depois que a execução do projeto ou da solução for concluída.

- Coloque as cadeias de caracteres que incluem espaços entre aspas duplas.

- As informações de resumo, incluindo erros, podem ser exibidas na janela **Comando** ou em qualquer arquivo de log especificado com a opção `/Out`.

## <a name="example"></a>Exemplo

Este exemplo executa a solução `MySolution` em um IDE minimizado usando a configuração de implantação ativa e, em seguida, fecha o IDE.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Confira também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
