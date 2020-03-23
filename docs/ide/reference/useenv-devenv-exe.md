---
title: -UseEnv (devenv.exe)
ms.date: 01/10/2019
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35808b27964b3ca8fa0488f1be2ce6dc5530b3dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596380"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Inicia o Visual Studio e carrega determinadas variáveis de ambiente para compilação.

> [!NOTE]
> Essa opção é instalada com a carga de trabalho de **Desenvolvimento para desktop com C++**.

## <a name="syntax"></a>Sintaxe

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumentos

- *Solutionname*

  O caminho completo e o nome de um arquivo de solução.

- *Projectname*

  O caminho completo e o nome de um arquivo de projeto.

## <a name="remarks"></a>Comentários

Esta opção afeta o IDE do Visual Studio nas propriedades do projeto para **diretórios VC++**. Se você especificar a opção `/UseEnv`, o nó dos **Diretórios VC++** mostrará os valores para as variáveis de ambiente PATH, INCLUDE, LIBPATH e LIB. (Também mostra valores para **Diretórios de Origem** e **Diretórios de Exclusão**.) Caso contrário, o nó substitui as variáveis de ambiente por cinco valores de diretório: **Diretórios executáveis,** **Diretórios de** **inclusão, diretórios de referência,** **diretórios de bibliotecas**e **diretórios winrt da biblioteca.**

> [!TIP]
> Para acessar as propriedades do projeto, clique com o botão direito do mouse no projeto do C++ e selecione **Propriedades**. Na caixa de diálogo **Páginas de Propriedades**, selecione **Propriedades de Configuração** e, em seguida, **Diretórios do VC++**.

Quando um nome de projeto é especificado com essa opção, a ferramenta exibe as variáveis de ambiente para todos os projetos dentro da solução primária do projeto.

## <a name="example"></a>Exemplo

O exemplo a seguir inicia o Visual Studio e carrega as variáveis de ambiente nas páginas de propriedades da solução `MySolution`.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Confira também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Página de propriedades de Diretórios do VC++ (Windows)](/cpp/build/reference/vcpp-directories-property-page)
