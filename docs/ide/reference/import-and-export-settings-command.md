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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0be61d8690c0605f6e7773efe02f5db351110f9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658771"
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

## <a name="see-also"></a>Consulte também

- [Configurações do ambiente](../../ide/environment-settings.md)
- [Sincronizar as configurações](../../ide/synchronized-settings-in-visual-studio.md)
- [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)