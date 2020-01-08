---
title: -Project (devenv.exe)
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
ms.openlocfilehash: a4b57a5bd51ff20de8da87798aa398db04bc1c7d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567769"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Identifica um único projeto dentro da configuração da solução especificada para ser compilado, limpo, recompilado ou implantado.

## <a name="syntax"></a>Sintaxe

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Necessária. O caminho completo e o nome do arquivo de solução.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Necessária. [Compila](build-devenv-exe.md), [limpa](clean-devenv-exe.md), [implanta](deploy-devenv-exe.md) ou [recompila](rebuild-devenv-exe.md) o projeto.

- *SolnConfigName*

  Opcional. Nome da configuração da solução (como `Debug` ou `Release`) aplicado à solução nomeada em *SolutionName*. Se mais de uma plataforma de solução estiver disponível, também será preciso especificar a plataforma (por exemplo, `Debug|Win32`). Se esse argumento não for especificado ou for uma cadeia de caracteres vazia (`""`), a ferramenta usará a configuração ativa da solução.

- `/Project` *ProjName*

  Opcional. O caminho e o nome de um arquivo de projeto na solução. Você pode inserir o nome de exibição do projeto ou um caminho relativo da pasta *SolutionName* para o arquivo do projeto. Também é possível inserir o caminho completo e o nome do arquivo do projeto.

- `/ProjectConfig` *ProjConfigName*

  Opcional. Nome da configuração de build do projeto (por exemplo, `Debug` ou `Release`) que será aplicado ao `/Project` nomeado. Se mais de uma plataforma de solução estiver disponível, também será preciso especificar a plataforma (por exemplo, `Debug|Win32`).

- `/Out` *NomeDoArquivoDeSaída*

  Opcional. O nome de um arquivo para o qual você deseja enviar a saída da ferramenta. Se o arquivo já existir, a ferramenta anexará a saída ao final do arquivo.

## <a name="remarks"></a>Comentários

- Deve ser usado parte de um `devenv` `/Build`, `/Clean`, `/Rebuild`ou comando `/Deploy`.

- Coloque as cadeias de caracteres que incluem espaços entre aspas duplas.

- As informações de resumo para builds, incluindo erros, podem ser exibidas na janela **Comando** ou em qualquer arquivo de log especificado com a opção `/Out`.

## <a name="example"></a>Exemplo

Este exemplo apresenta a compilação do projeto `CSharpWinApp`, usando a configuração de build de projeto `Debug` dentro de `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Veja também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
