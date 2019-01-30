---
title: -UseEnv (devenv.exe)
ms.date: 01/10/2019
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9006f8a4e6867e9d64db78a40f44e4b852280fe6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934634"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Inicia o Visual Studio e carrega determinadas variáveis de ambiente para compilação.

> [!NOTE]
> Essa opção é instalada com a carga de trabalho de **Desenvolvimento para desktop com C++**.

## <a name="syntax"></a>Sintaxe

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  O caminho completo e o nome de um arquivo de solução.

- *ProjectName*

  O caminho completo e o nome de um arquivo de projeto.

## <a name="remarks"></a>Comentários

Esta opção afeta o IDE do Visual Studio nas propriedades do projeto para **diretórios VC++**. Se você especificar a opção `/UseEnv`, o nó dos **Diretórios VC++** mostrará os valores para as variáveis de ambiente PATH, INCLUDE, LIBPATH e LIB. (Também mostra os valores para os **Diretórios de origem** e **Diretórios de exclusão**.) Caso contrário, o nó substitui as variáveis de ambiente por cinco valores de diretório: **Diretórios executáveis**, **Diretórios de inclusão**, **Diretórios de referência**, **Diretórios de biblioteca** e **Diretórios de biblioteca WinRT**.

> [!TIP]
> Para acessar as propriedades do projeto, clique com o botão direito do mouse no projeto do C++ e selecione **Propriedades**. Na caixa de diálogo **Páginas de Propriedades**, selecione **Propriedades de Configuração** e, em seguida, **Diretórios do VC++**.

Quando um nome de projeto é especificado com essa opção, a ferramenta exibe as variáveis de ambiente para todos os projetos dentro da solução primária do projeto.

## <a name="example"></a>Exemplo

O exemplo a seguir inicia o Visual Studio e carrega as variáveis de ambiente nas páginas de propriedades da solução `MySolution`.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Página de propriedades de Diretórios do VC++ (Windows)](/cpp/ide/vcpp-directories-property-page)
