---
title: -Project (devenv.exe)
description: Saiba como usar a opção de linha de comando devenv do projeto para identificar um único projeto dentro da configuração da solução especificada para compilar, limpar, recompilar ou implantar o projeto.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- Project Devenv switch (/Project)
- Devenv, /Project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90c1cdf37ddda7209b4f951e42ad07720e5cc40b
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040102"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Identifica um único projeto dentro da configuração da solução especificada para ser compilado, limpo, recompilado ou implantado.

## <a name="syntax"></a>Sintaxe

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumentos

- *SolutionName*

  Obrigatórios. O caminho completo e o nome do arquivo de solução.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Obrigatórios. [Compila](build-devenv-exe.md), [limpa](clean-devenv-exe.md), [implanta](deploy-devenv-exe.md) ou [recompila](rebuild-devenv-exe.md) o projeto.

- *SolnConfigName*

  Opcional. Nome da configuração da solução (como `Debug` ou `Release`) aplicado à solução nomeada em *SolutionName*. Se mais de uma plataforma de solução estiver disponível, também será preciso especificar a plataforma (por exemplo, `Debug|Win32`). Se esse argumento não for especificado ou for uma cadeia de caracteres vazia (`""`), a ferramenta usará a configuração ativa da solução.

- `/Project` *ProjName*

  Opcional. O caminho e o nome de um arquivo de projeto na solução. Você pode inserir o nome de exibição do projeto ou um caminho relativo da pasta *SolutionName* para o arquivo do projeto. Também é possível inserir o caminho completo e o nome do arquivo do projeto.

- `/ProjectConfig` *ProjConfigName*

  Opcional. Nome da configuração de build do projeto (por exemplo, `Debug` ou `Release`) que será aplicado ao `/Project` nomeado. Se mais de uma plataforma de solução estiver disponível, também será preciso especificar a plataforma (por exemplo, `Debug|Win32`).

- `/Out`*NomeDoArquivoDeSaída*

  Opcional. O nome de um arquivo para o qual você deseja enviar a saída da ferramenta. Se o arquivo já existir, a ferramenta anexará a saída ao final do arquivo.

## <a name="remarks"></a>Comentários

- Deve ser usado como parte de um `devenv` `/Build` `/Clean` comando,, `/Rebuild` ou `/Deploy` .

- Coloque as cadeias de caracteres que incluem espaços entre aspas duplas.

- As informações de resumo para builds, incluindo erros, podem ser exibidas na janela **Comando** ou em qualquer arquivo de log especificado com a opção `/Out`.

## <a name="example"></a>Exemplo

Este exemplo apresenta a compilação do projeto `CSharpWinApp`, usando a configuração de build de projeto `Debug` dentro de `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Confira também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
