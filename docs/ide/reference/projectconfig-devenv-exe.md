---
title: -ProjectConfig (devenv.exe)
description: Saiba como usar a opção de linha de comando ProjectConfig devenv para especificar uma configuração de compilação de projeto a ser aplicada quando você compilar, limpar, recompilar ou implantar o projeto.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /ProjectConfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /ProjectConfig switch
- ProjectConfig Devenv switch (/ProjectConfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ba1f6f0de7e7b716853ec58aa27a34fe11010da4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969588"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Especifica uma configuração de build do projeto a ser aplicada ao compilar, limpar, recompilar ou implantar o projeto nomeado no argumento `/Project`.

## <a name="syntax"></a>Sintaxe

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumentos

- *SolutionName*

  Obrigatório. O caminho completo e o nome do arquivo de solução.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Obrigatório. [Compila](build-devenv-exe.md), [limpa](clean-devenv-exe.md), [implanta](deploy-devenv-exe.md) ou [recompila](rebuild-devenv-exe.md) o projeto.

- *SolnConfigName*

  Opcional. O nome da configuração da solução (por exemplo, `Debug` ou `Release`) que será aplicado à solução nomeada em *SolutionName*. Se mais de uma plataforma de solução estiver disponível, também será preciso especificar a plataforma (por exemplo, `Debug|Win32`). Se esse argumento não for especificado ou for uma cadeia de caracteres vazia (`""`), a ferramenta usará a configuração ativa da solução.

- `/Project` *ProjName*

  Opcional. O caminho e o nome de um arquivo de projeto na solução. Você pode inserir o nome de exibição do projeto ou um caminho relativo da pasta *SolutionName* para o arquivo do projeto. Também é possível inserir o caminho completo e o nome do arquivo do projeto.

- `/ProjectConfig` *ProjConfigName*

  Opcional. Nome da configuração de build do projeto (por exemplo, `Debug` ou `Release`) que será aplicado ao `/Project` nomeado. Se mais de uma plataforma de solução estiver disponível, também será preciso especificar a plataforma (por exemplo, `Debug|Win32`).

- `/Out`*NomeDoArquivoDeSaída*

  Opcional. O nome de um arquivo para o qual você deseja enviar a saída da ferramenta. Se o arquivo já existir, a ferramenta anexará a saída ao final do arquivo.

## <a name="remarks"></a>Comentários

A opção `/ProjectConfig` deve ser usada com a opção `/Project` como parte de um comando `/Build`, /`Clean`, `/Deploy` ou `/Rebuild`.

Coloque as cadeias de caracteres que incluem espaços entre aspas duplas.

As informações de resumo para builds, incluindo erros, podem ser exibidas na janela Comando ou em qualquer arquivo de log especificado com a opção `/Out`.

## <a name="example"></a>Exemplo

O comando a seguir compila o projeto `CSharpWinApp`, usando a configuração de build do projeto `Debug` dentro de `MySolution`:

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Confira também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
