---
title: Comando Importar e Exportar Configurações
ms.date: 11/21/2018
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 409c0f40adfd374065dedb842965d2d1237bc9a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568822"
---
# <a name="import-and-export-settings-command"></a>Comando Importar e Exportar Configurações

Importa, exporta ou redefine as configurações do Visual Studio.

## <a name="syntax"></a>Sintaxe

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Opções

/export:`filename`

Opcional. Exporta as configurações atuais para o arquivo especificado.

/import:`filename`

Opcional. Importa as configurações no arquivo especificado.

/reset

Opcional. Redefine as configurações atuais.

## <a name="remarks"></a>Comentários

Executar esse comando sem nenhuma opção abre o assistente **Importar e Exportar Configurações**. Para obter mais informações, confira [Sincronizar as configurações](../synchronized-settings-in-visual-studio.md) e [Configurações do ambiente](../environment-settings.md).

## <a name="example"></a>Exemplo

O seguinte comando exporta as configurações atuais para o arquivo `MyFile.vssettings`:

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Confira também

- [Configurações do ambiente](../../ide/environment-settings.md)
- [Sincronizar as configurações](../../ide/synchronized-settings-in-visual-studio.md)
- [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
