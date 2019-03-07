---
title: -Command (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6daa21f9db7eef9a651577ad829d884dccf353dc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717514"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Executa o comando especificado depois de iniciar o IDE do Visual Studio.

## <a name="syntax"></a>Sintaxe

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Arguments

*CommandName*

Necessário. O nome completo de um comando do Visual Studio ou seu alias, entre aspas duplas. Para obter mais informações sobre comandos e a sintaxe de aliases, consulte [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Comentários

Após a conclusão da inicialização, o IDE executa o comando nomeado.

::: moniker range="vs-2017"

Se você usar essa opção, o IDE não exibirá a Página Inicial na inicialização.

::: moniker-end

Se um suplemento expor um comando, será possível usar essa opção para iniciar o suplemento por meio da linha de comando. Para obter mais informações, confira [Como: Controlar suplementos usando o Gerenciador de Suplementos](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Exemplo

O primeiro exemplo inicia o Visual Studio e executa a macro Abrir Arquivos Favoritos automaticamente.

O segundo exemplo abre uma guia de navegação na Web dentro do IDE e acessa o site Microsoft Docs.

O terceiro exemplo cria um novo arquivo chamado `some_file.cs` e o abre em um editor de código.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
- [Janela Comando](command-window.md)