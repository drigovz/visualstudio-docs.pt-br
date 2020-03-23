---
title: -Build (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1766fe22573554b41ebfaa38fbd9e8d6c90c5790
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595755"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Compila uma solução ou um projeto usando um arquivo de configuração de solução especificado.

## <a name="syntax"></a>Sintaxe

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumentos

- *Solutionname*

  Obrigatórios. O caminho completo e o nome do arquivo de solução.

- *SolnConfigName*

  Opcional. O nome da configuração da solução (por exemplo, `Debug` ou `Release`) que será usado para compilar a solução nomeada em *SolutionName*. Se várias plataformas de solução estiverem disponíveis, você também precisará especificar a plataforma (por exemplo, `Debug|Win32`). Se esse argumento não for especificado ou for uma cadeia de caracteres vazia (`""`), a ferramenta usará a configuração ativa da solução.

- `/Project`*ProjName*

  Opcional. O caminho e o nome de um arquivo de projeto na solução. Insira um caminho relativo da pasta *SolutionName* para o arquivo de projeto, o nome de exibição do projeto ou o caminho completo e o nome do arquivo de projeto.

- `/ProjectConfig` *ProjConfigName*

  Opcional. Nome de uma configuração de build do projeto (por exemplo, `Debug` ou `Release`) que será usado ao compilar o projeto nomeado. Se mais de uma plataforma de solução estiver disponível, também será preciso especificar a plataforma (por exemplo, `Debug|Win32`). Se esta opção for especificada, ela substituirá o argumento *SolnConfigName*.

- `/Out`*Nome de saída*

  Opcional. O nome de um arquivo para o qual você deseja enviar a saída da ferramenta. Se o arquivo já existir, a ferramenta anexará a saída ao final do arquivo.

## <a name="remarks"></a>Comentários

- A opção `/Build` realiza a mesma função que o comando de menu **Compilar Solução** dentro do ambiente de desenvolvimento integrado (IDE).

- Coloque as cadeias de caracteres que incluem espaços entre aspas duplas.

- As informações de resumo para builds, incluindo erros, podem ser exibidas na janela Comando ou em qualquer arquivo de log especificado com a opção `/Out`.

- A opção `/Build` compila somente os projetos que foram alterados desde o último build. Para compilar todos os projetos de uma solução, use [/rebuild](../../ide/reference/rebuild-devenv-exe.md).

- Se você receber uma mensagem de erro informando **Configuração de projeto inválida**, verifique se especificou a plataforma de solução ou a plataforma de projeto (por exemplo, `Debug|Win32`).

## <a name="example"></a>Exemplo

O comando a seguir compila o projeto `CSharpWinApp`, usando a configuração de build do projeto `Debug` dentro de `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Confira também

- [Criar e limpar projetos e soluções](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Reconstruir (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
