---
title: -ResetSettings (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52c3576b10fdc88563b3689e4b37d71b7f4659cd
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227545"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Restaura as configurações padrão do Visual Studio e inicia automaticamente o IDE do Visual Studio. Esta opção redefine facultativamente as configurações para um arquivo de configurações especificado.

As configurações padrão derivam do perfil selecionado quando o Visual Studio foi iniciado pela primeira vez.

> [!TIP]
> Para saber como redefinir configurações usando o IDE (ambiente de desenvolvimento integrado), confira [Reset settings](../environment-settings.md#reset-settings) (Redefinir configurações).

## <a name="syntax"></a>Sintaxe

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Arguments

- *SettingsFile*

  Opcional. O caminho completo e o nome do arquivo de configurações a ser aplicado ao Visual Studio.

- *DefaultCollectionSpecifier*

  Opcional. Um especificador que representa uma coleção padrão de configurações a restaurar. Escolha um dos especificadores de coleção padrão listados na tabela.

  | Nome da coleção padrão | Especificador da coleção |
  | --- | --- |
  | **Geral** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Desenvolvimento para a Web** | `Web` |
  | **Desenvolvimento para a Web (somente código)** | `WebCode` |

## <a name="remarks"></a>Comentários

Se nenhum *SettingsFile* for especificado, o IDE abrirá usando as configurações existentes.

## <a name="example"></a>Exemplo

O primeiro exemplo aplica as configurações armazenadas no arquivo `MySettings.vssettings`.

O segundo exemplo restaura o perfil padrão do Visual C#.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Consulte também

- [Configurações do ambiente](../environment-settings.md)
- [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)