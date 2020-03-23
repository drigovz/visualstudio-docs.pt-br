---
title: -ResetSettings (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eebcf2c6796723e51c3aefdb12575aa89779429f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593857"
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

## <a name="arguments"></a>Argumentos

- *SettingsFile*

  Opcional. O caminho completo e o nome do arquivo de configurações a ser aplicado ao Visual Studio.

- *DefaultCollectionSpecifier*

  Opcional. Um especificador que representa uma coleção padrão de configurações a restaurar. Escolha um dos especificadores de coleção padrão listados na tabela.

  | Nome da coleção padrão | Especificador da coleção |
  | --- | --- |
  | **Geral** | `General` |
  | **Javascript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C #** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Desenvolvimento Web** | `Web` |
  | **Desenvolvimento para a Web (Somente Código)** | `WebCode` |

## <a name="remarks"></a>Comentários

Se nenhum *SettingsFile* for especificado, o IDE abrirá usando as configurações existentes.

## <a name="example"></a>Exemplo

O primeiro exemplo aplica as configurações armazenadas no arquivo `MySettings.vssettings`.

O segundo exemplo restaura o perfil padrão do Visual C#.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Confira também

- [Configurações do ambiente](../environment-settings.md)
- [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
