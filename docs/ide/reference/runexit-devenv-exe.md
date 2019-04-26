---
title: -RunExit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fa010e72267dadfb1974f7ce8be3b6b9a3e1cff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935037"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

Compila e executa a solução ou o projeto especificado e, em seguida, fecha o IDE (ambiente de desenvolvimento integrado).

## <a name="syntax"></a>Sintaxe

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  O caminho completo e o nome de um arquivo de solução.

- *ProjectName*

  O caminho completo e o nome de um arquivo de projeto.

- `/Out` *OutputFilename*

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

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)