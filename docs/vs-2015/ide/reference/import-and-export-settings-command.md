---
title: Comando Import and Export Settings | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e3ee8549fd8cf1a4551818c013551ba24128f95
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671046"
---
# <a name="import-and-export-settings-command"></a>Comando Importar e Exportar Configurações
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Importa, exporta ou redefine configurações [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Sintaxe

```
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Opções
 /export:`filename` opcional. Exporta as configurações atuais para o arquivo especificado.

 /import: `filename` opcional. Importa as configurações no arquivo especificado.

 /reset Opcional. Redefine as configurações atuais.

## <a name="remarks"></a>Comentários
 Executar esse comando sem nenhuma opção abre o assistente **Importar e Exportar Configurações**. Para obter mais informações, consulte [Como: Compartilhar configurações entre computadores ou versões de Visual Studio](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).

## <a name="example"></a>Exemplo
 O comando a seguir exporta as configurações atuais para o arquivo `MyFile.vssettings`.

```
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Veja também
 [Personalizando as configurações de desenvolvimento no](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) Visual Studio [comandos](../../ide/reference/visual-studio-commands.md) do Visual Studio
